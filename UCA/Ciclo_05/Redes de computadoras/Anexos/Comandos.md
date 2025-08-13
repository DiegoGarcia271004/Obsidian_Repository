```Powershell
configure terminal

interface <nombre de la interfaz> <puerto de conexión>

ip adress <ip> <máscara>

no shutdown

exit

exit

wr

ip route <ruta destino> <máscara> <ip de paso>

show ip route static 
show running-config | include ip route 
show ip interface brief 

---

router rip

version 2

no auto-summary

network <cada una de las ip de red a las que está conectada el router>

passive-interface <nombre de la interfaz> <el valor de la interfaz>

show ip protocol 

show ip route rop 

---

router ospf <id> 

Router-id <x.x.x.x> 1.1.1.1 2.2.2.2 

Network <ip> <wildcar> area <>

show ip ospf interface <>

show ip ospf neighbor

netstat -ano | findstr :<puerto donde da el error>
taskkill /PID <nombre del proceso> /F
```
