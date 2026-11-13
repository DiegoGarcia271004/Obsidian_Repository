
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel almacenada en un archivo llamado "-", ubicado en el directorio de inicio.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit1@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If"
3. Se utiliza el comando `ls` para visualizar todos los archivos
4. Se ejecuta `cat ./-` para ver el interior del archivo

**Captura:**

![[Pasted image 20251113164216.png|center]]

**Explicación:**
El comando `cat ./-` permite visualizar el texto en el interior del archivo **-**

**Resultado obtenido:**
Contraseña: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

**Dificultades o retos:**
N/A

**Aprendizajes:**
Uso del comando `cat` para archivos con nombres especiales

