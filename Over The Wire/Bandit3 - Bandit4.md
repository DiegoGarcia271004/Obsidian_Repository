
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel almacenada en un archivo oculto en el directorio inhere.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit3@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx"
3. Se utiliza el comando `la inhere` para visualizar todos los archivos incluyendo archivos ocultos
4. Se ejecuta `cat inhere/...Hiding-From-You` para ver el interior del archivo dentro del directorio

**Captura:**

![[Pasted image 20251113165423.png|center]]

**Explicación:**
El comando `la inhere` permite visualizar la lista de todos los archivos dentro del directorio inhere, incluyendo también aquellos archivos ocultos.

**Resultado obtenido:**
Contraseña: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

**Dificultades o retos:**
N/A

**Aprendizajes:**
Uso del comando `la` para ver archivos ocultos en un directorio

