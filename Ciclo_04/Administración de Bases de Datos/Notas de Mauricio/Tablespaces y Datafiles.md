---
tags:
  - Abd
---

# Instancia de la base de datos

Ya se ha mencionado que, en el caso particular de Oracle, se tiene una base de datos general al cual se puede acceder mediante instancias. Elaborando en qué son las instancias, estas no son el motor de la base de datos como tal, sino que simplemente es un espacio de memoria asignado para trabajar con el [[Introducción a SQL|SGBD]].

Una instancia, a groso modo, está compuesta por el SGA (System Global Area) y los procesos en segundo plano que se ejecutan para poder conectarse y trabajar con los datos guardados en la base de datos, datos que se encuentran almacenados en archivos. Para poder trabajar con una instancia, es necesario trabajar con la PGA (Program Global Area), que es otro espacio de memoria que se asigna a la sesión que se conecta a la instancia. Se puede decir que la PGA es la herramienta con la que el administrador trabaja directamente.

# Tablespaces

Es una **unidad lógica** de almacenamiento (no forma parte de la memoria de la instancia, son una característica propia de la base de datos) que agrupa uno o más *datafiles*. Los tablespaces son los que contienen a los objetos que pertenecen a la base de datos, como lo son las tablas y los índices.

  

La gestion de los *espacios de tabla* permite mejorar el rendimiento de la base de datos, crear copias de seguridad, y organizar los datos eficientemente. Es posible ajustar el tamaño de un tablespace y cambiar objetos entre tablespaces de ser necesario.

## Tipos de tablespaces

- **SYSTEM y SYSAUX:** Por los nombres podemos inferir que son muy importantes. Estos espacios de tabla contienen todo lo necesario para que la base de datos funciona. En el caso de `SYSTEM`, esta contiene el diccionario de los objetos del sistemas fundamentales de la base de datos; mientras que `SYSAUX` posee datos auxiliares (pero siempre esenciales).

- **Tablespaces de usuario**: Son los espacios de tabla ==que se crean== con el propósito de almacenar los datos de los usuarios que trabajan con la instancia.

- **TEMP:** Es un tablespace temporal que se crea para almacenar datos temporales, que luego serán destruidos; como los datos que se recopilan para las operaciones [[(COMPLETAR) SQL Joins|JOIN]], tablas temporales, entre otros.

- **UNDO:** Tablespace crucial para almacenar la información necesaria para deshacer transacciones. Almacena los datos de la base de datos antes de que se confirmen (por medio de `commit`); o dicho de otra forma, es un historial de los cambios no permanentes que se han hecho.

## Estados de un tablespace

Los estados indican las acciones que pueden realizarse con un tablespace. Si un tablespace se encuentra "en línea", es posible trabajar con el espacio de tabla; pero si está "fuera de línea" no es posible realizar cualquier tipo de acción con los objetos del tablespace. Además, se encuentra `READ ONLY` y `READ WRITE`, que son estados que indican el tipo de acciones que pueden hacerse con un tablespace.

## Estructuración de un tablespace

La memoria dentro de un espacio de memoria es distribuida en tres categorías, por así decirlo.

### Bloques

La unidad lógica de almacenamiento más básico es denominado **bloque**; y está compuesto por tres tipos secciones de información:


Como se mencionó, son la unidad de memoria más pequeña administrada por Oracle, y toda la información que se guarda en la base de datos es almacenada a través de bloques. Para dimensionar el tamaño de un bloque, estos suelen contener desde una a dos filas en general; aunque esto puede variar dependiendo del tamaño del bloque y de las filas. Los bloques ocupan memoria en un rango de entre 2 KB a 32 KB generalmente, pero es configurable.

### Extensiones

Es un conjunto contiguo de bloques, como una especie de arreglo o pila. Es por medio de las extensiones que es posible controlar el nivel de crecimiento que tiene un objeto en cuestión, como las tablas. Oracle las administra de manera automática, pero es posible hacer cambios nosotros mismos para regular mejor su comportamiento.

### Segmentos

Las extensiones contienen bloques, los segmentos contienen extensiones. Estos son asignados de manera lógica a los elementos lógicos de la base de datos, y se entiende que todo objeto debe tener asignado al menos un segmento.

# Datafile

Los tablespace son espacios virtuales, son espacios lógicos. ==Tiene que haber algo que permita guardar los datos de manera física. **Eso son los datafiles**.== Un datafile es un archivo físico en el sistema operativo que almacena los datos reales de la base de datos.

  

Los tablespace y datafiles trabajan en conjunto para administrar el contenido de la base de datos. Los datafiles almacenan físicamente la información con los que trabajan los tablespaces, y los tablespaces agrupan y organizan estos datos a la hora de trabajar.

  

Los tablespaces pueden ser manipulados y gestionados para organizar la base de datos como el administrador lo vea conveniente, mientras que los datafiles gestionan el almacenamiento físico de la base de datos, y rara vez son manipulados directamente; para eso está el sistema gestor de base de datos que los lee, y los tablespaces. Si se llega a trabajar con los datafiles, usualmente es para recuperar datos, migrar datos o casos muy específicos de optimización del rendimiento de la base de datos.

