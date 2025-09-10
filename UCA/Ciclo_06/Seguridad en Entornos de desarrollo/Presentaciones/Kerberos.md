---
tags:
  - SED
---
Es un protocolo de autenticación que evita enviar la contraseña por la red. En su lugar un KDC entrega tickets cifrados que los servidores validan, asegurando un acceso confiable a los servicios.

Creado por **Steve Miller y Clifford Neuman** en **1988**.

Kerberos es basado en el protocolo simétrico Needham Schroeder, diseñado para generar claves de sesión entre dos equipos.
Surge como una mejora ante los protocolos inseguros.
El problema era que telnet mandaba las contraseñas de los usuarios en texto plano, lo que facilitaba el robo de información.

Actualmente Kerberos es un protocolo de autenticación robusto, integrado en Active Directory desde windows 2000, centralizando la autenticación y autorización de datos.

## Métodos de encriptación

Jerberos utiliza algoritmos de encriptación seguros, como lo serían AES-128 o AES-256

Las "tres cabezas" del protocolo
- Servidor de autenticación
- Servidor de entrega de tickets
- Servidor de auditoría

