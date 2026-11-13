---
date: 2025-11-22
---
z# Configuración de la VM
## Instalación de Ubuntu Server
Utilizando el ISO `ubuntu-24.04-latest-live-server-amd64` para instalar el servidor de Ubuntu, este tiene varias ventajas como permitir teclado español latino. La instalación se siguen los pasos indicados, y uno de esos es la creación de un usuario que no sea "root" pero con permiso para usar `sudo`. 

En este caso, usamos un usuario con contraseña segura para iniciar sesión con este. Para prevenir acceso SSH no autorizado desde la propia máquina al servidor, no se configurará OpenSSH para conexión remota. **Todas las configuraciones se harán en la virtual machine, y se asume que no podrá volver a ser accedida directamente.**

Después de instalado, si es posible, se actualizará el sistema:

```bash
sudo apt update
sudo apt upgrade
```
## Instalación de dependencias

```bash
sudo apt install nginx nodejs npm curl ca-certificates
```
## Configuración del firewall
Se utilizará el firewall UFW que Ubuntu trae por defecto.

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing

sudo ufw allow 80/tcp   # HTTP

sudo ufw enable
sudo ufw status # Se verifican los puertos abiertos al firewall
```
## Instalación de Nginx

```bash
sudo systemctl start nginx
```
## Hardening de Nginx
Se editará la configuración de Nginx para prevenir información necesaria y tomar medidas preventivas. Se ejecuta el siguiente comando:

```bash
sudo nano /etc/nginx/nginx.conf
```

Y luego, se edita el contenido de la siguiente forma:

```bash
# ...
http {
	##
	# Basic Settings
	##
	
	sendfile on;
	tcp_nopush on;
	types_hash_max_size 2048;
	server_tokens off; # Originalmente comentado, luego descomentar
	
	# ...
	
	##
	# Virtual Host Configs
	##
	
	# Agregar todo lo de abajo
	add_header X-XSS-Protection "1;mode=block";
	add_header X-Frame-Options "SAMEORIGIN"; # Puede ser DENY
	add_header Content-Security-Policy "default-src 'self'; connect-src 'self' http://IP;¨img-src * data: blob:; frame-ancestors 'self'" always; # Misma línea
	
	# Esto ya está en el config
	include /etc/nginx/conf.d/*.conf;
	include /etc/nginx/sites-enabled/*;
}
```

Hecho esto, se reinicia el servicio.

```bash
sudo systemctl restart nginx
sudo systemctl status nginx
```
## Agregando sitio web a Nginx

```bash
git clone https://github.com/DiegoGarcia271004/ProyectoSED.git
```
### Configuración del Front-end
Nos dirigimos al repositorio

```bash
cd ProyectoSED
```

Dentro, nos dirigimos la carpeta `Frontend`, instalamos los módulos de NPM y luego construimos el sitio estático de Vite.

```bash
cd Frontend/
npm install

nano .env 

# Se agregan las variables de entorno antes de contruirlo:
# VITE_API_URL=http://localhost:3000

npm run build

# Se copia la carpeta dist a /var/www/ y se cambia su nombre a app
sudo cp dist/ /var/www/app/
```


> [!warning] Sobre las variables de entorno.
> En el caso del frontend, es clave que solo se suban los archivos estáticos de la carpeta `dist` producto del `npm run build`. Vite inyecta las variables de entorno directamente, entonces no es necesario que en los archivos a leer por Nginx haya un `.env`.

Luego, se crear un nuevo archivo `webapp` en `/etc/nginx/sites-available/`:

```bash
sudo nano /etc/nginx/sites-available/webapp

# Su contendido:
server {
	listen 80;
	server_name _;
	
	root /var/www/app/;
	index index.html;
	
	location / {
		try_files $uri /index.html;
	}
	
	# Nos adelantamos al proceso para el backend
	location /api/ {
		proxy_pass http://localhost:3000/;
		proxy_set_header Host $host;
		proxy_set_header X-Real-IP $remote_addr;
		proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
	}
}
```

Luego, se ejecuta el siguiente comando para enlazar el archivo creado con `sites-enabled`:

```bash
sudo rm /etc/nginx/sites-enabled/default
sudo ln -s /etc/nginx/sites-available/webapp /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
```

Para este punto, el usuario `www-data` con el que Nginx trabaja solo tiene permisos de lectura. No debería haber problemas más allá de la filtración de datos con un acceso no autorizado desde `/var/www/app/`.
## Configuración de la base de datos
### Instalar Docker
Como no se puede copiar y pegar, esto va a doler:

```bash
# Add Docker's official GPG key:
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update

sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl start docker
sudo systemctl status docker
sudo docker run hello-world
```

El tiempo es limitado, así que los comandos que requieran de usar docker tienen que trabajarse con `sudo`.

```bash
mv .env.example .env

# para nosotros, estas son las variables de entorno:
# MONGO_INITDB_ROOT_USERNAME=rootuser
# MONGO_INITDB_ROOT_PASSWORD=_7ts.dQepkq7mjfTNoFv
# MONGO_INITDB_DATABASE=SED_DB
# MONGO_APP_USERNAME=backend
# MONGO_APP_PASSWORD=p4UjRQE*KyQJN3yrE*uJ
# WEBSITE_ADMIN_USERNAME=admin
# WEBSITE_ADMIN_EMAIL=bNTgo32NsvEs@admin.com
# WEBSITE_ADMIN_PASSWORD_HASH=$2y$10$5j5wRDugUsYyN7q1c8KkEewLLo.29ba3c8X53v4f/SmOPgJx3Zemm

docker run -d \
  --name mongodb_seguridad \
  -p 27017:27017 \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=admin123 \
  -v mongo_data:/data/db \
  mongo:latest
```

## Configuración del Back-end
Se tiene que crear un archivo con las variables de entorno del back-end. Esto se hace en una carpeta que no sea dentro de `/var/www/...` para que no sea visible en caso de un acceso no autorizado. Y, preferiblemente, restringir permisos.

```bash
sudo mkdir /etc/project/
sudo nano /etc/project/.env

# Se establecen las variables de entorno para trabajar con la base de datos
# MONGO_URI=mongodb://backend:p4UjRQE*KyQJN3yrE*uJ@localhost:27017/SED_DB?
# DB_NAME=SED_DB
# JWT_SECRET= fa85 2c1b fa08 0a8b b7ea d8fe dc6c c5e3
# PORT=3000

sudo chown root:root /etc/project/.env
sudo chmod 600 /etc/project/.env
```

Creamos la carpeta que contendrá al back-end y copiamos los archivos del back-end en esa carpeta:

```bash
sudo mkdir /var/www/backend/

# Eh, si no estas ahí todavía, tienes que estar afuera de Backend, en la carpeta del proyecto
cd Backend/
npm install
cd ..
sudo cp -r Backend/* /var/www/backend
```

> [!warning] dotenv
> La razón por la cual `dotenv.config()` funciona es porque, durante el desarrollo, `.env` se encuentra en la carpeta raíz del proyecto. Sin embargo, en producción, `.env` no tiene que estar en la carpeta expuesta. Entonces, se rompe cómo se inyectan las variables de entorno.
> 
> Entonces, hay dos opciones.
> - Prescindir completamente de dotenv en la VM. Se elimina las veces que se usa `dotenv.config()`.
> - Editar la configuración para que señale la ruta actual del `.env`: 
>   `dotenv.config({ path: "/etc/project/.env" });` En ese caso, el servicio no debe contener la parte de `EnvironmentFile`.
>   
>   De una forma u otra, hay que cambiar los archivos.

Es por esto de arriba que:

```bash
# Se comenta o borra la parte del dotenv.config()
nano Backend/Config/config.js 
```

Por algún motivo que no termino de entender bien, lo mejor es crear un usuario dedicado al manejo del back-end.

```bash
sudo adduser --system --no-create-home --group backend
sudo chown -R backend:backend /var/www/backend
```

Luego, para correr el back-end, se tiene que crear un servicio. Esta es una manera más confiable de correr la Web API, pues en caso de que la máquina se reinicie, empieza de nuevo, corre en segundo plano, se reinicia automáticamente si falla, etc.

```bash
sudo nano /etc/systemd/system/backend.service

# Se agrega el siguiente contenido
[Unit]
Description=Backend Node Server
After=network.target

[Service]
# Esto de aquí así que dotenv no sea necesario
Environment=NODE_ENV=production
EnvironmentFile=/etc/project/.env
WorkingDirectory=/var/www/backend
ExecStart=/usr/bin/node server.js
Restart=always
RestartSec=5
User=backend
Group=backend

# Seguridad (hardening)
NoNewPrivileges=true
PrivateTmp=true
ProtectSystem=off
ProtectHome=off

[Install]
WantedBy=multi-user.target
```

Creado el servicio, se activa.

```bash
sudo systemctl daemon-reload
sudo systemctl enable backend
sudo systemctl start backend
```

![[Pasted image 20251124114327.png]]

