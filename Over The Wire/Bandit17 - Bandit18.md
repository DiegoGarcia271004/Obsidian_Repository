
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel que se obtiene encontrando la única línea entre passwords.old y passwords.new que cambia.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh -i sshbandit17.private bandit17@bandit.labs.overthewire.org -p 2220`
2. Se usa el comando `diff passwords.old passwords.new` para buscar cuál es la línea que ha cambiado
3. Ya que escribimos passwords.new como segundo parámetro, la segunda salida será la contraseña.

**Captura:**

![[Pasted image 20251113204819.png]]


**Explicación:**
El comando `diff passwords.old passwords.new` busca los datos que han cambiado entre los dos archivos.

**Resultado obtenido:**
Contraseña: x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO

**Dificultades o retos:**
N/A

**Aprendizajes:**
Entendimiento de uso de `diff`

