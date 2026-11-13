
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel que se encuentra almacenada en el archivo data.txt, donde todas las letras minúsculas (a-z) y mayúsculas (A-Z) se han rotado 13 posiciones.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit11@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr"
3. Se utiliza el comando `cat data.txt | tr 'a-z' 'n-za-m' | tr 'A-Z' 'N-ZA-M'` para rotar las letras del archivo.

**Captura:**

![[Pasted image 20251113181117.png|center]]

**Explicación:**
El comando `cat data.txt | tr 'a-z' 'n-za-m' | tr 'A-Z' 'N-ZA-M'` rota tanto las letras minúsculas como mayúsculas 13 posiciones.

**Resultado obtenido:**
Contraseña: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

**Dificultades o retos:**
Problemas con la sintaxis del comando.

**Aprendizajes:**
Entendimiento del descifrado de datos.
