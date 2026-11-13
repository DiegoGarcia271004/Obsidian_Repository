## Origen

Publicado por el NIST (National Institute of Standards and Technology) el 5 de agosto de 2015, se baso en que el algoritmo SHA-1 era muy atacado, por lo que saco el SHA-2. Sin embargo, ya que el NIST quería tener un respaldo, entonces publicó un concurso en donde participaron 51 grupos donde SHA-3 fue el ganador.

Creado por un equipo de criptógrafos belgas guiado por Guido Bertoni.

## En qué consiste?

SHA-3 utiliza la construcción esponja, que es un proceso que se divide en 2 faces:
1. **Absorción:** Los datos se parten en diversos bloques para formar un bloque tridimensional, cada parte de la matriz genera un código con un máximo de 24 permutaciones.
2. **Extracción:** Se "exprime" el estado para generar el hash.
Ofrece múltiples variabtes:
- **Fijas**: Sha3-224, SHA3-256, SHA3-384, SHA3-512.
- **Extensibles:** SHAKE128, SHAKE256 (Hashs de longitud variable)

## Ventajas
- Inmune al algoritmo de Shor
- Mitiga Grover con longitudes >256 bits (SHA3-512)
- Resistente a colisiones, preimagen y segunda preimagen
- Diseño Robustecido
- Sin vulnerabilidades prácticas conocidas

## Usos
- Verificación de integridad de datos
- Almacenamiento seguro de contraseñas
- Generación de identificadores únicos
- Aplicaciones de alta seguridad como en blockchain

