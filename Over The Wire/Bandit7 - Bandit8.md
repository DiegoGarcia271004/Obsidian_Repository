
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña almacenada en el archivo **data.txt** a la par de la palabra millionth.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit7@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj"
3. Se utiliza el comando `cat data.txt | grep millionth` para filtrar el archivo data.txt y filtrarlos solamente por la palabra millionth

**Captura:**

![[Pasted image 20251113174350.png]]

**Explicación:**
El comando `cat data.txt | grep millionth` imprime el interior del archivo data.txt filtrando las líneas con la palabra millionth.

**Resultado obtenido:**
Contraseña: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

**Dificultades o retos:**
N/A

**Aprendizajes:**
Entendimiento del filtrado de salidas.
