
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña almacenada en el archivo **data.txt** en la línea que solo se repite una vez.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit8@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "4CKMh1JI91bUIZZPXDqGanal4xvAg0JM"
3. Se utiliza el comando `strings data.txt | grep ===` para filtrar el archivo data.txt.

**Captura:**

![[Pasted image 20251113175545.png|center]]

**Explicación:**
El comando `strings data.txt | grep ===` imprime todas las cadenas de texto dentro del archivo data.txt, luego se le pasa como parámetro a `grep` que filtra todas las salidas.

**Resultado obtenido:**
Contraseña: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

**Dificultades o retos:**
N/A

**Aprendizajes:**
Entendimiento del filtrado de salidas.
