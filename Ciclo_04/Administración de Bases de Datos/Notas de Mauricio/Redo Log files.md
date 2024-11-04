---
tags:
  - Abd
---
  

---

# Archivos de registro REDO

Los archivos Redo Log son archivos que, en esencia, almacenan todos los cambios realizados en la base de datos conforme van ocurriendo. Los datos almacenados en estos archivos son registros REDO (REDO entry), que son un grupo de vectores de cambio, cada uno describiendo un cambio realizado en un solo bloque de la base de datos.

El propósito de los Redo Log files es dar la capacidad de deshacer cambios hechos en la base de datos.

  

Describiendo brevemente el funcionamiento de los Redo Log files en la [[Control files#Arquitectura de Oracle|arquitectura de Oracle]], cuando se realiza un commit, los datos que se encontraban en el Redo Log Buffer, parte del SGA, son escritos en los Redo Log files a través del proceso LGWR (Log Writer). El registro guardado se puede describir como el dato antiguo, el dato nuevo, y el SCN (System Change Number).

  

La verdad es que hay más de un evento que hace que se escriban los datos del Redo Log Buffer a los Redo Log files; puede ser por un commit, cuando el Redo Log Buffer se haya saturado, en la creación de un checkpoint, y cuando se cambia de Redo Log file.

## Estados de los Redo Log files

Hay cuatro estados en el que pueden estar los Redo Log files:

- Inactive

- Active

- Current

  

La arquitectura de Oracle usualmente trabaja con dos Redo Log files, uno se considera activo y el otro se considera en uso (current). La idea es que, cada vez que un log file se ha saturado, ocurre un proceso de Log Switch, y se lleva el seguimiento del Redo Log file anterior y con el que se hizo el cambio. Los demás Redo Log files que no se les esté dando seguimiento se consideran inactivos.

  

```sql title:'Forzando Log Switch'

-- No hay que abusar de este comando, Oracle puede hacerlo solo.

ALTER SYSTEM SWITCH LOGFILE;

```

  

## Trabajando con Redo Log files

  

```sql title:'Vistas útiles'

SELECT * FROM V$LOG;

SELECT * FROM V$LOGFILE;

```

  

Al utilizar la vista `{sql icon}V$LOG`, los datos pertinentes son `GROUP#` y `STATUS`. Ya se explicó sobre los estados, así que centrándose en los grupos, pues indican a qué grupo pertenece el Redo Log file. Si no se ha hecho nada, hay un archivo por grupo, pero idealmente deberían haber replicas de estos archivos.

  

```sql title:'Agregando datafiles a los grupos'

ALTER DATABASE

ADD LOGFILE MEMBER '/opt/oracle/oradata/FREE/abd/REDO01-B.LOG'

TO GROUP 1;

  

ALTER DATABASE

ADD LOGFILE MEMBER '/opt/oracle/oradata/FREE/abd/REDO02-B.LOG'

TO GROUP 2;

  

ALTER DATABASE

ADD LOGFILE MEMBER '/opt/oracle/oradata/FREE/abd/REDO03-B.LOG'

TO GROUP 3;

```

  

Cuando se agrega un nuevo [[Tablespaces y Datafiles#Datafile|datafile]] a un grupo de Redo Log, el estado de dicho archivo será inválido hasta que se realice un Switch Log. Tras el Switch Log, el estado cambiará y su existencia se verá reflejada en los archivos Redo Log.

  

```sql title:'Agregando grupos de Redo Log files'

ALTER DATABASE ADD LOGFILE GROUP 4

    ('/opt/oracle/oradata/FREE/abd/REDO04-A.LOG',

    '/opt/oracle/oradata/FREE/abd/REDO04-B.LOG') SIZE 200M;

```

  

Cuando se crea un grupo nuevo, si no ha ocurrido un Switch Log, el grupo debería tener una secuencia de 0 y el estado UNUSED, mientras que los archivos creados tendrán el estado INVALID.

  

```sql title:'Borrando Redo Log files' error:4,5 info:8

ALTER DATABASE

DROP LOGFILE MEMBER '/opt/oracle/oradata/FREE/abd/REDO04-B.LOG';

  

ALTER DATABASE

DROP LOGFILE MEMBER '/opt/oracle/oradata/FREE/abd/REDO04-A.LOG'

  

-- No se puede borrar el último miembro de un grupo

ALTER DATABASE DROP LOGFILE GROUP 4;

```