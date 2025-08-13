### Paso 1: Configuración del Entorno en DigitalOcean

#### 1.1 Crear una Droplet

1. **Iniciar sesión en DigitalOcean**: Ve a [DigitalOcean](https://www.digitalocean.com/) y accede a tu cuenta.
2. **Crear una Droplet**:
    - Selecciona un sistema operativo (recomendado: Ubuntu).

    - Elige el tamaño de la Droplet (puedes empezar con el plan básico).

    - Configura la autenticación con una clave SSH (asegúrate de tener tu clave SSH añadida a tu cuenta).
1. **Completar la creación**: Asigna un nombre a tu Droplet y crea la Droplet. Una vez que esté lista, recibirás una dirección IP.
2. 
#### 1.2 Conectarse a la Droplet

Utiliza SSH para conectarte a tu Droplet desde la terminal:

```bash

ssh root@tu_direccion_ip

```
### Paso 2: Configurar el Firewall

Antes de instalar cualquier software, es buena práctica configurar un firewall.
#### 2.1 Instalar UFW

1. **Actualizar los paquetes**:

```bash

sudo apt update

sudo apt upgrade

```

#### 2. **Instalar UFW** (si no está ya instalado):

```bash

sudo apt install ufw

```

#### 3. **Configurar reglas del firewall**:

  
Permite el tráfico SSH (esto es crucial, ya que podrías perder acceso):

```bash

sudo ufw allow OpenSSH

```

Permite el tráfico HTTP y HTTPS (puedes omitir HTTPS si no usarás SSL):

```bash

sudo ufw allow http

sudo ufw allow https

```

#### 4. Activar el firewall:

```bash

sudo ufw enable

```
### 5. Verificar el estado de UFW:

```bash

sudo ufw status

```

### Paso 3: Configurar el Backend

#### 3.1 Instalar Node.js y npm

1. **Instalar Node.js y npm**:

#### 3.2 Subir el Código del Backend

  

1. **Transferir archivos a la Droplet**: Usa `scp` para subir el código del backend. Desde tu máquina local:

  

```bash

scp -r /ruta/a/tu/backend root@tu_direccion_ip:/ruta/destino

```

  

2. **Navegar al directorio del backend**:

  

``` bash

cd /ruta/destino

```

  

4. **Instalar dependencias:**

  

```bash

npm install

```

  

5. **Iniciar el servidor** (puedes usar `pm2` para mantener el proceso activo):

  

```bash

sudo npm install -g pm2

pm2 start index.js

pm2 startup

pm2 save

```

  

### Paso 4: Configurar el Frontend

  

#### 4.1 Instalar Nginx

  

1. **Instalar Nginx**:

  

```bash

sudo apt install nginx

```

  

2. **Verificar que Nginx esté corriendo**:

  

```bash

sudo systemctl status nginx

```

  

#### 4.2 Generar el Build del Frontend

  

1. **Transferir el código del frontend a tu Droplet**:

  

```bash

scp -r /ruta/a/tu/frontend root@tu_direccion_ip:/ruta/destino/frontend

```

  

2. **Navegar al directorio del frontend**:

  

```bash

cd /ruta/destino/frontend

```

  

3. **Instalar dependencias y crear el build**:

  

```bash

npm install npm run build

```

  

4. **Mover el build a la carpeta de Nginx**:

  

```bash

sudo cp -r build/* /var/www/html/

```

  

### Paso 5: Configurar Nginx para Servir el Frontend y el Backend

  

1. **Editar la configuración de Nginx**:

  

Abre el archivo de configuración de Nginx:

  

```bash

sudo nano /etc/nginx/sites-available/default

```

  

Reemplaza el contenido del archivo con la siguiente configuración:

  

```bash

server {    

    listen 80;    

    server_name tu_direccion_ip;      

    location / {        

        root /var/www/html;        

        index index.html index.htm;        

        try_files $uri $uri/ /index.html;    

    }      

    location /api {        

        proxy_pass http://localhost:5000;  # Cambia 5000 al puerto que usa tu backend        

        proxy_http_version 1.1;        

        proxy_set_header Upgrade $http_upgrade;        

        proxy_set_header Connection 'upgrade';        

        proxy_set_header Host $host;        

        proxy_cache_bypass $http_upgrade;    

    }

}

```

  

Esta configuración permite que Nginx sirva tu frontend y redirija las solicitudes de API al backend.

  

2. **Probar la configuración de Nginx**:

  

```bash

sudo nginx -t

```

  

3. **Reiniciar Nginx**:

  

```bash

sudo systemctl restart nginx

```

### Paso 6: Probar la Aplicación

  

1. **Abrir el navegador**: Navega a `http://tu_direccion_ip`.

  

2. **Verificar el frontend**: Deberías ver tu aplicación React.

  

3. **Verificar las solicitudes de API**: Asegúrate de que las operaciones de CRUD funcionen accediendo a las rutas de API desde el frontend.



--- 
### Paso 1: Configuración del Entorno en DigitalOcean

  

#### 1.1 Crear una Droplet

  

1. **Iniciar sesión en DigitalOcean**: Ve a [DigitalOcean](https://www.digitalocean.com/) y accede a tu cuenta.

  

2. **Crear una Droplet**:

  

    - Selecciona un sistema operativo (recomendado: Ubuntu).

    - Elige el tamaño de la Droplet (puedes empezar con el plan básico).

    - Configura la autenticación con una clave SSH (asegúrate de tener tu clave SSH añadida a tu cuenta).

  

1. **Completar la creación**: Asigna un nombre a tu Droplet y crea la Droplet. Una vez que esté lista, recibirás una dirección IP.

  

#### 1.2 Conectarse a la Droplet

  

Utiliza SSH para conectarte a tu Droplet desde la terminal:

  

```bash

ssh root@tu_direccion_ip

```

  

### Paso 2: Configurar el Firewall

  

Antes de instalar cualquier software, es buena práctica configurar un firewall.

  

#### 2.1 Instalar UFW

  

1. **Actualizar los paquetes**:

  

```bash

sudo apt update

sudo apt upgrade

```

  

#### 2. **Instalar UFW** (si no está ya instalado):

  

```bash

sudo apt install ufw

```

  

#### 3. **Configurar reglas del firewall**:

  

Permite el tráfico SSH (esto es crucial, ya que podrías perder acceso):

  

```bash

sudo ufw allow OpenSSH

```

  

Permite el tráfico HTTP y HTTPS (puedes omitir HTTPS si no usarás SSL):

  

```bash

sudo ufw allow http

sudo ufw allow https

```

  

#### 4. Activar el firewall:

  

```bash

sudo ufw enable

```

  

### 5. Verificar el estado de UFW:

  

```bash

sudo ufw status

```

  

### Paso 3: Configurar el Backend

  

#### 3.1 Instalar Node.js y npm

  

1. **Instalar Node.js y npm**:

  

#### 3.2 Subir el Código del Backend

  

1. **Transferir archivos a la Droplet**: Usa `scp` para subir el código del backend. Desde tu máquina local:

  

En esta parte, en lugar de hacer eso con scp, simplemente clona tu repo en ~, así es más fácil, ya luego te moves al repo y seguis los siguientes pasos.

  

```bash

scp -r /ruta/a/tu/backend root@tu_direccion_ip:/ruta/destino

```

  

2. **Navegar al directorio del backend**:

  

``` bash

cd /ruta/destino

```

  

4. **Instalar dependencias:**

  

```bash

npm install

```

  

5. **Iniciar el servidor** (puedes usar `pm2` para mantener el proceso activo)

  

```bash

sudo npm install -g pm2

pm2 start index.js

pm2 startup

pm2 save

```

  

### Paso 4: Configurar el Frontend

  

#### 4.1 Instalar Nginx

  

1. **Instalar Nginx**:

  

```bash

sudo apt install nginx

```

  

2. **Verificar que Nginx esté corriendo**:

  

```bash

sudo systemctl status nginx

```

  

#### 4.2 Generar el Build del Frontend

  

1. **Transferir el código del frontend a tu Droplet**:

  

En esta parte lo mismo, clona el repo y te moves al repo, ahí seguís con los siguientes pasos.

  

```bash

scp -r /ruta/a/tu/frontend root@tu_direccion_ip:/ruta/destino/frontend

```

  

2. **Navegar al directorio del frontend**:

  

```bash

cd /ruta/destino/frontend

```

  

3. **Instalar dependencias y crear el build**:

  

```bash

npm install npm run build

```

  

4. **Mover el build a la carpeta de Nginx**:

  

```bash

sudo cp -r build/* /var/www/html/

```

  

### Paso 5: Configurar Nginx para Servir el Frontend y el Backend

  

1. **Editar la configuración de Nginx**:

  

Abre el archivo de configuración de Nginx:

  

```bash

sudo nano /etc/nginx/sites-available/defaul

```

  

Reemplaza el contenido del archivo con la siguiente configuración:

  

```bash

server {    

    listen 80;    

    server_name tu_direccion_ip;      

    location / {        

        root /var/www/html;        

        index index.html index.htm;        

        try_files $uri $uri/ /index.html;    

    }      

    location /api {        

        proxy_pass http://localhost:5000;  # Cambia 5000 al puerto que usa tu backend        

        proxy_http_version 1.1;        

        proxy_set_header Upgrade $http_upgrade;        

        proxy_set_header Connection 'upgrade';        

        proxy_set_header Host $host;        

        proxy_cache_bypass $http_upgrade;    

    }

}

```

  

Esta configuración permite que Nginx sirva tu frontend y redirija las solicitudes de API al backend.

  

2. **Probar la configuración de Nginx**:

  

```bash

sudo nginx -t

```

  

3. **Reiniciar Nginx**:

  

```bash

sudo systemctl restart nginx

```

### Paso 6: Probar la Aplicación

  

1. **Abrir el navegador**: Navega a `http://tu_direccion_ip`.

  

2. **Verificar el frontend**: Deberías ver tu aplicación React.

  

3. **Verificar las solicitudes de API**: Asegúrate de que las operaciones de CRUD funcionen accediendo a las rutas de API desde el frontend.

---

 