
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel que se encuentra en algún archivo que posee todas las siguientes propiedades
- Legible para humanos
- Tamaño de 1033 bytes
- No es ejecutable

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit5@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw"
3. Se utiliza el comando `cd inhere` para navegar a la carpeta
4. Se ejecuta `find . -type f -size 1033c ! -executable -print0 | xargs -0 file | grep text` para ver solamente los archivos que sean de tipo texto legible para humanos, con tamaño de 1033 bytes y que no sean ejecutables.
5. Se ejecuta `cat maybehere07/.file2` para ver el interior del archivo dentro del directorio maybehere07.

**Captura:**

![[Pasted image 20251113171928.png]]

**Explicación:**
El comando `find . -type f -size 1033c ! -executable -print0 | xargs -0 file | grep text` hace distintas cosas a la vez:
- `find . -type f -size 1033c ! -executable -print0`: muestra todos los archivos del directorio actual que cumplan: tener un tamaño de 1033 bytes y no sean ejecutables. Separados por un carácter nulo.
- `xargs -0 file`: Pasa todos los tipos de datos de cada archivo al comando file.
- `grep text` Filtra toda la salida para solamente extraer los elementos que sean text.

**Resultado obtenido:**
Contraseña: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

**Dificultades o retos:**
N/A

**Aprendizajes:**
Entendimiento del comando `find`, `xargs` y `grep`
