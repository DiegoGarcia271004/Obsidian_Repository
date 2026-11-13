# TALLER VI — Arquitectura de Computadoras I
### Herramientas y configuraciones orientados al servicio del cliente
**Universidad Centroamericana | Ciclo 01, 2026**

---

## Contexto

Este taller **parte del estado final del Taller IV**. Se asume que el Server A ya tiene configurados y funcionando los siguientes servicios:

- IPs estáticas: `172.16.10.1` (Winery) y `172.16.20.1` (Brewery)
- Servidor DHCP sirviendo ambas subredes
- Servidor DNS Bind9 con las zonas `winery.local` y `brewery.local`
- Apache HTTP Server con la API RESTful en PHP

Lo que se añade en este taller es:

1. Enrutamiento entre subredes Winery y Brewery
2. NAT para que los clientes puedan salir a Internet
3. Una tercera máquina virtual C como cliente adicional

---

## Contenido

1. [Establecer Enrutamiento entre Winery y Brewery](#1-establecer-enrutamiento-entre-winery-y-brewery)
2. [Verificar Comunicación entre Subredes por Ping](#2-verificar-comunicación-entre-subredes-por-ping)
3. [Acceso al Servidor Web desde cualquier Subred](#3-acceso-al-servidor-web-desde-cualquier-subred)
4. [Configurar NAT para Acceso a Internet desde los Clientes](#4-configurar-nat-para-acceso-a-internet-desde-los-clientes)
5. [Crear la Máquina Virtual C](#5-crear-la-máquina-virtual-c)
6. [Verificación Final y Pruebas](#6-verificación-final-y-pruebas)

---

## 1. Establecer Enrutamiento entre Winery y Brewery

### ¿Por qué es necesario?

Por defecto, dos subredes distintas no se comunican entre sí aunque estén en el mismo servidor. El Server A tiene una interfaz en cada subred, pero el sistema operativo no reenvía paquetes de una interfaz a la otra a menos que se le indique explícitamente. A eso se le llama **enrutamiento** o *IP forwarding*.

### 1.1 Habilitar IP Forwarding en Server A

El IP forwarding le dice al kernel de Linux que puede reenviar paquetes que llegan por una interfaz hacia otra interfaz distinta — es decir, actuar como router.

```bash
# Verificar el estado actual (0 = desactivado, 1 = activado)
cat /proc/sys/net/ipv4/ip_forward
```

Para activarlo de forma permanente (que persista tras reinicios):

```bash
sudo nano /etc/sysctl.conf
```

Busque la línea siguiente y descoméntela (elimine el `#` del inicio):

```
net.ipv4.ip_forward=1
```

Aplique el cambio sin necesidad de reiniciar:

```bash
sudo sysctl -p

# Verificar que quedó activado
cat /proc/sys/net/ipv4/ip_forward
# Debe mostrar: 1
```

### 1.2 Verificar las Rutas Existentes en Server A

Con el IP forwarding activado, el Server A ya conoce ambas subredes porque tiene una interfaz en cada una. Verifique que las rutas están presentes:

```bash
ip route show

# Debe mostrar algo similar a:
# 172.16.10.0/24 dev enp0s8 proto kernel scope link src 172.16.10.1
# 172.16.20.0/24 dev enp0s9 proto kernel scope link src 172.16.20.1
```

Esto significa que el Server A ya sabe cómo llegar a ambas subredes. El IP forwarding es suficiente para que él pueda enrutar tráfico entre ellas.

### 1.3 Configurar la Ruta en los Clientes

Los clientes también necesitan saber cómo llegar a la subred opuesta. Deben indicarle a su gateway (el Server A) que él es quien sabe cómo llegar a la otra subred.

**En el Cliente B (conectado a Winery)**, para alcanzar Brewery:

```bash
# Agregar ruta hacia Brewery a través del gateway de Winery
sudo ip route add 172.16.20.0/24 via 172.16.10.1

# Verificar que la ruta fue agregada
ip route show
```

Para que esta ruta persista tras reinicios, agréguela en Netplan:

```bash
sudo nano /etc/netplan/00-installer-config.yaml
```

```yaml
network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: true
      routes:
        - to: 172.16.20.0/24
          via: 172.16.10.1
```

```bash
sudo netplan apply
```

> **Nota sobre nombres de interfaces en VMware:** En VMware las interfaces de red suelen llamarse `ens33`, `ens34`, `ens35` en lugar de `enp0s3`, `enp0s8`, `enp0s9`. Verifique los nombres exactos con `ip link show` antes de editar cualquier archivo de configuración y sustitúyalos donde corresponda a lo largo de esta guía.

> Si hubiera clientes en Brewery que necesiten alcanzar Winery, se haría el proceso inverso: `sudo ip route add 172.16.10.0/24 via 172.16.20.1`

---

## 2. Verificar Comunicación entre Subredes por Ping

### 2.1 Configurar el Firewall del Server A

Antes de probar el ping, asegúrese de que el firewall del Server A permite el tráfico entre interfaces (tráfico de reenvío):

```bash
# Permitir tráfico entre las dos interfaces internas
sudo ufw allow in on enp0s8
sudo ufw allow in on enp0s9
sudo ufw allow forward

# Alternativamente, con iptables (más explícito)
sudo iptables -A FORWARD -i enp0s8 -o enp0s9 -j ACCEPT
sudo iptables -A FORWARD -i enp0s9 -o enp0s8 -j ACCEPT
```

Para hacer las reglas de iptables permanentes:

```bash
sudo apt install -y iptables-persistent
sudo netfilter-persistent save
```

### 2.2 Prueba de Ping entre Subredes

**Desde el Cliente B (Winery) hacia el Server A en Brewery:**

```bash
# Ping al Server A por su IP en Brewery
ping -c 4 172.16.20.1

# Respuesta esperada:
# 4 packets transmitted, 4 received, 0% packet loss
```

**Desde el Cliente B (Winery) hacia un cliente en Brewery** (si existiera):

```bash
ping -c 4 172.16.20.101
```

**Desde el Server A hacia ambas subredes:**

```bash
# Ping hacia Winery
ping -c 4 172.16.10.1

# Ping hacia Brewery
ping -c 4 172.16.20.1
```

### 2.3 Solución si el Ping no Responde

Si el ping no funciona, verifique estos puntos en orden:

```bash
# 1. Confirmar que IP forwarding está activo
cat /proc/sys/net/ipv4/ip_forward

# 2. Confirmar que las rutas existen en el cliente
ip route show

# 3. Confirmar que el firewall no bloquea el tráfico
sudo ufw status
sudo iptables -L FORWARD

# 4. Hacer ping desde el Server A hacia el cliente para aislar el problema
ping -c 4 172.16.10.101
```

---

## 3. Acceso al Servidor Web desde cualquier Subred

El taller pide que cualquier cliente, independientemente de su subred, pueda acceder al servidor web Apache tanto por IP como por el nombre `winery.local`, desde terminal y desde navegador.

### 3.1 Acceso por Dirección IP

Con el enrutamiento configurado en el paso 1, el acceso por IP ya debería funcionar. Verifique desde el Cliente B:

```bash
# Acceso por IP desde terminal
curl http://172.16.10.1/

# Debe retornar el JSON de la API o la página de Apache
```

Desde el navegador del Cliente B (si tiene entorno gráfico):

```
http://172.16.10.1/
```

### 3.2 Acceso por Nombre winery.local

Para que el nombre `winery.local` funcione desde cualquier subred, el DNS del Server A debe estar configurado para responder a consultas que lleguen por ambas interfaces.

**Verificar la configuración de Bind9:**

```bash
sudo nano /etc/bind/named.conf.options
```

Asegúrese de que Bind9 escucha en todas las interfaces y permite consultas desde ambas subredes:

```
options {
    directory "/var/cache/bind";

    // Escuchar en todas las interfaces
    listen-on { any; };

    // Permitir consultas desde ambas subredes
    allow-query { 
        localhost;
        172.16.10.0/24;
        172.16.20.0/24;
    };


    forwarders {
        8.8.8.8;
        8.8.4.4;
    };

    forward only;
    dnssec-validation no;
};
```

```bash
# Reiniciar Bind9 para aplicar cambios
sudo systemctl restart bind9

# Verificar que no hay errores
sudo named-checkconf
```

### 3.3 Configurar el DNS en los Clientes de Brewery

Los clientes en Brewery deben apuntar al Server A como su servidor DNS. Si el DHCP ya les asigna `172.16.20.1` como DNS, esto ya está cubierto. Verifique en el cliente:

```bash
# Ver el servidor DNS configurado
cat /etc/resolv.conf

# Debe mostrar:
# nameserver 172.16.20.1  (o 172.16.10.1)
```

Si no está configurado, agréguelo manualmente:

```bash
sudo nano /etc/systemd/resolved.conf
```

```ini
[Resolve]
DNS=172.16.10.1
Domains=winery.local brewery.local
```

```bash
sudo systemctl restart systemd-resolved
```

### 3.4 Prueba de Resolución DNS y Acceso Web

```bash
# Desde cualquier cliente, resolver el nombre
nslookup winery.local
ping -c 4 winery.local

# Acceder al servidor web por nombre desde terminal
curl http://winery.local/

# Verificar que responde igual que por IP
curl http://172.16.10.1/
```

Desde el navegador (si el cliente tiene entorno gráfico):

```
http://winery.local/
```

---

## 4. Configurar NAT para Acceso a Internet desde los Clientes

Actualmente los clientes pueden comunicarse con el Server A dentro de la red interna, pero no pueden salir a Internet. Para lograrlo, el Server A debe aplicar NAT al tráfico de los clientes antes de enviarlo hacia el anfitrión.

### 4.1 Confirmar que el Adaptador NAT está Activo en Server A

En VMware, confirme que el Adaptador de red del Server A está configurado como **NAT** y que tiene conectividad hacia el anfitrión:

```bash
# Desde Server A, verificar que tiene ruta hacia Internet
ping -c 4 8.8.8.8

# Si responde, el adaptador NAT hacia el anfitrión funciona correctamente
```

Si no responde, revise en VMware que el adaptador de red esté habilitado y configurado como NAT en **Virtual Machine Settings → Network Adapter → NAT**.

### 4.2 Configurar NAT con iptables en Server A

El Server A debe tomar el tráfico que viene de las subredes internas y enmascararlo con su propia IP antes de enviarlo hacia el exterior (interfaz `enp0s3`):

```bash
# Regla NAT: enmascarar el tráfico saliente por la interfaz NAT (enp0s3)
sudo iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE

# Permitir tráfico reenviado desde las subredes internas hacia afuera
sudo iptables -A FORWARD -i enp0s8 -o enp0s3 -j ACCEPT
sudo iptables -A FORWARD -i enp0s9 -o enp0s3 -j ACCEPT

# Permitir tráfico de respuesta (conexiones ya establecidas)
sudo iptables -A FORWARD -i enp0s3 -o enp0s8 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i enp0s3 -o enp0s9 -m state --state RELATED,ESTABLISHED -j ACCEPT
```

### 4.3 Guardar las Reglas de iptables

Para que las reglas persistan tras reinicios:

```bash
# Instalar iptables-persistent si no está instalado
sudo apt install -y iptables-persistent

# Guardar las reglas actuales
sudo netfilter-persistent save

# Verificar que se guardaron
sudo iptables -t nat -L -n -v
```

Debe ver la regla MASQUERADE en la cadena POSTROUTING.

### 4.4 Configurar el Gateway por Defecto en los Clientes

Los clientes deben saber que para salir a Internet deben pasar por el Server A. Verifique que el gateway por defecto está configurado correctamente:

```bash
# En el Cliente B, ver la ruta por defecto
ip route show

# Debe mostrar una línea similar a:
# default via 172.16.10.1 dev enp0s3
```

Si no aparece la ruta por defecto, agréguela:

```bash
sudo ip route add default via 172.16.10.1
```

Para que persista, en Netplan del Cliente B:

```yaml
network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: true
      gateway4: 172.16.10.1
      nameservers:
        addresses: [172.16.10.1]
```

```bash
sudo netplan apply
```

### 4.5 Verificar Acceso a Internet desde los Clientes

```bash
# Ping hacia un servidor público
ping -c 4 8.8.8.8

# Resolver un dominio externo (prueba DNS + Internet)
nslookup google.com

# Actualizar el software del cliente
sudo apt update

# Debe descargar la lista de paquetes desde Internet correctamente
```

---

## 5. Crear la Máquina Virtual C

El taller pide crear una tercera VM con recursos mínimos para consumir los servicios del Server A en paralelo con el Cliente B. Se recomienda una distro ligera como **Ubuntu Server** (sin entorno gráfico) o **Lubuntu**.

### 5.1 Crear la VM en VMware

1. Abra VMware y haga clic en **Create a New Virtual Machine**.
2. Seleccione **Custom (advanced)** para tener control total sobre los recursos, luego haga clic en **Next** hasta llegar a la configuración de hardware.
3. Configure los recursos mínimos:

| Parámetro | Valor recomendado |
|---|---|
| Nombre | Cliente C |
| Sistema Operativo | Linux / Ubuntu 64-bit |
| RAM | 512 MB (mínimo viable) |
| CPU | 1 núcleo |
| Disco | 8 GB (disco virtual) |

4. En la sección **Network Adapter**, seleccione **LAN Segment** y asigne el mismo segmento que usaron el Server A y el Cliente B (`Winery` o `Brewery`). Si aún no existe el segmento, créelo desde **Edit → Virtual Network Editor**.
5. Monte la ISO de la distro elegida en **CD/DVD → Use ISO image file** y complete la instalación.

> **Recomendación:** Use Ubuntu Server 22.04 LTS sin entorno gráfico. Es la opción más ligera del ecosistema Ubuntu y consume menos de 512 MB de RAM en reposo.

### 5.2 Instalación Mínima

Durante la instalación de Ubuntu Server, en la selección de software:

- **No seleccione** ningún paquete adicional.
- Solo marque **OpenSSH Server** si desea acceder por SSH desde el anfitrión.
- Deje todo lo demás desmarcado para mantener el sistema lo más liviano posible.

### 5.3 Verificar que el Cliente C Obtiene IP por DHCP

Una vez instalado e iniciado el Cliente C:

```bash
# Ver la IP asignada por el DHCP del Server A
ip addr show

# Debe mostrar una IP en el rango 172.16.10.100-200 (si está en Winery)
# o en 172.16.20.100-200 (si está en Brewery)
```

Si no obtuvo IP automáticamente:

```bash
sudo dhclient enp0s3
ip addr show
```

### 5.4 Instalar curl en el Cliente C

La instalación mínima puede no incluir curl. Instálelo para poder consumir la API:

```bash
# Actualizar repositorios (ya debe tener Internet gracias al NAT del paso 4)
sudo apt update

# Instalar curl
sudo apt install -y curl
```

### 5.5 Consumir los Servicios del Server A desde el Cliente C

```bash
# Verificar conectividad con el servidor
ping -c 4 172.16.10.1

# Resolver el nombre de dominio
nslookup winery.local

# Acceder a la API por IP
curl http://172.16.10.1/

# Acceder a la API por nombre
curl http://winery.local/

# Crear un producto mediante POST
curl -X POST http://winery.local/ \
     -H 'Content-Type: application/json' \
     -d '{"nombre":"Rose Verano","precio":12.00}'

# Actualizar software (prueba de acceso a Internet)
sudo apt update
```

---

## 6. Verificación Final y Pruebas

### 6.1 Lista de Verificación Completa

| #   | Verificación                               | Dónde ejecutar                                 |
| --- | ------------------------------------------ | ---------------------------------------------- |
| ☐   | IP forwarding activo en Server A           | `cat /proc/sys/net/ipv4/ip_forward` (Server A) |
| ☐   | Ping de Winery hacia Brewery               | `ping 172.16.20.1` (Cliente B)                 |
| ☐   | Ping de Brewery hacia Winery               | `ping 172.16.10.1` (Cliente C en Brewery)      |
| ☐   | Acceso a Apache por IP desde Cliente B     | `curl http://172.16.10.1/` (Cliente B)         |
| ☐   | Acceso a Apache por nombre desde Cliente B | `curl http://winery.local/` (Cliente B)        |
| ☐   | Acceso a Apache por IP desde Cliente C     | `curl http://172.16.10.1/` (Cliente C)         |
| ☐   | Acceso a Apache por nombre desde Cliente C | `curl http://winery.local/` (Cliente C)        |
| ☐   | Cliente B tiene acceso a Internet          | `ping 8.8.8.8` (Cliente B)                     |
| ☐   | Cliente C tiene acceso a Internet          | `ping 8.8.8.8` (Cliente C)                     |
| ☐   | Cliente B puede actualizar software        | `sudo apt update` (Cliente B)                  |
| ☐   | Cliente C puede actualizar software        | `sudo apt update` (Cliente C)                  |
| ☐   | Reglas NAT persistentes tras reinicio      | Reiniciar Server A y repetir pruebas           |

### 6.2 Diagrama Final del Sistema

```
Internet
    ↓
   ISP
    ↓
Equipo Anfitrión (gateway hacia ISP / VMware)
    ↓
Server A (VM A)
├── enp0s3  →  NAT hacia anfitrión (Internet)
├── enp0s8  →  172.16.10.1  (gateway Winery)
│               ↓
│           Cliente B  →  172.16.10.10x  (DHCP)
│           Cliente C  →  172.16.10.10x  (DHCP) *si está en Winery
│
└── enp0s9  →  172.16.20.1  (gateway Brewery)
                ↓
            Cliente C  →  172.16.20.10x  (DHCP) *si está en Brewery
```

### 6.3 Solución de Problemas Comunes

#### El ping entre subredes no funciona
- Confirme que IP forwarding está activo: `cat /proc/sys/net/ipv4/ip_forward` debe devolver `1`.
- Verifique las reglas de FORWARD en iptables: `sudo iptables -L FORWARD`.
- Confirme que el cliente tiene la ruta hacia la otra subred: `ip route show`.

#### Los clientes no tienen acceso a Internet
- Confirme que la regla MASQUERADE existe: `sudo iptables -t nat -L POSTROUTING`.
- Verifique que el Server A sí tiene acceso a Internet: `ping -c 4 8.8.8.8` desde Server A.
- Confirme que el cliente tiene como gateway al Server A: `ip route show | grep default`.

#### El nombre winery.local no resuelve desde Brewery
- Verifique que Bind9 permite consultas desde la subred Brewery en `named.conf.options`.
- Confirme que el cliente apunta al DNS correcto: `cat /etc/resolv.conf`.
- Pruebe la resolución directamente: `dig @172.16.10.1 winery.local`.

#### El Cliente C no obtiene IP por DHCP
- Confirme que el adaptador está en el **LAN Segment** correcto en VMware (**Virtual Machine Settings → Network Adapter → LAN Segment**).
- Verifique que el DHCP del Server A está activo: `sudo systemctl status isc-dhcp-server`.
- Solicite IP manualmente: `sudo dhclient enp0s3`.

---

> **Resultado esperado del Taller:** Al finalizar, los Clientes B y C deben poder comunicarse entre subredes por ping, acceder al servidor web Apache tanto por IP (`172.16.10.1`) como por nombre (`winery.local`) desde terminal y navegador, y tener acceso a Internet para actualizar su software — todo enrutado a través del Server A que actúa simultáneamente como router interno y gateway NAT hacia el exterior.

---

*Taller VI — Arquitectura de Computadoras I — Ciclo 01, 2026 — UCA*
