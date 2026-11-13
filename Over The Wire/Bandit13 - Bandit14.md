
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel se almacena en /etc/bandit_pass/bandit14 y solo puede ser leída por el usuario bandit14.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit13@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn"
3. Al entrar y listar los archivos en el servidor, se ve que solo existe una clave ssh privada, por lo que conociendo la localización de la ssh se procede a extraer la llave a un directorio propio con `scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .`
4. Se intenta conectar al nivel 14 con la llave obtenida.
5. Una vez conectado, se busca la contraseña en /etc/bandit_pass/bandit14

**Captura:**

![[Pasted image 20251113192110.png]]
![[Pasted image 20251113191943.png|center]]

**Explicación:**
El comando `scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .` se conecta al servidor en el puerto especificado, y se copia el archivo seleccionado en el directorio local.

**Resultado obtenido:**
Contraseña: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

**Dificultades o retos:**
Problemas con la obtención de archivos desde un servidor.

**Aprendizajes:**
Entendimiento de la copia de archivos desde un servidor.
