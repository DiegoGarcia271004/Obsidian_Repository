# Guía de despliegue — WarehouseInventory

## Preparación de la Droplet (DigitalOcean)

---

## 1. Requisitos previos

- Droplet con Ubuntu 22.04 LTS
- Acceso SSH como root
- Puerto 80 abierto en el firewall de DigitalOcean

---

## 2. Actualizar el sistema

```bash
apt update && apt upgrade -y
```

---

## 3. Instalar Docker

Usar el script oficial de Docker — instala Docker Engine y el plugin Compose moderno:

```bash
curl -fsSL https://get.docker.com | sh
```

Iniciar el daemon y habilitarlo para que arranque automáticamente:

```bash
systemctl start docker
systemctl enable docker
```

Verificar que todo quedó instalado correctamente:

```bash
docker --version
docker compose version
```

---

## 4. Instalar Git

```bash
apt install git -y
```

---

## 5. Clonar el repositorio

```bash
git clone https://github.com/DiegoGarcia271004/Proyecto-N-capas /opt/warehouse
cd /opt/warehouse
```

---

## 6. Configurar variables de entorno

```bash
cp .env.example .env
nano .env
```

Completar los siguientes valores:

```env
POSTGRES_DB=warehouse_inventory
POSTGRES_USER=warehouse_user
POSTGRES_PASSWORD=una_password_segura

JWT_EXPIRATION_MINUTES=60

# Sin dominio real, dejar en localhost para evitar warnings
DOMAIN=localhost
```

Guardar y salir: `Ctrl+X` → `Y` → `Enter`

---

## 7. Levantar la aplicación

```bash
docker compose -f docker-compose.yml -f docker-compose.prod.yml up -d --build
```

La primera vez tarda varios minutos — está descargando imágenes base y compilando el backend con Maven.

---

## 8. Verificar que todo está corriendo

```bash
# Ver estado de los contenedores
docker compose ps

# Ver logs del backend (buscar "Started WarehouseInventoryApplication")
docker compose logs backend

# Ver logs del frontend/nginx
docker compose logs frontend
```

---

## 9. Crear el usuario administrador

Entrar a la base de datos:

```bash
docker exec -it warehouse_db psql -U warehouse_user -d warehouse_inventory
```

Insertar el usuario admin (reemplazar el hash por el de tu contraseña):

```sql
INSERT INTO users (id, active, password, role, username)
VALUES (
    gen_random_uuid(),
    true,
    '$2a$10$hash_de_tu_password',
    'ADMIN',
    'admin'
);
\q
```

Para generar el hash de una contraseña, usar cualquier generador BCrypt online con 10 rondas, o correr este snippet en Java:

```java
System.out.println(new BCryptPasswordEncoder().encode("tu_password"));
```

---

## 10. Acceder a la aplicación

|Recurso|URL|
|---|---|
|Frontend|`http://IP_DROPLET`|
|Swagger UI|`http://IP_DROPLET/swagger-ui/index.html`|

---

## Comandos útiles post-despliegue

```bash
# Ver logs en tiempo real
docker compose logs -f backend

# Reiniciar solo el backend
docker compose restart backend

# Bajar todo
docker compose down

# Bajar y eliminar la base de datos (⚠️ borra todos los datos)
docker compose down -v

# Actualizar después de un cambio en el código
git pull
docker compose -f docker-compose.yml -f docker-compose.prod.yml up -d --build
```

---

## Solución de problemas frecuentes

| Problema                          | Causa probable           | Solución                                             |
| --------------------------------- | ------------------------ | ---------------------------------------------------- |
| `Cannot connect to Docker daemon` | Docker no está corriendo | `systemctl start docker`                             |
| `variable is not set`             | Falta variable en `.env` | Revisar y completar `.env`                           |
| `port is already allocated`       | Puerto 80 ocupado        | `lsof -i :80` y detener el proceso                   |
| Backend no arranca                | Error de conexión a DB   | Verificar credenciales en `.env`                     |
| Login falla                       | Cookie Secure en HTTP    | Confirmar `JWT_COOKIE_SECURE=false` en prod override |