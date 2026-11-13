
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel almacenada en un archivo llamado --spaces in this filename--  ubicado en el directorio de inicio.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit2@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "263JGJPfgU6LtdEvgfWU1XP5yac29mFx"
3. Se utiliza el comando `ls` para visualizar todos los archivos
4. Se ejecuta `cat "./--spaces in this filename--"` para ver el interior del archivo

**Captura:**

![[Pasted image 20251113164614.png|center]]

**Explicación:**
El comando `cat cat "./--spaces in this filename--"` permite visualizar el texto en el interior del archivo que tiene espacios en su nombre

**Resultado obtenido:**
Contraseña: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

**Dificultades o retos:**
N/A

**Aprendizajes:**
Uso del comando `cat` para archivos con espacios en su nombre

