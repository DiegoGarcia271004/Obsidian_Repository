
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel que se consigue al subir la contraseña del nivel actual al localhost en el puerto 30000.

**Herramientas:**
Shell

**Pasos:**
1. Actualmente ya estamos dentro del perfil de bandit14
2. Para subir cosas al localhost se usa `nc`
3. Usamos `nc locahost 30000` y colocamos la contraseña del nivel actual, es decir: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
**Captura:**

![[Pasted image 20251113192649.png|center]]

**Explicación:**
El comando `nc` permite conectarse a conexiones TCP y UDP, y procede a escuchar, por lo que al subirle la contraseña escucha la respuesta del puerto.

**Resultado obtenido:**
Contraseña: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

**Dificultades o retos:**
Problemas con el uso del comando `nc`.

**Aprendizajes:**
Entendimiento de escucha de puertos.
