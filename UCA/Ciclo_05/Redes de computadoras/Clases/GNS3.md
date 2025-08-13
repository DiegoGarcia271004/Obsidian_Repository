---
tags:
  - RedesDeComputadoras
---
Comandos:
```Powershell
configure terminal

interface <nombre de la interfaz> <puerto de conexión>

ip adress <ip> <máscara>

no shutdown

exit

exit

wr
```

Primeramente, se abre la consola de uno de los routers.
1. Se abre la terminal de configuración con `configure terminal`.
2. Entramos a la configuración de interfaz `interface <nombre de la interfaz> <puerto de conexión>`
3. Se le agrega una ip `ip adress <ip> <máscara>` 
4. Se le agrega `no shutdown`
5. Salimos de la configuración `exit`
6. Buildeamos `wr`


```bash
show ip route static #Muestra las conexiones existentes del router (activas)
show running-config | include ip route #Muestra todas las conexiones existentes, aún las inactivas

show ip interface brief #Muestra la configuración de las interfaces de los routers
```

---

## Enrutamiento dinámico

- El administrador se encarga menos del mantenimiento de la configuración al momento de agregar y quitar redes.
- Los routers se encargan de todo

**Comandos**:

```bash
router rip

version 2

no auto-summary

network <cada una de las ip de red a las que está conectada el router>

passive-interface <nombre de la interfaz> <el valor de la interfaz> #solo a las computadoras

show ip protocol #permite ver la configuración de protocolo

show ip route rop #muestra las conexiones a los demás dispositivos
```

0-126: A

128-191: B

192-223: C


### Áreas de enrutamiento 

```bash
router ospf <id> #mismo valor a todos los routers

Router-id <x.x.x.x> 1.1.1.1 2.2.2.2 #Sea x el número de cada router

Network <ip> <wildcar> area <>

show ip ospf interface <>

show ip ospf neighbor
```


### Comandos especiales

Usualmente al abrir un archivo puede que hayan quedado procesos sin terminar y evite que el proyecto se abra con normalidad, para esto identificaremos cuál es el proceso sin terminar con:
```bash
 netstat -ano | findstr :<puerto donde da el error>
```
Ya que nos devuelve el nombre del proceso que impide la carga del archivo, lo eliminaremos:
```bash
taskkill /PID <nombre del proceso> /F
```

