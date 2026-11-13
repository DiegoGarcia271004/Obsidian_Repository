Nace de la familia de algoritmos SHA. Debido a que SHA-0 tenia un problema de seguridad SHA-1 sale en 1995.
Fue desarrollado por la NSA (National Security Agency)

Consiste en recibir una entrada $x$ de tamaño arbitrario, retornando un valor hash $h(x)$ de 160 bits (20 bytes)

## Etapas
### Preprocesamiento
Primeramente el mensaje $x$ se rellena hasta alcanzar un tamaño que es múltiplo de 512 utilizando la función módulo.
Antes de 

- Aplicaciones en TSL/SSL, PGP, SSH, IPsec, certificados y firmas digitales.
- Es derivado de MD4
- Posee debilidades estructurales en colisión desde 2005.

## Predecesor
SHA-0 Desarrollado en 1933, siendo el primero de la familia de los SHA. Pero posee una debilidad cirptográfica que hacía más fácil encontrar colisiones. Para arreglar el problema, NSA y NIST modificaron esta versión para sacar SHA-1

- Los que habría tomado miles de años a una sola computadora para romper SHA-1, los investigadores lo consiguieron en meses usando clusters.
- Git usaba SHA-1 para identificar cada commit, lo que nos permite detectar cambios en el historial.
- El proyecto SHAttered fue la primera colisión real de SHA-1. Fue realizado usando archivos PDF.

```bash
sudo apt update
sudo apt install wget
wget "file1"
wget "file2"
sha1sum shattered-1.pdf
sha1sum shattered-2.pdf
```
