
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña almacenada en el archivo **data.txt** que contiene datos codificados con base64.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit10@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey"
3. Se utiliza el comando `base64 -d data.txt` para descifrar el archivo data.txt.

**Captura:**

![[Pasted image 20251113180021.png|center]]

**Explicación:**
El comando `base64 -d data.txt` muestra el resultado de descifrar el archivo data.txt.

**Resultado obtenido:**
Contraseña: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

**Dificultades o retos:**
N/A

**Aprendizajes:**
Entendimiento del descifrado de datos.
