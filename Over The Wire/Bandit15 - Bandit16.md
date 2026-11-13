
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel que se obtiene al subir la contraseña del nivel actual al puerto 30001 en localhost usando encriptación SSL/TLS.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit15@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo"
3. Se usa el comando `openssl s_client -connect localhost:30001` y se ingresa la contraseña.

**Captura:**

![[Pasted image 20251113193421.png]]
![[Pasted image 20251113193431.png]]

**Explicación:**
El comando `openssl s_client -connect localhost:30001` implementa un simple client que se conecta al localhost:30001 usando SSL/TLS

**Resultado obtenido:**
Contraseña: kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

**Dificultades o retos:**
Investigación de conexiones SSL/TLS.

**Aprendizajes:**
Entendimiento de las conexiones con protocolos SSL/TLS.
