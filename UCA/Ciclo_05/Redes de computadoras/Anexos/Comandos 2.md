```powershell
# Estática
# Routers
ipv6 unicast-routing
<entrar a la interfaz>
ipv6 address <ip>/64
no shutdown

# Computadoras 
ip auto

# Realizar el enrutamiento
ipv6 route <ip final> <ip de salto> <distancia administrativa (métrica)>

show ipv6 route static
show running-config | include ^ipv6 route

# RIP

# Routers
ipv6 unicast-routing
ipv6 router rip RIPNG # creo que es opcional
<ingresar a la interfaz>
ipv6 address <ip o autoconfig, pero el autoconfig a la otra ruta debe tener su ip antes>
ipv6 rip RIPNG enable
no shutdown

show ipv6 route rip


# OSPF

# Routers
ipv6 unicast-routing
ipv6 router ospf 1
router-id <x.x.x.x> # Sea x el num del router
<entrar a la interfaz>
ipv6 ospf 1 area 0
```
