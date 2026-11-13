
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel que se obtiene en el interior de un archivo readme.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit18@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO"
3. El servidor inmediatamente cierra la conexión.
4. Si bien no es posible ingresar completamente al servidor, si es posible ejecutar comandos antes que nuestra conexión sea terminada.
5. Primeramente haremos nuestra conexión junto al comando `ls` para poder asegurarnos que el archivo se encuentre en el directorio inicial `ssh bandit18@bandit.labs.overthewire.org -p 2220 ls`
6. Luego de confirmar la existencia del archivo, procederemos a leerlo con: `ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme`

**Captura:**

![[Pasted image 20251113212709.png]]

**Explicación:**
Si bien el bashrc del servidor ha sido alterado, aún es posible acceder momentáneamente y ejecutar comandos, que nos permiten conseguir la contraseña. 

**Resultado obtenido:**
Contraseña: cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8

**Dificultades o retos:**
Investigación de exploración de puertos.

**Aprendizajes:**
Entendimiento de exploración de puertos
