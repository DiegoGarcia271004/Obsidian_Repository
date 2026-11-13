## Origen

Oficialmente se presento en 1997, presentado como parte de la competencia para seleccionar el nuevo estándar de cifrado AES, organizada por el NIST.
Creado por un equipo liderado por Bruce Schneier, junto con John Kelsey y otros más. Como dato, Bruce ya era conocido por ser el creador de [[Blowfish]].

Twofish buscaba resolver las necesidad de proteger datos seguros ante ataques de fuerza bruta, por la necesidad de un estándar abierto y flexible, y el avance del hardware (ya que conforme mejoraba, mejoraban también los ataques de fuerza bruta).

## En qué consiste?

Es un cifrado de clave simétrica por bloques, es decir que toma los datos en bloques de 128 bits y utiliza una red Feistel con 16 rondas, donde los bloques de datos se van mezclando.

Utiliza S-boxes dependientes de la clave, que son tablas de sustitución que cambian dependiendo de la clave utilizada.
Además de la utilización de una matríz MDS que provee una seguridad de caos determinista.

## En qué se usa?

- En cifrado de discos y archivos, en herramientas como trueCrypt
- Comunicación segura
- En el ámbito de la investigación.

Twofish es derivado del algoritmo [[Blowfish]] que al contrario de este, que utiliza bloques de 64 bits, este utiliza 128 bits.

| Diferencia      | Blowfish    | TwoFish  |
| --------------- | ----------- | -------- |
| Bloques         | 64 bits     | 128 bits |
| Tamaño de clave | 64-448 bits |          |
## Curiosidades
- Uno de los 5 finalistas de la AES
- Cifrado sin patentes, no hay derechos de autor sobre el código (open source).
- No está comprometido todavía.