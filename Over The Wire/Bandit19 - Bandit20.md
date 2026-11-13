
**Objetivo:**
Para acceder al siguiente nivel, se debe utilizar el binario setuid en el directorio de inicio para acceder a la contraseña en /etc/bandit_pass.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit19@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8"
3. Existe solamente un setuid en el directorio, con este podemos hacer acciones del usuario bandit20 aún sin serlo, por lo que ejecutamos el setuid y navegamos en el servidor buscando la contraseña en el lugar establecido.

**Captura:**

![[Pasted image 20251113213501.png]]

**Explicación:**
El setuid nos permite ejecutar comandos como si fuéramos otro usuario, por lo que podemos acceder a directorios que con nuestro usuario principal no podríamos.

**Resultado obtenido:**
Contraseña: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO

**Dificultades o retos:**
N/A

**Aprendizajes:**
Entendimiento de los setuid.
