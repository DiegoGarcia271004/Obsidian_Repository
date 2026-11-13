
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel que se encuentra en un archivo llamado **readme** ubicado en el directorio de inicio. Se utilizará esta contraseña para iniciar sesión en bandit1 mediante SSH.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit0@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "bandit0"
3. Se utiliza el comando `ls` para visualizar todos los archivos
4. Se ejecuta `cat readme` para ver el interior del archivo

**Captura:**

![[Pasted image 20251113163610.png]]

**Explicación:**
El comando `cat readme` permite visualizar el texto en el interior del archivo **readme**

**Resultado obtenido:**
Contraseña: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

**Dificultades o retos:**
N/A

**Aprendizajes:**
Uso del comando `cat`

