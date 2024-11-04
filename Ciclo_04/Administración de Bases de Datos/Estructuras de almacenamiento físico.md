---
tags:
  - Abd
---
Al trabajar con almacenamiento en Oracle, es necesario conocer como se comporta este. A continuación empezaremos enlistando los distintos componentes de almacenamiento que posee.

## Bloques

Los bloques son la unidad más básica de almacenamiento en Oracle, cada vez que se almacenan datos en la base, se hacen en forma de bloques.
Los bloques contienen filas de una tabla o índices, cada bloque puede almacenar una o más filas, dependiendo del tamaño del bloque y de la fila.
El tamaño de los bloques es configurable. Sin embargo, se suelen encontrar en tamaños de: 2KB, 4KB, 8KB, 16KB o 32KB.

Los bloques están conformados por tres espacios:
1. **Cabecera:** En este espacio se encuentran los metadatos del bloque tales como la ubicación, el tipo y otra información de administración.
2. **Datos:**  Es la zona principal del bloque en donde se almacenan los datos de las filas de la base de datos, se encuentran las columnas y la información de las tablas que ocupan el bloque.
3. **Espacio Vacío:** Es un espacio que se pone a disposición en caso de ser necesitado en un futuro para almacenar nuevas filas, columnas o expandir filas existentes.

## Extensiones

Las extensiones son un conjunto de [[Estructuras de almacenamiento físico#Bloques|bloques]] de bases de datos, las extensiones permiten que un objeto crezca en tamaño de manera controlada.
Oracle gestiona extensiones automáticamente, el tamaño de estas puede ser uniforme (todas las extensiones del segmento tienen el mismo tamaño) o variable (El tamaño de las extensiones puede ir variando progresivamente).

## Segmentos

Los segmentos son un conjunto de [[Estructuras de almacenamiento físico#Extensiones|extensiones]] las cuales se asignan a una estructura lógica en la base de datos como una tabla, un índice, una tabla temporal, etc. Cada objeto de la base de datos que almacena datos tiene asociado al menos un segmento.
Los segmentos son los que agrupan y organizan las extensiones, los segmentos pueden estar conformados por múltiples extensiones y cada extensión esta compuesta por múltiples bloques.

### Administración de extensiones y segmentos

#### AUTOALLOCATE
```SQL
CREATE SMALLFILE TABLESPACE TS_EMPLEADOS
DATAFILE 'C:\Oracle\oradata\ORCL\general_data\DF_EMPLEADO.DBF'
SIZE 10M
EXTENT MANAGEMENT LOCAL AUTOALLOCATE; 
-- Opcion por defecto
-- posibles extensiones: 64K, 1M, 8M, 64M
-- Alternativa: crear TB con tamaño fijo: EXTENT LOCAL UNIFORM SIZE xM

CREATE TABLE EMP__ (
    id INT PRIMARY KEY,
    nombre VARCHAR2(50)
)
TABLESPACE TS_EMPLEADOS
STORAGE (INITIAL 100K);
-- Para elegir el tamaño de la extensión se elige la de menor valor entre dos posibles opciones
-- Para esta tabla se necesitaron 2 extensiones de 64K. 2*64k=128K

SELECT * FROM DBA_SEGMENTS WHERE SEGMENT_NAME = 'EMP__';
-- Se han creado 2 extensiones
-- Se han creado 16 bloques porque cada bloque tiene 8K, 8K*2extensiones=16bloques
SELECT * FROM DBA_EXTENTS WHERE SEGMENT_NAME = 'EMP__';

DROP TABLE EMP__;
DROP TABLESPACE TS_EMPLEADOS
   INCLUDING CONTENTS AND DATAFILES;
```


#### UNIFORM
```SQL
CREATE SMALLFILE TABLESPACE TS_EMPLEADOS
DATAFILE 'C:\Oracle\oradata\ORCL\general_data\DF_EMPLEADO.DBF'
SIZE 10M
EXTENT MANAGEMENT LOCAL UNIFORM SIZE 1M; 

CREATE TABLE EMP__ (
    id INT PRIMARY KEY,
    nombre VARCHAR2(50)
)
TABLESPACE TS_EMPLEADOS
STORAGE (INITIAL 100K);

SELECT * FROM DBA_SEGMENTS WHERE SEGMENT_NAME = 'EMP__';
SELECT * FROM DBA_EXTENTS WHERE SEGMENT_NAME = 'EMP__';

DROP TABLE EMP__;
DROP TABLESPACE TS_EMPLEADOS
   INCLUDING CONTENTS AND DATAFILES;
```

