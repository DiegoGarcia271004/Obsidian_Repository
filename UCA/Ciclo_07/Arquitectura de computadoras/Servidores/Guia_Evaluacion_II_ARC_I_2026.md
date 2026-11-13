# EVALUACIÓN II — Arquitectura de Computadoras I
### Diseño de Soluciones On-Premise
**Universidad Centroamericana | Ciclo 01, 2026**

---

## Contexto

Se debe construir un servidor que atienda a múltiples clientes de una compañía de seguros e inversiones en criptomonedas. El servidor proveerá DHCP, DNS, HTTPS, API REST y FTP, con tres subredes diseñadas mediante VLSM sobre la red `172.30.40.0/22`.

---

## Contenido

1. [Diseño VLSM de la Red](#1-diseño-vlsm-de-la-red)
2. [Arquitectura de VMs en VMware](#2-arquitectura-de-vms-en-vmware)
3. [Configuración de Interfaces de Red del Servidor](#3-configuración-de-interfaces-de-red-del-servidor)
4. [Servicio DHCP](#4-servicio-dhcp)
5. [Enrutamiento entre Subredes y hacia Internet (NAT)](#5-enrutamiento-entre-subredes-y-hacia-internet-nat)
6. [Servicio DNS (Bind9) alojado en DMZ](#6-servicio-dns-bind9-alojado-en-dmz)
7. [Certificados SSL Locales (HTTPS)](#7-certificados-ssl-locales-https)
8. [Servicio Web HTTPS — www.windbag.la y www.crypto.la](#8-servicio-web-https--wwwwindbagla-y-wwwcryptola)
9. [API REST en PHP — api.windbag.la](#9-api-rest-en-php--apiwindbagla)
10. [Scripts Bash de Administración](#10-scripts-bash-de-administración)
11. [Rutas GET en la API para exponer los logs](#11-rutas-get-en-la-api-para-exponer-los-logs)
12. [Servicio FTP (vsftpd)](#12-servicio-ftp-vsftpd)
13. [Copias de Seguridad Programadas](#13-copias-de-seguridad-programadas)
14. [Diagrama de Infraestructura](#14-diagrama-de-infraestructura)
15. [Verificación Final](#15-verificación-final)

---

## 1. Diseño VLSM de la Red

### 1.1 ¿Qué es VLSM?

VLSM (*Variable Length Subnet Masking*) permite dividir una red en subredes de tamaños diferentes, asignando a cada una exactamente el espacio que necesita. Se ordenan las subredes de mayor a menor y se asignan bloques contiguos del espacio disponible.

### 1.2 Cálculo

La red base es `172.30.40.0/22`, que abarca desde `172.30.40.0` hasta `172.30.43.255` (1024 direcciones totales).

Las subredes ordenadas de mayor a menor requerimiento:

- **windbag**: 100 hosts → el bloque más pequeño que los contiene es 128 IPs → **/25** (126 hosts útiles)
- **crypto**: 35 hosts → el bloque más pequeño que los contiene es 64 IPs → **/26** (62 hosts útiles)
- **DMZ**: red de protección, pocos hosts → 16 IPs → **/28** (14 hosts útiles)

### 1.3 Tabla de Subredes

| Subred | Red | Máscara | Gateway | Rango DHCP | Broadcast |
|---|---|---|---|---|---|
| **windbag** | 172.30.40.0/25 | 255.255.255.128 | 172.30.40.1 | .10 – .110 | 172.30.40.127 |
| **crypto** | 172.30.40.128/26 | 255.255.255.192 | 172.30.40.129 | .139 – .189 | 172.30.40.191 |
| **DMZ** | 172.30.40.192/28 | 255.255.255.240 | 172.30.40.193 | .194 – .206 | 172.30.40.207 |

> La DMZ usa una máscara `/28` intencionalmente restrictiva para limitar el número de dispositivos que pueden existir en esa zona, reduciendo la superficie de ataque. Es la práctica estándar en redes corporativas.

---

## 2. Arquitectura de VMs en VMware

### 2.1 Crear los LAN Segments (Redes Internas)

En VMware las redes internas aisladas se llaman **LAN Segments**. Créelas antes de crear las VMs:

1. Abra VMware y vaya a **Edit → Virtual Network Editor**.
2. Haga clic en **Add Network** y cree tres redes de tipo **Host-only** sin DHCP (ya que el DHCP lo manejará el servidor):

| Nombre de segmento | Tipo | DHCP de VMware |
|---|---|---|
| `windbag` | LAN Segment | Desactivado |
| `crypto` | LAN Segment | Desactivado |
| `dmz` | LAN Segment | Desactivado |

> En VMware Workstation los LAN Segments se crean directamente desde la configuración de red de cada VM → **LAN Segments… → Add**. No necesitan configurarse globalmente primero.

### 2.2 Servidor Principal

Cree una VM con los siguientes recursos:

| Parámetro | Valor |
|---|---|
| Nombre | Servidor |
| RAM | 2048 MB |
| CPU | 2 núcleos |
| Disco | 20 GB |
| ISO | Ubuntu Server 22.04 LTS |

Durante la creación seleccione **Custom (Advanced)** para tener control total. Al llegar a la configuración de red, deje el adaptador por defecto como **NAT**. Una vez creada la VM, agréguele los adaptadores adicionales:

1. Haga clic derecho sobre la VM → **Settings → Add → Network Adapter**.
2. Agregue tres adaptadores adicionales:

| NIC | Tipo de red | Propósito |
|---|---|---|
| NIC 1 | NAT | Salida a Internet |
| NIC 2 | LAN Segment → `windbag` | Gateway subred windbag |
| NIC 3 | LAN Segment → `crypto` | Gateway subred crypto |
| NIC 4 | LAN Segment → `dmz` | Gateway subred DMZ |

### 2.3 Clientes (windbag y crypto)

Cree al menos un cliente por subred con recursos mínimos:

| Parámetro | Valor |
|---|---|
| RAM | 512 MB |
| CPU | 1 núcleo |
| Disco | 8 GB |
| NIC 1 | LAN Segment → `windbag` o `crypto` según corresponda |

---

## 3. Configuración de Interfaces de Red del Servidor

### 3.1 Identificar las Interfaces

Una vez instalado el servidor (Ubuntu Server 22.04 LTS), identifique los nombres de las interfaces:

```bash
ip link show
```

En VMware los nombres típicos son:

```
ens33  →  NIC 1 (NAT — salida a Internet)
ens34  →  NIC 2 (windbag)
ens35  →  NIC 3 (crypto)
ens36  →  NIC 4 (DMZ)
```

> Los nombres exactos pueden variar. Siempre verifique con `ip link show` antes de editar cualquier archivo y sustituya los nombres donde corresponda en toda la guía.

### 3.2 Configurar IPs Estáticas con Netplan

```bash
sudo nano /etc/netplan/00-installer-config.yaml
```

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    ens33:
      dhcp4: true                 
    ens34:
      dhcp4: false
      addresses:
        - 172.30.40.1/25         
    ens35:
      dhcp4: false
      addresses:
        - 172.30.40.129/26       
    ens36:
      dhcp4: false
      addresses:
        - 172.30.40.193/28    
```

```bash
sudo netplan apply

# Verificar
ip addr show
```

---

## 4. Servicio DHCP

### 4.1 Instalación

```bash
sudo apt update
sudo apt install -y isc-dhcp-server
```

### 4.2 Especificar Interfaces

```bash
sudo nano /etc/default/isc-dhcp-server
```

```bash
INTERFACESv4="ens34 ens35 ens36"
INTERFACESv6=""
```

### 4.3 Configuración de Rangos

```bash
sudo nano /etc/dhcp/dhcpd.conf
```

```
default-lease-time 600;
max-lease-time 7200;
authoritative;

# ─── Subred windbag ──────────────────────────────────────
subnet 172.30.40.0 netmask 255.255.255.128 {
  range 172.30.40.10 172.30.40.110;
  option routers 172.30.40.1;
  option domain-name-servers 172.30.40.193;
  option domain-name "windbag.la";
}

# ─── Subred crypto ───────────────────────────────────────
subnet 172.30.40.128 netmask 255.255.255.192 {
  range 172.30.40.139 172.30.40.189;
  option routers 172.30.40.129;
  option domain-name-servers 172.30.40.193;
  option domain-name "crypto.la";
}

# ─── Subred DMZ ──────────────────────────────────────────
subnet 172.30.40.192 netmask 255.255.255.240 {
	range 172.30.40.194 172.30.40.206;
	option routers 172.30.40.193;
	option domain-name-servers 172.30.40.193;
}
```

> Note que `option domain-name-servers` apunta a `172.30.40.193` en todas las subredes — esa es la IP del servidor en la DMZ, donde vivirá el DNS.

### 4.4 Iniciar el Servicio

```bash
sudo systemctl start isc-dhcp-server
sudo systemctl enable isc-dhcp-server
sudo systemctl status isc-dhcp-server
```

---

## 5. Enrutamiento entre Subredes y hacia Internet (NAT)

### 5.1 Habilitar IP Forwarding

```bash
sudo nano /etc/sysctl.conf
```

Descomente la línea:

```
net.ipv4.ip_forward=1
```

```bash
sudo sysctl -p
cat /proc/sys/net/ipv4/ip_forward
# Debe mostrar: 1
```

### 5.2 Configurar NAT con iptables

```bash
# NAT hacia Internet por la interfaz NAT de VMware
sudo iptables -t nat -A POSTROUTING -o ens33 -j MASQUERADE

# Permitir reenvío desde cada subred hacia Internet
sudo iptables -A FORWARD -i ens34 -o ens33 -j ACCEPT
sudo iptables -A FORWARD -i ens35 -o ens33 -j ACCEPT
sudo iptables -A FORWARD -i ens36 -o ens33 -j ACCEPT

# Permitir respuestas de vuelta
sudo iptables -A FORWARD -i ens33 -o ens34 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i ens33 -o ens35 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i ens33 -o ens36 -m state --state RELATED,ESTABLISHED -j ACCEPT

# Permitir reenvío entre subredes internas
sudo iptables -A FORWARD -i ens34 -o ens35 -j ACCEPT
sudo iptables -A FORWARD -i ens35 -o ens34 -j ACCEPT
sudo iptables -A FORWARD -i ens34 -o ens36 -j ACCEPT
sudo iptables -A FORWARD -i ens36 -o ens34 -j ACCEPT
sudo iptables -A FORWARD -i ens35 -o ens36 -j ACCEPT
sudo iptables -A FORWARD -i ens36 -o ens35 -j ACCEPT
```

### 5.3 Persistir las Reglas

```bash
sudo apt install -y iptables-persistent
sudo netfilter-persistent save
```

---

## 6. Servicio DNS (Bind9) alojado en DMZ

El DNS se aloja en la interfaz DMZ (`172.30.40.193`) pero debe ser accesible desde windbag y crypto.

### 6.1 Instalación

```bash
sudo apt install -y bind9 bind9utils bind9-doc
```

### 6.2 Configurar Opciones Globales

```bash
sudo nano /etc/bind/named.conf.options
```

```
options {
    directory "/var/cache/bind";

    listen-on { 172.30.40.193; 127.0.0.1; };

    allow-query {
        localhost;
        172.30.40.0/25;     # windbag
        172.30.40.128/26;   # crypto
        172.30.40.192/28;   # DMZ
    };

    forwarders {
        8.8.8.8;
        8.8.4.4;
    };

    forward only;
    dnssec-validation no;
};
```

### 6.3 Definir las Zonas

```bash
sudo nano /etc/bind/named.conf.local
```

```
# Zona windbag.la
zone "windbag.la" {
    type master;
    file "/etc/bind/zones/db.windbag.la";
};

# Zona crypto.la
zone "crypto.la" {
    type master;
    file "/etc/bind/zones/db.crypto.la";
};

# Zona inversa windbag
zone "40.30.172.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/db.172.30.40";
};
```

### 6.4 Crear los Archivos de Zona

```bash
sudo mkdir -p /etc/bind/zones
```

**Zona windbag.la:**

```bash
sudo nano /etc/bind/zones/db.windbag.la
```

```
$TTL    604800
@   IN  SOA     ns1.windbag.la. admin.windbag.la. (
                      2          ; Serial
                 604800          ; Refresh
                  86400          ; Retry
               2419200           ; Expire
                 604800 )        ; Negative Cache TTL
;
@       IN  NS      ns1.windbag.la.
ns1     IN  A       172.30.40.193
@       IN  A       172.30.40.1
www     IN  A       172.30.40.193
api     IN  A       172.30.40.193
```

**Zona crypto.la:**

```bash
sudo nano /etc/bind/zones/db.crypto.la
```

```
$TTL    604800
@   IN  SOA     ns1.crypto.la. admin.crypto.la. (
                      2          ; Serial
                 604800          ; Refresh
                  86400          ; Retry
               2419200           ; Expire
                 604800 )        ; Negative Cache TTL
;
@       IN  NS      ns1.crypto.la.
ns1     IN  A       172.30.40.193
@       IN  A       172.30.40.129
www     IN  A       172.30.40.193
```

### 6.5 Verificar y Reiniciar

```bash
sudo named-checkconf
sudo named-checkzone windbag.la /etc/bind/zones/db.windbag.la
sudo named-checkzone crypto.la /etc/bind/zones/db.crypto.la

sudo systemctl restart bind9
sudo systemctl enable bind9

# Prueba
dig @172.30.40.193 www.windbag.la
dig @172.30.40.193 www.crypto.la
```

---

## 7. Certificados SSL Locales (HTTPS)

Como no hay un dominio real registrado, generaremos certificados **autofirmados** con OpenSSL. Esto permite que Apache sirva HTTPS — los navegadores mostrarán una advertencia de seguridad que se acepta manualmente, pero el cifrado funciona correctamente.

### 7.1 Instalar OpenSSL

```bash
sudo apt install -y openssl
```

### 7.2 Crear los Certificados

```bash
# Crear directorio para los certificados
sudo mkdir -p /etc/ssl/localcerts

# Certificado para windbag.la
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout /etc/ssl/localcerts/windbag.key \
  -out /etc/ssl/localcerts/windbag.crt \
  -subj "/C=SV/ST=SanSalvador/L=SanSalvador/O=UCA/CN=www.windbag.la" \
  -addext "subjectAltName=DNS:www.windbag.la,DNS:windbag.la,DNS:api.windbag.la"

# Certificado para crypto.la
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout /etc/ssl/localcerts/crypto.key \
  -out /etc/ssl/localcerts/crypto.crt \
  -subj "/C=SV/ST=SanSalvador/L=SanSalvador/O=UCA/CN=www.crypto.la" \
  -addext "subjectAltName=DNS:www.crypto.la,DNS:crypto.la"
```

---

## 8. Servicio Web HTTPS — www.windbag.la y www.crypto.la

### 8.1 Instalar Apache y PHP

```bash
sudo apt install -y apache2 php libapache2-mod-php php-json

# Habilitar módulos necesarios
sudo a2enmod ssl rewrite headers
sudo systemctl restart apache2
```

### 8.2 Crear los Directorios y Landing Pages

**Landing page windbag:**

```bash
sudo mkdir -p /var/www/windbag
sudo nano /var/www/windbag/index.html
```

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>windbag.la</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: Arial, sans-serif;
      background: #0a0a2e;
      color: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }
    .card {
      text-align: center;
      padding: 60px 80px;
      background: rgba(255,255,255,0.05);
      border: 1px solid rgba(255,255,255,0.1);
      border-radius: 16px;
    }
    h1 { font-size: 3rem; color: #4fc3f7; margin-bottom: 12px; }
    p  { font-size: 1.2rem; color: #aaa; }
    .badge {
      display: inline-block;
      margin-top: 20px;
      padding: 6px 18px;
      background: #4fc3f7;
      color: #000;
      border-radius: 20px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="card">
    <h1>windbag</h1>
    <p>Subred Windbag — Compania de Seguros e Inversiones</p>
    <span class="badge">172.30.40.0/25</span>
  </div>
</body>
</html>
```

**Landing page crypto:**

```bash
sudo mkdir -p /var/www/crypto
sudo nano /var/www/crypto/index.html
```

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>crypto.la</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: Arial, sans-serif;
      background: #0d1f0d;
      color: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }
    .card {
      text-align: center;
      padding: 60px 80px;
      background: rgba(255,255,255,0.05);
      border: 1px solid rgba(255,255,255,0.1);
      border-radius: 16px;
    }
    h1 { font-size: 3rem; color: #69f0ae; margin-bottom: 12px; }
    p  { font-size: 1.2rem; color: #aaa; }
    .badge {
      display: inline-block;
      margin-top: 20px;
      padding: 6px 18px;
      background: #69f0ae;
      color: #000;
      border-radius: 20px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="card">
    <h1>crypto</h1>
    <p>Subred Crypto - Inversiones en Criptomonedas</p>
    <span class="badge">172.30.40.128/26</span>
  </div>
</body>
</html>
```

### 8.3 Crear los VirtualHosts HTTPS

**VirtualHost windbag:**

```bash
sudo nano /etc/apache2/sites-available/windbag.conf
```

```apache
<VirtualHost *:443>
    ServerName www.windbag.la
    ServerAlias windbag.la
    DocumentRoot /var/www/windbag

    SSLEngine on
    SSLCertificateFile    /etc/ssl/localcerts/windbag.crt
    SSLCertificateKeyFile /etc/ssl/localcerts/windbag.key

    <Directory /var/www/windbag>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog  ${APACHE_LOG_DIR}/windbag-error.log
    CustomLog ${APACHE_LOG_DIR}/windbag-access.log combined
</VirtualHost>

<VirtualHost *:80>
    ServerName www.windbag.la
    ServerAlias windbag.la
    Redirect permanent / https://www.windbag.la/
</VirtualHost>
```

**VirtualHost crypto:**

```bash
sudo nano /etc/apache2/sites-available/crypto.conf
```

```apache
<VirtualHost *:443>
    ServerName www.crypto.la
    ServerAlias crypto.la
    DocumentRoot /var/www/crypto

    SSLEngine on
    SSLCertificateFile    /etc/ssl/localcerts/crypto.crt
    SSLCertificateKeyFile /etc/ssl/localcerts/crypto.key

    <Directory /var/www/crypto>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog  ${APACHE_LOG_DIR}/crypto-error.log
    CustomLog ${APACHE_LOG_DIR}/crypto-access.log combined
</VirtualHost>

<VirtualHost *:80>
    ServerName www.crypto.la
    ServerAlias crypto.la
    Redirect permanent / https://www.crypto.la/
</VirtualHost>
```

### 8.4 Activar los Sitios

```bash
sudo a2ensite windbag.conf
sudo a2ensite crypto.conf
sudo systemctl reload apache2

# Prueba desde el servidor
curl -k https://www.windbag.la/
curl -k https://www.crypto.la/
```

> El flag `-k` indica a curl que acepte el certificado autofirmado sin error.

---

## 9. API REST en PHP — api.windbag.la

### 9.1 Crear el Directorio de la API

```bash
sudo mkdir -p /var/www/api
sudo mkdir -p /var/log/api-scripts
```

### 9.2 VirtualHost de la API

```bash
sudo nano /etc/apache2/sites-available/api-windbag.conf
```

```apache
<VirtualHost *:443>
    ServerName api.windbag.la
    DocumentRoot /var/www/api

    SSLEngine on
    SSLCertificateFile    /etc/ssl/localcerts/windbag.crt
    SSLCertificateKeyFile /etc/ssl/localcerts/windbag.key

    <Directory /var/www/api>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog  ${APACHE_LOG_DIR}/api-error.log
    CustomLog ${APACHE_LOG_DIR}/api-access.log combined
</VirtualHost>

<VirtualHost *:80>
    ServerName api.windbag.la
    Redirect permanent / https://api.windbag.la/
</VirtualHost>
```

```bash
sudo a2ensite api-windbag.conf
sudo systemctl reload apache2
```

### 9.3 Archivo .htaccess

```bash
sudo nano /var/www/api/.htaccess
```

```apache
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php?path=$1 [QSA,L]
```

### 9.4 Archivo Principal index.php

```bash
sudo nano /var/www/api/index.php
```

```php
<?php
header('Content-Type: application/json; charset=UTF-8');
header('Access-Control-Allow-Origin: *');
header('Access-Control-Allow-Methods: GET, OPTIONS');
header('Access-Control-Allow-Headers: Content-Type');

if ($_SERVER['REQUEST_METHOD'] === 'OPTIONS') {
    http_response_code(204); exit;
}

// Archivos de log generados por los scripts bash
define('LOG_API',    '/var/log/api-scripts/api_health.txt');
define('LOG_DHCP',   '/var/log/api-scripts/dhcp_renew.txt');
define('LOG_CLIENT', '/var/log/api-scripts/dhcp_clients.txt');
define('LOG_LEASE',  '/var/log/api-scripts/dhcp_leases.txt');

$path   = isset($_GET['path']) ? trim($_GET['path'], '/') : '';
$method = $_SERVER['REQUEST_METHOD'];

// ─── Función para leer y parsear un log TXT ───────────────
function readLog($file) {
    if (!file_exists($file)) {
        return ['error' => 'Log no encontrado', 'file' => $file];
    }
    $lines = file($file, FILE_IGNORE_NEW_LINES | FILE_SKIP_EMPTY_LINES);
    return [
        'total_registros' => count($lines),
        'registros'       => $lines
    ];
}

// ─── Enrutamiento ─────────────────────────────────────────
if ($method === 'GET') {
    switch ($path) {

        case 'api/health':
            
            echo json_encode([
                'descripcion' => 'Registros de salud del API PHP (cada 30s)',
                'data'        => readLog(LOG_API)
            ]);
            break;

        case 'api/dhcp-renew':
            
            echo json_encode([
                'descripcion' => 'Registros de reasignacion DHCP (cada 1min)',
                'data'        => readLog(LOG_DHCP)
            ]);
            break;

        case 'api/dhcp-clients':
            
            echo json_encode([
                'descripcion' => 'Clientes conectados al DHCP (cada 2min)',
                'data'        => readLog(LOG_CLIENT)
            ]);
            break;

        case 'api/leases':
            
            echo json_encode([
                'descripcion' => 'Bitacora de asignaciones IP/MAC',
                'data'        => readLog(LOG_LEASE)
            ]);
            break;

        case 'api/customer':
            // Ruta de ejemplo del enunciado
            echo json_encode([
                'status'    => 'OK',
                'endpoint'  => 'customer',
                'message'   => 'Servicio de clientes activo',
                'timestamp' => date('Y-m-d H:i:s')
            ]);
            break;

        default:
            echo json_encode([
                'status'  => 'OK',
                'api'     => 'api.windbag.la',
                'version' => '1.0',
                'rutas'   => [
                    'GET /api/customer',
                    'GET /api/health',
                    'GET /api/dhcp-renew',
                    'GET /api/dhcp-clients',
                    'GET /api/leases'
                ]
            ]);
    }
} else {
    http_response_code(405);
    echo json_encode(['error' => 'Metodo no permitido']);
}
?>
```

```bash
sudo chown -R www-data:www-data /var/www/api
sudo chmod -R 755 /var/www/api
sudo chown -R www-data:www-data /var/log/api-scripts
```

---

## 10. Scripts Bash de Administración

Todos los scripts se guardarán en `/opt/scripts/` y sus logs en `/var/log/api-scripts/`.

```bash
sudo mkdir -p /opt/scripts
sudo mkdir -p /var/log/api-scripts
```

### 10.1 Script 2.1 — Salud del API cada 30 segundos

```bash
sudo nano /opt/scripts/check_api.sh
```

```bash
#!/bin/bash
# Verifica que el API PHP responde correctamente cada 30 segundos

LOG="/var/log/api-scripts/api_health.txt"
URL="https://api.windbag.la/api/customer"

while true; do
    TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')
    HTTP_CODE=$(curl -sk -o /dev/null -w "%{http_code}" "$URL")

    if [ "$HTTP_CODE" == "200" ]; then
        STATUS="OK"
    else
        STATUS="ERROR (HTTP $HTTP_CODE)"
    fi

    echo "[$TIMESTAMP] API $URL - Estado: $STATUS" >> "$LOG"
    sleep 30
done
```

### 10.2 Script 2.2 — Reasignación DHCP cada 1 minuto

```bash
sudo nano /opt/scripts/dhcp_renew.sh
```

```bash
#!/bin/bash
# Fuerza la reasignación de IPs dinámicas del DHCP cada 1 minuto

LOG="/var/log/api-scripts/dhcp_renew.txt"
LEASES="/var/lib/dhcp/dhcpd.leases"

while true; do
    TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')

    # Eliminar leases expirados del archivo para forzar reasignacion
    BEFORE=$(grep -c "binding state active" "$LEASES" 2>/dev/null || echo 0)

    # Enviar senal al DHCP para que procese leases sin reiniciar el servicio
    kill -HUP $(cat /var/run/dhcp-server/dhcpd.pid) 2>/dev/null

    sleep 2
    AFTER=$(grep -c "binding state active" "$LEASES" 2>/dev/null || echo 0)

    echo "[$TIMESTAMP] DHCP reasignacion - Leases antes: $BEFORE | Leases despues: $AFTER" >> "$LOG"

    sleep 58
done
```

### 10.3 Script 2.3 — Clientes conectados cada 2 minutos

```bash
sudo nano /opt/scripts/dhcp_clients.sh
```

```bash
#!/bin/bash
# Cuenta cuántos clientes están conectados al DHCP cada 2 minutos

LOG="/var/log/api-scripts/dhcp_clients.txt"
LEASES="/var/lib/dhcp/dhcpd.leases"

while true; do
    TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')

    # Contar leases activos (lineas que contienen binding state active)
    ACTIVE=$(grep -c "binding state active" "$LEASES" 2>/dev/null || echo 0)

    echo "[$TIMESTAMP] Clientes DHCP activos: $ACTIVE" >> "$LOG"

    # Listar IPs activas
    grep -A2 "binding state active" "$LEASES" 2>/dev/null \
        | grep "lease " \
        | awk '{print "  -> IP: " $2}' >> "$LOG"

    sleep 120
done
```

### 10.4 Script 2.4 — Bitácora de asignaciones IP/MAC

```bash
sudo nano /opt/scripts/dhcp_leases_log.sh
```

```bash
#!/bin/bash
# Registra en bitácora cada asignación IP con MAC, hostname y SO

LOG="/var/log/api-scripts/dhcp_leases.txt"
LEASES="/var/lib/dhcp/dhcpd.leases"
PROCESSED="/var/log/api-scripts/.processed_leases"

# Verificar que nmap esté instalado
if ! command -v nmap &>/dev/null; then
    sudo apt install -y nmap
fi

touch "$PROCESSED"

while true; do
    TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')

    awk '
    /^lease / { ip = $2 }
    /hardware ethernet/ { mac = $3; gsub(/;/, "", mac) }
    /client-hostname/ { hostname = $2; gsub(/[";]/, "", hostname) }
    /binding state active/ { active = 1 }
    /^}/ {
        if (active && ip != "") {
            print ip, mac, hostname
            ip=""; mac=""; hostname=""; active=0
        }
    }
    ' "$LEASES" | while read -r IP MAC HOST; do
        KEY="${IP}_${MAC}"
        if ! grep -q "$KEY" "$PROCESSED" 2>/dev/null; then

            # Intentar detectar SO con nmap
            OS=$(nmap -O --osscan-guess "$IP" 2>/dev/null \
                | grep "OS details\|Aggressive OS" \
                | head -1 \
                | sed 's/.*: //')

            # Si nmap no logra detectarlo
            if [ -z "$OS" ]; then
                OS="No detectado"
            fi

            echo "[$TIMESTAMP] IP: $IP | MAC: $MAC | Hostname: ${HOST:-desconocido} | OS: $OS" >> "$LOG"
            echo "$KEY" >> "$PROCESSED"
        fi
    done

    sleep 30
done
```

### 10.5 Dar permisos y ejecutar como servicios systemd

Para que los scripts corran automáticamente al iniciar el servidor, créelos como servicios:

```bash
sudo chmod +x /opt/scripts/*.sh
```

**Servicio para check_api:**

```bash
sudo nano /etc/systemd/system/check-api.service
```

```ini
[Unit]
Description=Monitor de salud del API PHP
After=network.target apache2.service

[Service]
Type=simple
ExecStart=/opt/scripts/check_api.sh
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```

```ini
[Unit]
Description=Bitacora de asignaciones IP/MAC/OS
After=network.target isc-dhcp-server.service

[Service]
Type=simple
ExecStart=/opt/scripts/dhcp_leases_log.sh
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```

Repita el mismo patrón para los otros tres scripts creando:
- `/etc/systemd/system/dhcp-renew.service` → ExecStart=/opt/scripts/dhcp_renew.sh
- `/etc/systemd/system/dhcp-clients.service` → ExecStart=/opt/scripts/dhcp_clients.sh
- `/etc/systemd/system/dhcp-leases-log.service` → ExecStart=/opt/scripts/dhcp_leases_log.sh

Activar todos:

```bash
sudo systemctl daemon-reload
sudo systemctl enable check-api dhcp-renew dhcp-clients dhcp-leases-log
sudo systemctl start  check-api dhcp-renew dhcp-clients dhcp-leases-log

# Verificar que todos corren
sudo systemctl status check-api
sudo systemctl status dhcp-renew
sudo systemctl status dhcp-clients
sudo systemctl status dhcp-leases-log
```

---

## 11. Rutas GET en la API para exponer los logs

Las rutas ya están implementadas en el `index.php` del paso 9.4. Verifique que responden correctamente:

```bash
# Desde el servidor o cualquier cliente con curl

# 2.1 — Salud del API
curl -k https://api.windbag.la/api/health

# 2.2 — Registros de reasignación DHCP
curl -k https://api.windbag.la/api/dhcp-renew

# 2.3 — Clientes conectados
curl -k https://api.windbag.la/api/dhcp-clients

# 2.4 — Bitácora IP/MAC
curl -k https://api.windbag.la/api/leases

# Ruta de ejemplo del enunciado
curl -k https://api.windbag.la/api/customer
```

Cada ruta devuelve un JSON con los registros del archivo TXT correspondiente.

---

## 12. Servicio FTP (vsftpd)

El FTP permite que desde un cliente de cualquier subred se pueda conectar al servidor y editar los archivos PHP de Apache directamente.

### 12.1 Instalación

```bash
sudo apt install -y vsftpd
```

### 12.2 Crear Usuario FTP

```bash
# Crear usuario dedicado para FTP
sudo useradd -m -s /bin/bash ftpuser
sudo passwd ftpuser
# Ingrese una contraseña segura cuando se solicite

# Dar permisos sobre los directorios web
sudo usermod -aG www-data ftpuser
sudo chown -R ftpuser:www-data /var/www/api
sudo chown -R ftpuser:www-data /var/www/windbag
sudo chown -R ftpuser:www-data /var/www/crypto
sudo chmod -R 775 /var/www/api /var/www/windbag /var/www/crypto
```

### 12.3 Configurar vsftpd

```bash
sudo nano /etc/vsftpd.conf
```

Reemplace el contenido con:

```
# Configuración general
listen=YES
listen_ipv6=NO
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES

# Jaula al directorio home del usuario (chroot)
chroot_local_user=YES
allow_writeable_chroot=YES
user_sub_token=$USER
local_root=/var/www

# Rango de puertos pasivos (para clientes detrás de NAT)
pasv_enable=YES
pasv_min_port=40000
pasv_max_port=50000

# Logs
xferlog_file=/var/log/vsftpd.log
log_ftp_protocol=YES

# Limitar acceso solo al usuario ftpuser
userlist_enable=YES
userlist_file=/etc/vsftpd.userlist
userlist_deny=NO
```

```bash
# Agregar el usuario a la lista permitida
echo "ftpuser" | sudo tee /etc/vsftpd.userlist

# Iniciar y habilitar vsftpd
sudo systemctl start vsftpd
sudo systemctl enable vsftpd
sudo systemctl status vsftpd
```

### 12.4 Abrir el Puerto FTP en el Firewall

```bash
sudo ufw allow 20/tcp
sudo ufw allow 21/tcp
sudo ufw allow 40000:50000/tcp
```

### 12.5 Conectarse desde un Cliente

Desde cualquier cliente en windbag o crypto:

```bash
# Instalar cliente FTP
sudo apt install -y ftp

# Conectar al servidor (usar IP del servidor en la subred del cliente)
ftp 172.30.40.1

# Ingresar usuario: ftpuser
# Ingresar contraseña: (la que configuró)

# Navegar a los archivos PHP
ftp> cd api
ftp> ls
ftp> get index.php          # descargar archivo
ftp> put index.php          # subir archivo modificado
```

---
me quede aca

## 13. Copias de Seguridad Programadas

### 13.1 Script de Backup

```bash
sudo nano /opt/scripts/backup.sh
```

```bash
#!/bin/bash

TIMESTAMP=$(date '+%Y%m%d_%H%M%S')
BACKUP_DIR="/var/backups/infraestructura"
mkdir -p "$BACKUP_DIR"

ARCHIVE="$BACKUP_DIR/backup_$TIMESTAMP.tar.gz"
LOG="$BACKUP_DIR/backup.log"

echo "[$TIMESTAMP] Iniciando backup..." >> "$LOG"


tar -czf "$ARCHIVE" \
    /etc/bind/               \
    /etc/dhcp/               \
    /etc/default/isc-dhcp-server \
    /var/lib/dhcp/dhcpd.leases   \
    /etc/iptables/           \
    /etc/vsftpd.conf         \
    /etc/vsftpd.userlist     \
    /etc/netplan/            \
    /opt/scripts/            \
    2>> "$LOG"

if [ $? -eq 0 ]; then
    SIZE=$(du -sh "$ARCHIVE" | cut -f1)
    echo "[$TIMESTAMP] Backup completado: $ARCHIVE ($SIZE)" >> "$LOG"
else
    echo "[$TIMESTAMP] ERROR: Backup fallido" >> "$LOG"
fi

find "$BACKUP_DIR" -name "backup_*.tar.gz" -mtime +7 -delete
echo "[$TIMESTAMP] Backups antiguos eliminados" >> "$LOG"
```

### 13.2 Programar con Cron

```bash
sudo chmod +x /opt/scripts/backup.sh

# Abrir el crontab
sudo crontab -e
```

Agregue la siguiente línea para ejecutar el backup todos los días a las 2:00 AM:

```
0 2 * * * /opt/scripts/backup.sh
```

### 13.3 Verificar los Backups

```bash
# Ver los archivos de backup generados
ls -lh /var/backups/infraestructura/

# Ver el log de backups
cat /var/backups/infraestructura/backup.log

# Ejecutar manualmente para probar
sudo /opt/scripts/backup.sh
```

---

## 14. Diagrama de Infraestructura


## 15. Verificación Final

### 15.1 Lista de Verificación Completa

| #   | Verificación                          | Comando                                       |
| --- | ------------------------------------- | --------------------------------------------- |
| ☐   | Interfaces con IPs correctas          | `ip addr show`                                |
| ☐   | DHCP activo                           | `systemctl status isc-dhcp-server`            |
| ☐   | Cliente windbag obtiene IP .10–.110   | `ip addr show` (cliente)                      |
| ☐   | Cliente crypto obtiene IP .139–.189   | `ip addr show` (cliente)                      |
| ☐   | IP forwarding activo                  | `cat /proc/sys/net/ipv4/ip_forward`           |
| ☐   | Ping entre subredes                   | `ping 172.30.40.129` (desde windbag)          |
| ☐   | Clientes tienen Internet              | `ping 8.8.8.8` (cliente)                      |
| ☐   | DNS resuelve windbag.la               | `dig @172.30.40.193 www.windbag.la`           |
| ☐   | DNS resuelve crypto.la                | `dig @172.30.40.193 www.crypto.la`            |
| ☐   | HTTPS windbag funciona                | `curl -k https://www.windbag.la/`             |
| ☐   | HTTPS crypto funciona                 | `curl -k https://www.crypto.la/`              |
| ☐   | API responde                          | `curl -k https://api.windbag.la/api/customer` |
| ☐   | Ruta /api/health devuelve JSON        | `curl -k https://api.windbag.la/api/health`   |
| ☐   | Ruta /api/leases devuelve JSON        | `curl -k https://api.windbag.la/api/leases`   |
| ☐   | FTP acepta conexión desde cliente     | `ftp 172.30.40.1` (cliente)                   |
| ☐   | Backup se ejecuta correctamente       | `sudo /opt/scripts/backup.sh`                 |
| ☐   | Scripts bash corriendo como servicios | `systemctl status check-api`                  |

### 15.2 Prueba completa desde un cliente

```bash
# Desde un cliente en windbag, ejecutar todo esto:

# 1. Ver IP obtenida
ip addr show

# 2. Ping al gateway
ping -c 2 172.30.40.1

# 3. Ping a la otra subred
ping -c 2 172.30.40.129

# 4. Ping a Internet
ping -c 2 8.8.8.8

# 5. Resolver dominios
nslookup www.windbag.la
nslookup www.crypto.la

# 6. Acceder a sitios web
curl -k https://www.windbag.la/
curl -k https://www.crypto.la/

# 7. Consumir la API
curl -k https://api.windbag.la/api/customer
curl -k https://api.windbag.la/api/health
curl -k https://api.windbag.la/api/leases
curl -k https://api.windbag.la/api/dhcp-renew
curl -k https://api.windbag.la/api/dhcp-clients

# 8. Conectar por FTP
ftp 172.30.40.1
# ver backups
ls -lh /var/backups/infraestructura/
```

---

> **Resultado esperado:** Un servidor centralizado con cuatro interfaces de red que atiende tres subredes diseñadas con VLSM, provee DHCP, DNS en DMZ, dos sitios web HTTPS, una API REST con rutas que exponen logs en tiempo real, acceso FTP a los archivos del servidor, scripts de monitoreo automático y copias de seguridad programadas — todo funcionando simultáneamente desde cualquier cliente conectado a cualquier subred.

---

*Evaluación II — Arquitectura de Computadoras I — Ciclo 01, 2026 — UCA*
