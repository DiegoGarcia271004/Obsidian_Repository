
**Objetivo:**
Hay un binario setuid en el directorio de inicio que hace lo siguiente: establece una conexión con localhost en el puerto que se especifica como argumento de la línea de comandos. A continuación, lee una línea de texto de la conexión y la compara con la contraseña del nivel anterior (bandit20). Si la contraseña es correcta, transmitirá la contraseña del siguiente nivel (bandit21).

**Herramientas:**
Shell, netcat

**Pasos:**
1. Se ejecuta `ssh bandit20@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO"
3. Usando netcat podemos crear una conexión en modo servidor para que escuche, así que ejecutaremos: `echo -n '0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO' | nc -l -p 1234 &`
4. Ejecutar el setuid en el puerto que definimos significa que conectara a nuestro puerto netcat recibiendo la contraseña a través de `echo` y devolverá la siguiente contraseña
**Captura:**

![[Pasted image 20251113214142.png]]

**Explicación:**
Con netcat podemos crear un servidor en localhost con la bandera `-l` que significa que esta escuchando. Para especificar el puerto se usa `-p`, para crear un servidor que envíe un mensaje y luego se desconecte usamos el pipe `|` y `echo` para mandar el mensaje.

**Resultado obtenido:**
Contraseña: EeoULMCra2q0dSkYj561DX7s1CpBuOBt

**Dificultades o retos:**
N/A

**Aprendizajes:**
Entendimiento de los setuid.
