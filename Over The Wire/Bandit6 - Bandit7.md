
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel que se encuentra en algún lugar del servidor que posee todas las siguientes propiedades
- Propiedad del usuario bandit7
- Propiedad del grupo bandit6
- Tamaño de 33 bytes

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit6@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "HWasnPhtq9AVKe0dmk45nxy20cvUa6EG"
3. Se utiliza el comando `cd inhere` para navegar a la carpeta
4. Se ejecuta `find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null` para buscar los archivos que pertenezcan al usuario bandit7, que sean del grupo bandit6 y que sean de 33 bytes de tamaño.
5. Se ejecuta `cat /var/lib/dpkg/info/bandit7.password` para ver el interior del archivo.

**Captura:**

![[Pasted image 20251113173252.png]]

**Explicación:**
El comando `find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null` hace distintas cosas a la vez:
- `find / -type f -user bandit7 -group bandit6 -size 33c:` Muestra todos los archivos que pertenezcan a bandit7, que sean del grupo bandit6 se tamaño 33 bytes.
- `2>/dev/null`: Al ejecutar el comando anterior lanzará muchos mensajes de error por falta de permisos, por lo que al agregarle esta parte, mandará todos esos mensajes de error a un archivo nulo (los borrará) y solo dejará los archivos que nos interesan.

**Resultado obtenido:**
Contraseña: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

**Dificultades o retos:**
Entender como lidiar con los mensajes de error

**Aprendizajes:**
Entendimiento del control de errores.
