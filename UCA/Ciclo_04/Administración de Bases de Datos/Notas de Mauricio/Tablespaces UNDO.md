---
tags:
  - Abd
---
  

---

# Tablespace UNDO

El [[UCA/Ciclo_04/Administración de Bases de Datos/Notas de Mauricio/Tablespaces y Datafiles#Tablespaces|tablespace]] UNDO es un tablespace especial de Oracle, pues en este se almacena la información de deshacer de las transacciones. Básicamente, guarda los cambios realizados para que, en caso de un fallo o de un rollback, pueda revertir las operaciones realizadas. Entre las principales funciones del tablespace UNDO se encuentran:

- Control de transacciones

- Recuperación de fallos

- Lectura consistente

  

Dentro de la [[UCA/Ciclo_04/Administración de Bases de Datos/Control Files#Arquitectura de Oracle|arquitectura de Oracle]], el tablespace UNDO es actualizado en el mismo instante que se realiza un commit. La información proviene del *Redo Log Buffer* y es la que se almacena en los [[Redo Log files|archivos Redo Log]], pero en ellos se encuentran los datos antes y después de la modificación. El tablespace UNDO solo contiene los datos antiguos.

## Lectura consistente

Elaborando en la función de lectura consistente, la idea es cuando una base de datos está siendo usada por varios usuarios a la vez; si alguien actualiza la base de datos y hace un commit, entonces no es necesario que el resto de los usuarios tenga que actualizar la base de datos para seguir trabajando, sino que los datos son sacados del tablespace UNDO.

  

![[reading-consistency.png]]

  

# Administrando Tablespace UNDO

Se pueden mostrar los datos generales del tablespace UNDO por medio del comando `{sql icon}SHOW PARAMETERS UNDO`.

  

``` title:'Parametros del tablespace UNDO' ln:false

SQL> SHOW PARAMETERS UNDO;

  

NAME                                 TYPE        VALUE

------------------------------------ ----------- ----------------------

temp_undo_enabled                    boolean     FALSE

undo_management                      string      AUTO

undo_retention                       integer     900

undo_tablespace                      string      UNDOTBS1

```

  

- `{sql icon}undo_management`: Es la forma en la que se va a manejar el tablespace UNDO. Actualmente, Oracle lo hace de manera automática, pero antes era un trabajo que tenía que realizarse manualmente.

- `{sql icon}undo_retention`: Es el tiempo mínimo que se conserva un dato del tablespace UNDO. El parámetro se mide en segundos, por lo que para el ejemplo, los datos se conservan en la tabla por un mínimo de 15 minutos (900 segundos).

- `{sql icon}undo_tablespace`: Es el nombre del tablespace definido como UNDO. En este caso, es el tablespace UNDOTBS1.

  

Es posible verificar la existencia del un tablespace UNDO por medio de `{sql icon}SELECT * FROM DBA_TABLESPACES`. Es posible crear más tablespaces que acepten contenido UNDO.

  

```sql title:'Creando un tablespace UNDO' info:5,6

CREATE UNDO TABLESPACE ABD_UNDO

DATAFILE '/opt/oracle/oradata/FREE/abd/ABD_UNDO.dbf'

SIZE 64M AUTOEXTEND ON NEXT 8M MAXSIZE 256M;

  

ALTER SYSTEM SET UNDO_TABLESPACE = ABD_UNDO

SCOPE = BOTH;

  

SELECT * FROM DBA_TABLESPACES;

```

  

Solo puede haber un tablespace seleccionado como el tablespace UNDO a la vez. Para cambiar la selección del tablespace, hay que considerar al parámetro `{sql icon}SCOPE`. Este parámetro acepta tres valores:

- `{sql icon}MEMORY`: Guarda los cambios en la instancia solamente. Esto significa que, una vez reiniciado la base de datos, los cambios en la configuración se perderán.

- `{sql icon}SPFILE`: Guarda los cambios en el archivo de parámetros de la base de datos. Los cambios se ejecutarán hasta que se reinicie la base de datos.

- `{sql icon}BOTH`: Guarda los cambios en la instancia y la base de datos.

  

Una cosa también que se puede mencionar es que la retención de datos del tablespace UNDO no es garantizada, pues Oracle prioriza la ejecución de consultas CRUD. Si el tablespace UNDO se queda sin espacio, entonces los demás cambios y datos antiguos no se guardarán.

  

```sql title:'Configurando tablespace UNDO'

ALTER SYSTEM SET UNDO_RETENTION = 1200;

ALTER TABLESPACE ABD_UNDO RETENTION GUARANTEE;

```

  

Añadido que la retención de los datos del tablespace UNDO sea garantizada, ahora se prioriza el tiempo de retención de datos. Si el tablespace UNDO está saturado y no ha pasado el tiempo de retención mínima, cualquier consulta que actualize datos fallará.

  

```sql title:'Eliminando tablespace UNDO'

-- Regresando a la configuración normal

ALTER SYSTEM SET UNDO_TABLESPACE=UNDOTBS1 SCOPE=BOTH;

ALTER SYSTEM SET UNDO_RETENTION = 900;

ALTER TABLESPACE ABD_UNDO RETENTION NOGUARANTEE;

  

DROP TABLESPACE ABD_UNDO INCLUDING CONTENTS AND DATAFILES;

```

  

## Buenas prácticas

Primeramente, establecer un tamaño acorde con las transacciones que se realizan en la tabla de datos. Si el tamaño del tablespace es muy pequeño, no se guardarán todos los datos en caso de que se prioricen las transacciones; y si se prioriza la retención de datos, no será posible realizar transacciones si el tablespace se satura. Es por eso que hay que ajustar el tamaño asignado al volumen de transacciones y la duración media de estas. Es posible obtener información que nos ayude a estimar el tamaño del tablespace UNDO por medio de la vista `{sql icon}V$UNDOSTAT`.

  

La carga de información que recibe el tablespace UNDO debe ser monitoreado para determinar qué cambios deben realizarse de manera que el rendimiento de la base de datos no se vea afectado. Las vistas `{sql icon}V$UNDOSTAT`, `{sql icon}DBA_UNDO_EXTENTS` y `{sql icon}DBA_ROLLBACK_SEGS` son de mucha utilidad, y es recomendable establecer un plan para revisarlas.

  

La retención de los datos debe ser configurada para cubrir transacciones de lectura largas. En general, hay que conocer bien el entorno de trabajo para determinar cuánto tiempo deben ser retenidos los datos del tablespace UNDO.

  

Se sugiere colocar los tablespace UNDO en discos duros de alta velocidad para que puedan manejar la cantidad de operaciones que se hacen en el tablespace. Esto es porque es maneja muchos procesos de entrada y salida, por lo que minimizar el tiempo de acceso a los datos es crucial para el buen rendimiento de la base de datos.

Siempre en la idea del rendimiento, se recomienda crear un tablespace de tamaño fijo que sea lo suficientemente grande, para así no tener que recurrir a la fragmentación del tablespace; por lo que se debe hacer un análisis para determinar el tamaño necesario.

  

Para el entorno de trabajo Oracle RAC (Real Application Clusters), cada usuario debe tener su propio tablespace UNDO, esto con el objetivo de prevenir conflictos por el uso compartido. Antes de pasar a la fase de producción, se deben realizar pruebas que simulen la carga que experimentarán los tablespaces UNDO en un entorno real.