
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña almacenada en el archivo **data.txt** en la línea que solo se repite una vez.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit8@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc"
3. Se utiliza el comando `sort data.txt | uniq -u` para filtrar el archivo data.txt.

**Captura:**

![[Pasted image 20251113175039.png|center]]

**Explicación:**
El comando `sort data.txt | uniq -u` primero ordena las cadenas de texto dentro de data.txt y coloca aquellas que se repitan de forma seguida, luego se le pasa esta salida como parámetro al comando `uniq -u` que devuelve solamente las líneas que no se repiten.

**Resultado obtenido:**
Contraseña: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

**Dificultades o retos:**
N/A

**Aprendizajes:**
Entendimiento del filtrado de salidas.
