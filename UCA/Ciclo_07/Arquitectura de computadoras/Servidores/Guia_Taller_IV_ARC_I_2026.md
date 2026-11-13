# TALLER IV — Arquitectura de Computadoras I
### Protocolos, herramientas y configuraciones orientados al servicio
**Universidad Centroamericana | Ciclo 01, 2026**

---

## Contenido

1. [Introducción y Arquitectura del Sistema](#1-introducción-y-arquitectura-del-sistema)
2. [Diseño de Subredes (Winery y Brewery)](#2-diseño-de-subredes-winery-y-brewery)
3. [Configuración de la Máquina Virtual A — Servidor](#3-configuración-de-la-máquina-virtual-a--servidor)
4. [Instalación y Configuración de DHCP](#4-instalación-y-configuración-del-servidor-dhcp)
5. [Instalación y Configuración de Apache HTTP Server](#5-instalación-y-configuración-de-apache-http-server)
6. [Configuración del Servicio DNS (Bind9)](#6-configuración-del-servicio-dns-bind9)
7. [Creación de la API RESTful con PHP](#7-creación-de-la-api-restful-con-php)
8. [Configuración de la Máquina Virtual B — Cliente](#8-configuración-de-la-máquina-virtual-b--cliente)
9. [Verificación Final y Pruebas](#9-verificación-final-y-pruebas)

---

## 1. Introducción y Arquitectura del Sistema

Este taller consiste en implementar una red corporativa simulada usando dos máquinas virtuales (VMs). La máquina **A** actúa como servidor centralizado que provee múltiples servicios de red, mientras que la máquina **B** actúa como cliente que consume dichos servicios.

### 1.1 Topología de Red

El diseño de red que implementaremos incluye los siguientes componentes:

- **Equipo Anfitrión (Host):** Actúa como gateway hacia el ISP y ejecuta VirtualBox Manager.
- **Server A (VM A):** Servidor con DHCP, DNS y Apache HTTP con API PHP.
- **Cliente B (VM B):** Máquina cliente que obtiene IP automática del DHCP y accede a los servicios del servidor.
- **Red interna:** Utilizando el bloque de direcciones `172.16.x.x`.

### 1.2 Servicios a Configurar en Server A

| Servicio | Descripción |
|---|---|
| **DHCP Server** | Asigna direcciones IP automáticamente a los clientes |
| **DNS Server (Bind9)** | Resuelve nombres de dominio dentro de la red |
| **Apache HTTP Server** | Sirve contenido web por el puerto 80 |
| **API RESTful en PHP** | Endpoint accesible desde la red interna |

> **Prerequisito:** Se asume que ambas máquinas virtuales ya fueron creadas e instaladas en el Taller III con un sistema operativo Linux (preferiblemente Ubuntu Server 22.04 LTS o Debian 11/12). Asegúrese de tener acceso root o sudo en ambas máquinas.

---

## 2. Diseño de Subredes (Winery y Brewery)

El enunciado especifica que utilizaremos la red `172.16.x.x` con un segmento de 8 bits para identificar la subred y 8 bits para los hosts, permitiendo **254 hosts por subred**. Esto equivale a una máscara `/16` dividida en subredes `/24`.

### 2.1 Propuesta de Diseño de Subredes

| Subred | Red | Máscara | Gateway | Rango de Hosts | Broadcast |
|---|---|---|---|---|---|
| **Winery** | 172.16.10.0 | 255.255.255.0 | 172.16.10.1 | 172.16.10.2 – .254 | 172.16.10.255 |
| **Brewery** | 172.16.20.0 | 255.255.255.0 | 172.16.20.1 | 172.16.20.2 – .254 | 172.16.20.255 |

### 2.2 Asignación de IPs Fijas en Server A

El servidor A tendrá dos interfaces de red (además de la interfaz NAT/Bridge hacia el host). Cada interfaz estará conectada a una subred diferente:

- `eth1` (o `enp0s8`): IP fija `172.16.10.1/24` — puerta de enlace de la subred Winery.
- `eth2` (o `enp0s9`): IP fija `172.16.20.1/24` — puerta de enlace de la subred Brewery.

### 2.3 Justificación del Diseño

- El bloque `172.16.x.x` es una red privada clase B según el RFC 1918.
- El **tercer octeto** diferencia cada subred: `.10` para Winery, `.20` para Brewery.
- El **cuarto octeto** identifica cada host dentro de la subred (1–254).
- La dirección `.1` de cada subred se reserva para el gateway (Server A).
- La dirección `.255` es el broadcast y no se asigna a ningún host.

---

## 3. Configuración de la Máquina Virtual A — Servidor

### 3.1 Configuración de Interfaces de Red en VirtualBox

Antes de encender la VM, configure los adaptadores de red en VirtualBox:

1. Abra VirtualBox y seleccione la **VM A** → **Configuración** → **Red**.
2. **Adaptador 1:** Configúrelo como **NAT** (para acceso a Internet durante instalaciones).
3. **Adaptador 2:** Seleccione **Red Interna**, nombre de red: `Winery`.
4. **Adaptador 3:** Seleccione **Red Interna**, nombre de red: `Brewery`.
5. Haga clic en **Aceptar** y encienda la VM.

### 3.2 Identificar las Interfaces en la VM

Una vez dentro del servidor, identifique los nombres de las interfaces:

```bash
# Ver todas las interfaces de red disponibles
ip link show

# Salida esperada (los nombres pueden variar):
# 1: lo          — loopback
# 2: enp0s3      — Adaptador 1 (NAT)
# 3: enp0s8      — Adaptador 2 (Winery)
# 4: enp0s9      — Adaptador 3 (Brewery)
```

### 3.3 Configurar IPs Estáticas (Netplan — Ubuntu)

Edite el archivo de configuración de Netplan (el nombre puede variar, usualmente `00-installer-config.yaml`):

```bash
sudo nano /etc/netplan/00-installer-config.yaml
```

Reemplace el contenido con la siguiente configuración:

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: true           # NAT — obtiene IP automáticamente
    enp0s8:
      dhcp4: false
      addresses:
        - 172.16.10.1/24    # IP del Server A en Winery
    enp0s9:
      dhcp4: false
      addresses:
        - 172.16.20.1/24    # IP del Server A en Brewery
```

Aplique la configuración:

```bash
sudo netplan apply

# Verificar que las IPs quedaron asignadas correctamente
ip addr show
```

> **Si usa Debian con interfaces.d:** Edite `/etc/network/interfaces` en lugar de Netplan. La sintaxis sería: `auto enp0s8` / `iface enp0s8 inet static` / `address 172.16.10.1` / `netmask 255.255.255.0`.

---

## 4. Instalación y Configuración del Servidor DHCP

### 4.1 Instalación del Paquete DHCP

```bash
# Actualizar repositorios
sudo apt update

# Instalar el servidor DHCP
sudo apt install -y isc-dhcp-server
```

### 4.2 Especificar las Interfaces que Escuchará el DHCP

```bash
sudo nano /etc/default/isc-dhcp-server
```

Modifique la línea `INTERFACESv4` para incluir ambas interfaces:

```bash
INTERFACESv4="enp0s8 enp0s9"
INTERFACESv6=""
```

### 4.3 Configuración de los Rangos DHCP

```bash
sudo nano /etc/dhcp/dhcpd.conf
```

Reemplace el contenido del archivo con la siguiente configuración:

```
# Configuración global
default-lease-time 600;
max-lease-time 7200;

# Indicar que este es el servidor DHCP autorizado
authoritative;

# ─── Subred Winery ───────────────────────────────────────
subnet 172.16.10.0 netmask 255.255.255.0 {
  range 172.16.10.100 172.16.10.200;
  option routers 172.16.10.1;
  option domain-name-servers 172.16.10.1;
  option domain-name "winery.local";
}

# ─── Subred Brewery ──────────────────────────────────────
subnet 172.16.20.0 netmask 255.255.255.0 {
  range 172.16.20.100 172.16.20.200;
  option routers 172.16.20.1;
  option domain-name-servers 172.16.20.1;
  option domain-name "brewery.local";
}
```

### 4.4 Iniciar y Habilitar el Servicio DHCP

```bash
# Iniciar el servicio
sudo systemctl start isc-dhcp-server

# Habilitarlo para que inicie automáticamente con el sistema
sudo systemctl enable isc-dhcp-server

# Verificar el estado del servicio
sudo systemctl status isc-dhcp-server
```

Si el servicio está activo, verá el texto `Active: active (running)` en verde.

### 4.5 Verificación de IPs Asignadas

```bash
# Ver las asignaciones DHCP activas
cat /var/lib/dhcp/dhcpd.leases

# Ver log en tiempo real (útil para depuración)
sudo journalctl -u isc-dhcp-server -f
```

---

## 5. Instalación y Configuración de Apache HTTP Server

### 5.1 Instalación de Apache y PHP

```bash
# Instalar Apache y los módulos PHP necesarios
sudo apt install -y apache2 php libapache2-mod-php php-json

# Verificar que Apache está corriendo
sudo systemctl status apache2
```

### 5.2 Habilitar el Firewall para HTTP

```bash
# Permitir tráfico HTTP (puerto 80)
sudo ufw allow 80/tcp
sudo ufw allow 'Apache'

# Si ufw no está activo, habilitarlo
sudo ufw enable
sudo ufw status
```

### 5.3 Verificar que Apache Sirve Páginas

```bash
# Prueba con curl desde el servidor
curl http://localhost

# Debe mostrar el HTML de la página de bienvenida de Apache
```

### 5.4 Configurar un VirtualHost para la API

Crearemos un VirtualHost dedicado para nuestra API con el dominio `api.winery.local`:

```bash
sudo nano /etc/apache2/sites-available/api-winery.conf
```

Contenido del archivo:

```apache
<VirtualHost *:80>
    ServerName api.winery.local
    ServerAlias api.brewery.local
    DocumentRoot /var/www/api

    <Directory /var/www/api>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/api-error.log
    CustomLog ${APACHE_LOG_DIR}/api-access.log combined
</VirtualHost>
```

```bash
# Crear el directorio raíz de la API
sudo mkdir -p /var/www/api

# Activar el sitio y el módulo rewrite
sudo a2ensite api-winery.conf
sudo a2enmod rewrite

# Recargar Apache para aplicar cambios
sudo systemctl reload apache2
```

---

## 6. Configuración del Servicio DNS (Bind9)

### 6.1 Instalación de Bind9

```bash
sudo apt install -y bind9 bind9utils bind9-doc

# Verificar estado
sudo systemctl status bind9
```

### 6.2 Configuración de las Zonas DNS

```bash
sudo nano /etc/bind/named.conf.local
```

Agregue las definiciones de zona:

```
# Zona directa Winery
zone "winery.local" {
    type master;
    file "/etc/bind/zones/db.winery.local";
};

# Zona inversa Winery (172.16.10.x)
zone "10.16.172.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/db.172.16.10";
};

# Zona directa Brewery
zone "brewery.local" {
    type master;
    file "/etc/bind/zones/db.brewery.local";
};
```

### 6.3 Crear los Archivos de Zona

```bash
# Crear el directorio para los archivos de zona
sudo mkdir -p /etc/bind/zones

# Copiar plantilla base
sudo cp /etc/bind/db.local /etc/bind/zones/db.winery.local
sudo nano /etc/bind/zones/db.winery.local
```

Contenido del archivo `db.winery.local`:

```
$TTL    604800
@   IN  SOA     ns1.winery.local. admin.winery.local. (
                      2          ; Serial
                 604800          ; Refresh
                  86400          ; Retry
               2419200           ; Expire
                 604800 )        ; Negative Cache TTL
;
@       IN  NS      ns1.winery.local.
ns1     IN  A       172.16.10.1
server  IN  A       172.16.10.1
api     IN  A       172.16.10.1
@       IN  A       172.16.10.1
```

> Repita el proceso para Brewery (`db.brewery.local`), cambiando el dominio y las IPs por `172.16.20.x`.

### 6.4 Verificar y Reiniciar Bind9

```bash
# Verificar la sintaxis de la configuración
sudo named-checkconf

# Verificar la zona
sudo named-checkzone winery.local /etc/bind/zones/db.winery.local

# Reiniciar el servicio DNS
sudo systemctl restart bind9
sudo systemctl enable bind9

# Probar resolución DNS desde el mismo servidor
dig @172.16.10.1 api.winery.local
nslookup api.winery.local 172.16.10.1
```

---

## 7. Creación de la API RESTful con PHP

### 7.1 Estructura de la API

Crearemos una API RESTful básica con los métodos GET, POST, PUT y DELETE. La API manejará un recurso de ejemplo llamado `productos`.

### 7.2 Crear el Archivo Principal de la API

```bash
sudo nano /var/www/api/index.php
```

Contenido completo de `index.php`:

```php
<?php
// Configurar cabeceras para respuesta JSON y CORS
header('Content-Type: application/json; charset=UTF-8');
header('Access-Control-Allow-Origin: *');
header('Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS');
header('Access-Control-Allow-Headers: Content-Type');

// Datos de ejemplo (en producción se conectaría a una base de datos)
$productos = [
    ['id' => 1, 'nombre' => 'Vino Tinto Reserva',    'precio' => 25.00],
    ['id' => 2, 'nombre' => 'Cerveza Artesanal IPA', 'precio' =>  5.50],
    ['id' => 3, 'nombre' => 'Vino Blanco Chardonnay','precio' => 18.00],
];

// Obtener el método HTTP y parámetros
$method = $_SERVER['REQUEST_METHOD'];
$path   = isset($_GET['path']) ? $_GET['path'] : '';
$id     = isset($_GET['id'])   ? (int)$_GET['id'] : null;

// Manejar preflight CORS
if ($method === 'OPTIONS') {
    http_response_code(204);
    exit;
}

// ─── Enrutamiento ──────────────────────────────────────────
switch ($method) {

    case 'GET':
        if ($id) {
            // GET /api?id=1  →  Obtener un producto por ID
            $found = array_filter($productos, fn($p) => $p['id'] === $id);
            if (empty($found)) {
                http_response_code(404);
                echo json_encode(['error' => 'Producto no encontrado']);
            } else {
                echo json_encode(array_values($found)[0]);
            }
        } else {
            // GET /api  →  Listar todos los productos
            echo json_encode([
                'status' => 'OK',
                'total'  => count($productos),
                'data'   => $productos
            ]);
        }
        break;

    case 'POST':
        // POST /api  →  Crear nuevo producto
        $body = json_decode(file_get_contents('php://input'), true);
        if (!isset($body['nombre'], $body['precio'])) {
            http_response_code(400);
            echo json_encode(['error' => 'Faltan campos: nombre y precio']);
        } else {
            $nuevo = [
                'id'     => count($productos) + 1,
                'nombre' => $body['nombre'],
                'precio' => $body['precio']
            ];
            http_response_code(201);
            echo json_encode(['message' => 'Producto creado', 'data' => $nuevo]);
        }
        break;

    case 'PUT':
        // PUT /api?id=1  →  Actualizar un producto
        $body = json_decode(file_get_contents('php://input'), true);
        echo json_encode(['message' => "Producto $id actualizado", 'data' => $body]);
        break;

    case 'DELETE':
        // DELETE /api?id=1  →  Eliminar un producto
        echo json_encode(['message' => "Producto $id eliminado"]);
        break;

    default:
        http_response_code(405);
        echo json_encode(['error' => 'Método no permitido']);
}
?>
```

### 7.3 Configurar Permisos del Directorio

```bash
# Asignar propiedad al usuario de Apache
sudo chown -R www-data:www-data /var/www/api
sudo chmod -R 755 /var/www/api

# Verificar que el archivo existe
ls -la /var/www/api/
```

### 7.4 Crear `.htaccess` para Rutas Amigables

```bash
sudo nano /var/www/api/.htaccess
```

```apache
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php?path=$1 [QSA,L]
```

### 7.5 Prueba de la API desde el Servidor

```bash
# Probar GET — listar todos los productos
curl http://api.winery.local/

# Si DNS no está listo aún, usar la IP directamente
curl http://172.16.10.1/

# Probar POST — crear un nuevo producto
curl -X POST http://172.16.10.1/ \
     -H 'Content-Type: application/json' \
     -d '{"nombre":"Malbec 2023","precio":30.00}'
```

---

## 8. Configuración de la Máquina Virtual B — Cliente

### 8.1 Configuración del Adaptador de Red en VirtualBox

1. Apague la VM B si está encendida.
2. En VirtualBox, vaya a **Configuración** → **Red** de la VM B.
3. **Adaptador 1:** Seleccione **Red Interna**, nombre: `Winery` (o `Brewery` según corresponda).
4. Guarde y encienda la VM B.

### 8.2 Obtener IP por DHCP

La VM B debería obtener una IP automáticamente. Verifique:

```bash
# Ver la IP asignada (debe estar en el rango 172.16.10.100–200)
ip addr show

# Si no obtuvo IP automáticamente, solicitar una manualmente
sudo dhclient enp0s3

# Confirmar la asignación
ip addr show enp0s3
```

### 8.3 Verificar Conectividad con el Servidor

```bash
# Hacer ping al servidor A (gateway de la red Winery)
ping -c 4 172.16.10.1

# Verificar la tabla de rutas
ip route show
```

### 8.4 Configurar el DNS en el Cliente

```bash
# Editar la configuración de systemd-resolved
sudo nano /etc/systemd/resolved.conf
```

Agregue o modifique estas líneas:

```ini
[Resolve]
DNS=172.16.10.1
Domains=winery.local
```

```bash
# Reiniciar el servicio de resolución DNS
sudo systemctl restart systemd-resolved

# Probar resolución DNS
nslookup api.winery.local
ping api.winery.local
```

### 8.5 Acceder a la API desde el Cliente

```bash
# Instalar curl si no está disponible
sudo apt install -y curl

# Acceder a la API por nombre de dominio
curl http://api.winery.local/

# Acceder directamente por IP (si DNS no está configurado aún)
curl http://172.16.10.1/

# Consultar producto con ID 1
curl http://api.winery.local/?id=1
```

La respuesta debe ser un JSON similar a:

```json
{
  "status": "OK",
  "total": 3,
  "data": [
    { "id": 1, "nombre": "Vino Tinto Reserva",     "precio": 25   },
    { "id": 2, "nombre": "Cerveza Artesanal IPA",  "precio": 5.5  },
    { "id": 3, "nombre": "Vino Blanco Chardonnay", "precio": 18   }
  ]
}
```

---

## 9. Verificación Final y Pruebas

### 9.1 Lista de Verificación Completa

| # | Verificación | Comando (ejecutar en…) |
|---|---|---|
| ☐ | Server A tiene IPs `172.16.10.1` y `172.16.20.1` | `ip addr show` (VM A) |
| ☐ | Servicio DHCP activo | `systemctl status isc-dhcp-server` (VM A) |
| ☐ | Servicio Apache activo | `systemctl status apache2` (VM A) |
| ☐ | Servicio DNS Bind9 activo | `systemctl status bind9` (VM A) |
| ☐ | Cliente B obtuvo IP en rango `.100–.200` | `ip addr show` (VM B) |
| ☐ | Cliente B hace ping al Server A | `ping 172.16.10.1` (VM B) |
| ☐ | DNS resuelve `api.winery.local` | `nslookup api.winery.local` (VM B) |
| ☐ | API responde a solicitudes GET | `curl http://172.16.10.1/` (VM B) |
| ☐ | API responde a solicitudes POST | `curl -X POST ...` (VM B) |

### 9.2 Solución de Problemas Comunes

#### El DHCP no asigna IPs al cliente
- Verifique que ambas VMs están en la misma **Red Interna** de VirtualBox (mismo nombre exacto).
- Confirme que el servicio está activo: `sudo systemctl status isc-dhcp-server`
- Revise los logs: `sudo journalctl -u isc-dhcp-server --since '10 min ago'`

#### Apache no responde
- Verifique el estado: `sudo systemctl status apache2`
- Revise los logs de error: `sudo tail -f /var/log/apache2/error.log`
- Confirme que el firewall permite el puerto 80: `sudo ufw status`

#### El DNS no resuelve los nombres
- Verifique la sintaxis: `sudo named-checkconf && sudo named-checkzone winery.local /etc/bind/zones/db.winery.local`
- Confirme que el cliente apunta al servidor DNS correcto: `cat /etc/resolv.conf`
- Pruebe la resolución directamente: `dig @172.16.10.1 api.winery.local`

#### La API PHP da error 500
- Revise los logs de Apache: `sudo tail -f /var/log/apache2/api-error.log`
- Verifique la sintaxis del PHP: `php -l /var/www/api/index.php`
- Confirme los permisos: `ls -la /var/www/api/`

---

> **Resultado esperado del Taller:** Al finalizar todos los pasos, desde la máquina B deberá poder ejecutar `curl http://api.winery.local/` y recibir la respuesta JSON de la API alojada en el Server A. Esto demostrará que los servicios DHCP, DNS, Apache y PHP están funcionando correctamente como un sistema integrado.

---

*Taller IV — Arquitectura de Computadoras I — Ciclo 01, 2026 — UCA*