# Trabajando con tablespaces y datafiles

Una vez en la instancia de la base de datos, es posible utilizar las siguientes [[SQL Vistas (COMPLETAR)|vistas]] para observar los tablespaces que hay en la base de datos, o bien los datafiles:

  

```sql title:'Vistas útiles'

SELECT * FROM DBA_TABLESPACES;

SELECT * FROM DBA_DATA_FILES;

SELECT * FROM DBA_TEMP_FILES;

SELECT * FROM V$DATAFILE;

SELECT * FROM V$TEMPFILE;

SELECT * FROM DBA_FREE_SPACE;

```

  

Para crear un tablespace nuevo, es necesario identificar la dirección del directorio en el que se va a crear. Una nueva característica de la versión más reciente de Oracle es que los tablespace, por defecto, crean archivos `BIGFILE`. Para propósitos de la clase, no es necesaria tanta memoria, por lo que se especifica que es un `SMALLFILE`.

  

```sql title:'Creando tablespace'

-- Creando un tablespace

CREATE SMALLFILE TABLESPACE TS_EMPLEADOS

DATAFILE 'opt/oracle/oradata/FREE/abd/DF_EMPLEADOS.dbf'

SIZE 10M;

  

-- Borrando un tablespace

DROP TABLESPACE TS_EMPLEADOS;

DROP TABLESPACE TS_EMPLEADOS INCLUDING CONTENTS;

DROP TABLESAPCE TS_EMPLEADOS INCLUDING CONTENTS AND DATAFILES;

```

  

Como se mencionó, un tablespace puede contener múltiples datafiles. La forma de asignar múltiples datafiles a un tablespace es la siguiente:

  

```sql title:'Tablespace con múltiples datafiles'

CREATE TABLESPACE TS_EMPLEADOS

DATAFILE

'/opt/oracle/oradata/FREE/abd/DF_EMPLEADOS_1.dbf' SIZE 10M,

'/opt/oracle/oradata/FREE/abd/DF_EMPLEADOS_2.dbf' SIZE 5M;

  

ALTER TABLESPACE TS_EMPLEADOS

ADD DATAFILE '/opt/oracle/oradata/FREE/abd/DF_EMPLEADOS_3.dbf' SIZE 10M;

  

-- Para verificar los cambios hechos:

SELECT * FROM DBA_DATA_FILES;

  

-- Modificando el tamaño de un datafile

ALTER DATABASE DATAFILE '/opt/oracle/oradata/FREE/abd/DF_EMPLEADOS_2.dbf'

RESIZE 10M;

```

  

Por defecto, Oracle crea extensiones de memoria que pueden ser de 64 KB, 1 MB, 8 MB o 64 MB, y dentro de estas extensiones es donde se colocan los objetos del tablespace.

  

```sql title:'Extensiones de un tablespace' info:4,8

CREATE SMALLFILE TABLESPACE TS_EMPLEADOS

DATAFILE '/opt/oracle/oradata/FREE/abd/DF_EMPLEADO.DBF'

SIZE 10M

EXTENT MANAGEMENT LOCAL AUTOALLOCATE;

  

-- La opción resaltada es por defecto, la alternativa es establecer

-- un tamaño de extensión fija.

EXTENT MANAGEMENT LOCAL UNIFORM SIZE 1M;

```

  

Los objetos creados que son asignados a un tablespace son colocados en una o varias extensiones, y si el objeto llegará a rebalsar la memoria, se le asignan más extensiones. Con `AUTOALLOCATE`, el tamaño de la extensión no será fija, y habrán extensiones de diversos tamaños, pero con `UNIFORM SIZE` todas las extensiones serán del mismo tamaño. Hay tanto espacio de memoria disponible como lo permitan los datafiles del tablespace.

  

```sql title:'Asignando tabla a un tablespace' info:5-6

CREATE TABLE EMP__ (

   id INT PRIMARY KEY,

   nombre VARCHAR2(50)

)

TABLESPACE TS_EMPLEADOS

STORAGE (INITIAL 100K);

```

  

La tabla creada es asignada al espacio de tabla. La sentencia `{sql icon} STORAGE (INITIAL 100K)` indica que la extensión a la que pertenece la tabla tendrá un tamaño inicial de 100 KB, pero esto solo tendrá efecto el tablespace está configurado con `{sql icon} AUTOALLOCATE` o si el tamaño fijo establecido fuera menor que 100 KB.

Si se tiene una situación donde el espacio de tabla tiene la configuración `{sql icon} EXTENT MANAGEMENT LOCAL UNIFORM SIZE 1M`, se ignora la sentencia y la tabla es asignada a una extensión de 1 MB de memoria.

  

```sql title:'Verificando extensiones'

SELECT * FROM DBA_SEGMENTS WHERE SEGMENT_NAME = 'EMP__';

SELECT * FROM DBA_EXTENTS WHERE SEGMENT_NAME = 'EMP__';

```

  

