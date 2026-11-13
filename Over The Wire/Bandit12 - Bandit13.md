
**Objetivo:**
El objetivo de este nivel es encontrar la contraseña para el siguiente nivel que se encuentra almacenada en el archivo data.txt, que es un hexdump de un archivo que ha sido comprimido repetidas veces.

**Herramientas:**
Shell

**Pasos:**
1. Se ejecuta `ssh bandit12@bandit.labs.overthewire.org -p 2220`
2. Se ingresa la contraseña "7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4"
3. Se crea un directorio temporal con `mktemp -d`
4. Se navega al directorio dado: `cd /tmp/tmp.EowuUC8vIw`
5. Se copia el archivo data.txt al directorio actual `cp ~/data.txt .`
6. Se sabe que data.txt es un hexdump, por lo que se hará un revert del hexdump y se guardará en un archivo llamado text con `xxd -r > text`
7. Se verificará que tipo de archivo es text con `file text`
8. Al ser un archivo comprimido con gzip, se descomprimirá con `mv text text.gz && gzip -d text.gz`
9. Se verifica que tipo de archivo es.
10. Al ser un archivo comprimido con bzip2, se descomprimirá con `mv text text.bz2 && bzip2 -d text.bz2`
11. Se vuelve a verificar el tipo de dato
12. Al ser un archivo comprimido con gzip, se descomprimirá con `mv text text.gz && gzip -d text.gz`
13. Se verifica el tipo de dato
14. Al ser un archivo tar, se utiliza tar para extraer el archivo original `tar -xf text`
15. Esto devuelve un archivo llamado data5.bin, se verifica el tipo de dato de este nuevo archivo.
16. Al ser un archivo tar, se utiliza tar para extraer el archivo original `tar -xf data5.bin`
17. Esto devuelve un archivo llamado data6.bin, se verifica el tipo de dato de este archivo.
18. Al ser un archivo comprimido con bzip2, se descomprimirá con `mv data6.bin data6.bin.bz2 && bzip2 -d data6.bin.bz2`
19. Se verifica el tipo de dato.
20. Al ser un archivo tar, se utiliza tar para extraer el archivo original `tar -xf data6.bin`
21. esto devuelve un archivo llamado data8.bin, se verifica el tipo de dato.
22. Al ser un archivo comprimido con gzip, se descomprimirá con `mv data8.bin data8.bin.gz && gzip -d data8.bin.gz`
23. Se verifica el tipo de dato.
24. Al ser un archivo de texto, usamos `cat data8.bin` para visualizar el interior del archivo.

**Captura:**

![[Pasted image 20251113184853.png]]
![[Pasted image 20251113185138.png]]
**Explicación:**
El comando con el comando `file` podemos visualizar el tipo de archivo que se tiene, dependiendo de este se descomprimirá con `gzip, bzip2 o tar` 

**Resultado obtenido:**
Contraseña: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

**Dificultades o retos:**
N/A

**Aprendizajes:**
Entendimiento del descifrado y descompresión de archivos.
