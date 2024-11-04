---
tags:
  - "#Abd"
---
Un **tablespace** es una unidad lógica de almacenamiento la cual agrupa uno o más datafiles, los cuales contienen los datos de las tablas, índices y otros objetos de la base de datos.
Enfatizando más en los datafiles, estos son un archivo físico que almacena los datos de las tablas de la base de datos cada tablespace está relacionado **con uno o más datafiles.**

## Tipos de tablespaces

1. **SYSTEM y SYSAUX:** Son tablespaces que contienen los objetos y los datos internos necesarios para la operación de la base de datos. Entre los datos que pueden almacenar, están los diccionarios de datos y componentes del sistema.
2. **Tablespaces de usuario:** Son aquellos que se crean para almacenar la información de los usuarios, como tablas y otros objetos.
3. **TEMP:** Tablespace temporal que almacena datos temporales generados por operaciones, como los joins u otras operaciones de clasificación.
4. **UNDO:** Este tablespace almacena información necesaria para deshacer transacciones, permitiendo la recuperación y consistencia transaccional, permiten regresar a un estado anterior de la base de datos en  caso de cometer errores.

## ¿Cómo se relacionan los tablespaces con los datafiles?

Los tablespaces son una unidad lógica de almacenamiento, la cual organiza y agrupa los objetos de la base de datos.
Los datafiles son archivos físicos que almacenan datos reales de un tablespace.

Gracias a los tablespaces, los administradores pueden gestionar y organizar los datos lógicamente, mientras que los datafiles gestionan el almacenamiento físico en el disco.

### Algunas vistas útiles

```SQL
SELECT * FROM DBA_TABLESPACES 
```
Es una consulta que muestra la información acerca de todos los tablespaces de la base de datos. Incluyendo el nombre, el tipo, estado y otras características relacionadas al almacenamiento de estos.
Sirve para obtener una visión general de los tablespaces que se encuentran disponibles en la base de datos.

```SQL
SELECT * FROM DBA_DATA_FILES
```
Recupera los detalles de los archivos de datos asociados a los tablespaces permanentes. Incluye información como el nombre, el tablespace al que pertenece, el tamaño y la ubicación del archivo en el sistema de archivos.
Permite ver los diferentes archivos de datos físicos que almacenan las tablas y otros objetos de base de datos.

```SQL
SELECT * FROM DBA_TEMP_FILES
```
Devuelve los detalles de los archivos temporales relacionados a los tablespaces temporales.
Ayudan a identificar los archivos temporales utilizados por la base de datos para tareas transitorias.

```SQL
SELECT * FROM V$DATAFILE
```
Selecciona información de los datos en tiempo real sobre los archivos de datos actuales de la base de datos, como su estado y el espacio utilizado.
Se usa principalmente para monitorear el estado de los archivos de datos en uso.

```SQL
SELECT * FROM V$TEMPFILE
```
Es una vista dinámica que proporciona información acerca de los archivos temporales actuales en uso por la base de datos.
Es útil para verificar el estado de los archivos temporales durante la ejecución de operaciones transitorias.

```SQL
SELECT * FROM DBA_FREE_SPACE
```
Muestra la información sobre el espacio libre en los tablespaces, incluyendo el tamaño de los segmentos libres de cada tablespace.
Permite monitorear el espacio disponible en los tablespaces, lo cual es crucial para evitar problemas de almacenamiento.

## Trabajando con tablespaces

### Operaciones básicas

-  **Creación de tablespaces:**
```SQL
CREATE SMALLFILE TABLESPACE TS_EMPLEADOS
DATAFILE 'C\Oracle\oradata\ORCL\general_data\DF_EMPLEADO.DBF'
SIZE 10M
```

- **Borrar una tablespace:**
```SQL
DROP TABLESPACE TS_EMPLEADOS
```

- **Borrar totalmente un tablespace:**
```SQL
DROP TABLESPACE TS_EMPLEADOS
   INCLUDING CONTENTS AND DATAFILES;
```

- **Crear una tablespace con varios datafiles asociados:**
```SQL
CREATE SMALLFILE TABLESPACE TS_EMPLEADOS
DATAFILE 
'C:\Oracle\oradata\ORCL\general_data\DF_EMPLEADO_1.DBF' SIZE 10M,
'C:\Oracle\oradata\ORCL\general_data\DF_EMPLEADO_2.DBF' SIZE 5M;
```

### Formas de modificar el tamaño de un tablespace

- **Crear nuevos datafiles**
```SQL
ALTER TABLESPACE TS_EMPLEADOS
ADD DATAFILE 'C:\Oracle\oradata\ORCL\general_data\DF_EMPLEADO_3.DBF' SIZE 10M;
SELECT * FROM DBA_DATA_FILES;
```

- **Agregar datafiles creados anteriormente:**
```SQL
ALTER TABLESPACE TS_EMPLEADOS
ADD DATAFILE 'C:\Oracle\oradata\ORCL\general_data\DF_EMPLEADO.DBF';
SELECT * FROM DBA_DATA_FILES;
```

- **Alterando el tamaño de un datafile:**
```SQL
ALTER DATABASE DATAFILE 'C:\Oracle\oradata\ORCL\general_data\DF_EMPLEADO_3.DBF' RESIZE 15M;
SELECT * FROM DBA_DATA_FILES;
```

### Creación de tablespaces autoextensibles

- **Creando el tablespace autoextensible:**
```SQL
CREATE SMALLFILE TABLESPACE TS_EMPLEADOS
DATAFILE 'C:\Oracle\oradata\ORCL\general_data\DF_EMPLEADO.DBF'
SIZE 1M
AUTOEXTEND ON NEXT 1M
MAXSIZE 100M; -- por defecto: no autoextendibles
```

- **Alterando el tablespace:**
```SQL
ALTER DATABASE DATAFILE 'C:\Oracle\oradata\ORCL\general_data\DF_EMPLEADO.DBF' AUTOEXTEND OFF;
```

### Modificando el estado de un tablespace

- **Modo READ ONLY:**
```SQL
CREATE SMALLFILE TABLESPACE TS_EMPLEADOS
DATAFILE 'C:\Oracle\oradata\ORCL\general_data\DF_EMPLEADO.DBF'
SIZE 10M;

CREATE TABLE EMP__ (
    id INT PRIMARY KEY,
    nombre VARCHAR2(50)
)
TABLESPACE TS_EMPLEADOS;

INSERT INTO EMP__ VALUES (1, 'Margaret Summers');

ALTER TABLESPACE TS_EMPLEADOS READ ONLY;
SELECT * FROM EMP__;
INSERT INTO EMP__ VALUES (2, 'Lilly Mcgee'); --error
UPDATE EMP__ SET nombre = 'Margaret Summers H.' WHERE id = 1; --error
--Ya que es read only, no se pueden insertar ni alterar datos.
```

- **Modo READ WRITE:**
```SQL
ALTER TABLESPACE TS_EMPLEADOS READ WRITE;
```

- **Modo OFFLINE:**
```SQL
ALTER TABLESPACE TS_EMPLEADOS OFFLINE NORMAL;
COMMIT; 
SELECT * FROM EMP__; -- error
```

- **Modo ONLINE:**
```SQL
ALTER TABLESPACE TS_EMPLEADOS ONLINE;
```