Para modificar los estados del tablespace, se hace uso del comando `{sql icon} ALTER`. Si el estado del tablespace es cambiado a `OFFLINE`, entonces no es posible realizar ningún tipo de acción. En general, hay dos formas de "desconectar" un tablespace, siendo estas `NORMAL` e `IMMEDIATE`.

  

```sql title:'Estados de un tablespace' error:2,9-10 info:5,14-15

ALTER TABLESPACE TS_EMPLEADOS OFFLINE NORMAL;

SELECT * FROM EMP__; --error

  

ALTER TABLESPACE TS_EMPLEADOS ONLINE;

SELECT * FROM EMP__; --it works

  

ALTER TABLESPACE TS_EMPLEADOS READ ONLY;

SELECT * FROM EMP__;

INSERT INTO EMP__ VALUES (2, 'Lilly Mcgee'); --error

UPDATE EMP__ SET nombre = 'Margaret Summers H.' WHERE id = 1; --error

  

ALTER TABLESPACE TS_EMPLEADOS READ WRITE;

SELECT * FROM EMP__;

INSERT INTO EMP__ VALUES (2, 'Lilly Mcgee'); --it works

UPDATE EMP__ SET nombre = 'Margaret Summers H.' WHERE id = 1; --it works

```

  

El tamaño del tablespace está determinado por el tamaño de los datafiles. Si los datafiles están saturados, no es posible llenar más datos; pero hay una posible solución para esto, y es permitir que, de rebalsar los datos, se le asigne más memoria al datafile. Ahora bien, permitir que un datafile crezca indefinidamente no siempre es buena idea, pues el disco duro será el que se sature rápidamente; por eso se agrega un límite máximo.

  

```sql title:'Tablespaces autoextendibles' info:4-5

CREATE SMALLFILE TABLESPACE TS_EMPLEADOS

DATAFILE '/opt/oracle/oradata/FREE/abd/DF_EMPLEADOS.dbf'

SIZE 1M

AUTOEXTEND ON NEXT 1M -- Aumento de memoria al rebalsar

MAXSIZE 100M; -- Límite de tamaño máximo

  

-- Modificando opción del tablespace

ALTER DATABASE

DATAFILE '/opt/oracle/oradata/FREE/abd/DF_EMPLEADOS.dbf'

AUTOEXTEND OFF;

```

  

Por defecto, los tablespaces no se extienden, sino que tienen un tamaño estático. También es posible reducir el tamaño de un datafile, siempre y cuando ese espacio reducido esté vacío.

  

```sql title:'Reduciendo tamaño de un tablespace' info:5-7 error:9-11

ALTER TABLESPACE TS_EMPLEADOS

ADD DATAFILE '/opt/oracle/oradata/FREE/abd/DF_PRODUCTOS.dbf'

SIZE 10M;

  

ALTER DATABASE

DATAFILE '/opt/oracle/oradata/FREE/abd/DF_PRODUCTOS.dbf'

RESIZE 5M;

  

ALTER DATABASE

DATAFILE '/opt/oracle/oradata/FREE/abd/DF_PRODUCTOS.dbf'

RESIZE 512K;

```

  

Ahora, los datafiles pueden ser renombrados o cambiados de directorio por dos métodos. Mientras la base de datos está encendida o apagada. Si se [[Ciclo_04/Administración de Bases de Datos/Control Files#Etapas de inicialización de la instancia|apaga la base de datos]], por medio del comando `{sql icon}SHUTDOWN IMMEDIATE`, se pueden copiar y pegar los datafiles en otro directorio, y renombrarlos manualmente.

  

``` title:'Renombrando datafiles' ln:false

SQL> SHUTDOWN IMMEDIATE;

  

SQL> STARTUP MOUNT;

  

SQL> ALTER DATABASE

   2 RENAME FILE '/opt/oracle/oradata/FREE/DF_EMPLEADOS.dbf'

   3 TO '/opt/oracle/oradata/FREE/abd/DF_EMPLEADOS.dbf';

SQL> ALTER DATABASE OPEN;

```

  

La primera ruta del archivo determina el nombre del archivo antiguo y la segunda la del nuevo archivo. Esto se puede usar para recolocar los archivos, donde la primera ruta era la dirección antigua y la segunda ruta es la nueva dirección del datafile.

  

---

# Apéndice

**Por que soy un cobarde** y no intenté instalar oracle directamente, estoy obligado a trabajar con Docker. Entonces, para poder trabajar con directorios en Docker, se deben seguir los siguientes pasos.

  

1. Inicializar el contenedor de Docker, y esperar a que la base de datos se haya inicializado correctamente.

2. Abrir la consola de Ubuntu, y acceder al contenedor a través de bash:

  

``` title:'Consola' ln:false

   $ docker exec -it oracle23ai bash

```

  

3. Crear el directorio en el directorio principal de la instancia de la base de datos. La ruta de esta es `/opt/oracle/oradata/FREE/`. Por ejemplo, si se quiere crear un directorio en de nombre `abd`, se ejecuta el siguiente comando:

  

``` title:Consola ln:false

$ mkdir /opt/oracle/oradata/FREE/abd

```

  

4. Hecho esto, salimos de bash con el comando `exit`.





