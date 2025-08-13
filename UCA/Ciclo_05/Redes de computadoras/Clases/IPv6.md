---
tags:
  - RedesDeComputadoras
---
Diseñado por la IETF, ofrece un espacio de 128 bits, hasta $2^{128}$ o $16^{32}$ IPs

AF01:DB8:AABB:CE0::
FF00:1234:FFFF::ii

**GNS3**
```bash
ipv6 unicast-routing #Habilitar el ipv6

interface <igual que en el resto>

ipv6 address
```

```bash
# EUI64
mac-address <>

```

```bash
# otra forma
ipv6 enable
ipv6 address autoconfig
No shutdown
```

```bash
#entrar a la interfaz
ipv6 enable

```

## IPv4 a IPv6

**Conversión directa:**

10111101.00111100.00100100.00000010
1011 | 1101 . 0011 | 1100 . 0010 | 0100 . 0000 | 0010
::FFFF:BD3C:2402

## MAC a IPv6

1. FFFE al centro
2. 7° bit (pasar a binario el primer par de valores y cambiar el bit #7)
3. FE80

MAC 0A-00-27-00-00-12
0A:00:27:00:00:12

0A:00:27:FFFE:00:00:12
0A = 000001010 $\to$ 0000 0100 $\to$ 08

08:00:27:FFFE:00:00:12
0800:27FF:FE00:0012

FE80:0:0:0:0800:27FF:FE00:0012
FE80::800:27FF:FE00:12

MAC BC-00-27-18-00-12
BC:00:27:18:00:12
BC:00:27:FFFE:18:00:12
BC=1011 1100 $\to$ 1011 1110 $\to$ BE
BE00:27FF:FE18:0012
FE80:0:0:0:BE00:27FF:FE18:0012
FE80::BE00:27FF:FE18:12

Prefix 2002:00B8:ABCD:5698
MAC 1A-00-27-00-00-12
1A:00:27:18:00:12
1A:00:27:FFFE:00:00:12
1A=0001 1010 $\to$ 0001 1000  $\to$ 18
1800:27FF:FE00:0012
2002:00B8:ABCD:5698:1800:27FF:FE00:0012/64


## Rutas estáticas

```bash
ipv6 route <ruta final> 
```

al trabajar con las rutas estáticas, todas las conexiones deberán de asignárseles valor de ip global. Es decir que si se hace una estática, se debe trabajar como si fuera una IPv4