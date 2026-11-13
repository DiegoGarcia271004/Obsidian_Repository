
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel que se encuentra en el único archivo legible por humanos del directorio inhere.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit4@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ"
3. Se utiliza el comando `cd inhere` para navegar a la carpeta
4. Se utiliza `ls` para visualizar todos los archivos del directorio
5. Se ejecuta `find . -type f -print0 | xargs -0 file | grep text` para ver solamente los archivos que sean de tipo texto
6. Se ejecuta `cat ./-file07` para ver el interior del archivo

**Captura:**

![[Pasted image 20251113171439.png]]

**Explicación:**
El comando `find . -type f -print0 | xargs -0 file | grep text` hace distintas cosas a la vez:
- `find . -type f -print0`: muestra todos los archivos del directorio actual separados por un carácter nulo.
- `xargs -0 file`: Pasa todos los tipos de datos de cada archivo al comando file.
- `grep text` Filtra toda la salida para solamente extraer los elementos que sean text.

**Resultado obtenido:**
Contraseña: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

**Dificultades o retos:**
Entender el uso de `find` con sus banderas, entender la aplicación de `xargs` y filtrar salidas con `grep`.

**Aprendizajes:**
Entendimiento del comando `find`, `xargs` y `grep`
