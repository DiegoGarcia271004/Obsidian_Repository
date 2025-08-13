  

---

# Archivos de control

Los archivos de control de Oracle son archivos binarios que contienen la estructura fundamental de la base de datos. Estos archivos contienen la metadata que Oracle necesita para poder llevar a cabo la gestión **y recuperación** de la base de datos. Son extremadamente importantes, por lo que si se llegaran a dañar, la base de datos se arruinó sin oportunidad de recuperación. Es por eso que se recomienda tener múltiples copias de los control files.

  

```sql title:'Vistas útiles'

SELECT * FROM V$CONTROLFILE;

SELECT * FROM V$DATABASE;

```

  

Los control files almacenan entre otras cosas:

- El nombre de la base de datos

- Nombre y ubicación de los [[Redo Log files|archivos Redo Log]]

- Fecha y creación de la base de datos

- Archivos Redo log disponibles

- Información de checkpoints

## Buenas prácticas

Para la administración de los control files, es recomendable tener múltiples copias de estos, y que estas copias no se encuentren en un solo disco duro, sino que en varios; son tan cruciales para el funcionamiento de la base de datos que no se puede correr el riesgo de perderlos en caso de que las copias se pierdan por un disco duro dañado o extraviado.

  

Estas copias de respaldo deben ser actualizadas frecuentemente, y monitoreadas periódicamente para verificar su estado. No sé por qué se haría, son archivos binarios, pero evitar modificar los archivos manualmente. Verificar que haya suficiente espacio para poder hacer copias en las memorias de respaldo para prevenir errores de escritura.

  

Para realizar una copia de un control file, primeramente (porque trabajo con Docker) debe de abrirse la terminal de Linux, para luego iniciar sesión en SQL Plus, todo con el objetivo de apagar la instancia.

  

``` title:'Iniciando sesión en SQL plus' ln:false

$ sudo su

$ docker exec -it oracle23ai sqlplus sys/root as sysdba

$ SQL> SHUTDOWN IMMEDIATE;

$ SQL> EXIT;

```

  

Ahora, corresponde entrar al bash del contenedor. Es ahí donde se encuentran los archivos de la base de datos; y es aquí donde buscaremos la ubicación de los archivos de control para copiarlos.

  

``` title:'Copiando archivos de control' ln:false

$ docker exec -it oracle23ai bash

$ cd /opt/oracle/oradata/FREE/

$ cp control01.ctl ./abd/control01dkr.ctl

$ exit

```

## Agregando nuevo archivos de control

En caso de que se dañe un archivo de control, tenemos que tomar las copias de las memorias de respaldo. Esto se hace primeramente creando el archivo `init.ora`, y para ello es necesario que la base de datos esté iniciada normalmente.

  

``` title:'Creando archivo init.ora' ln:false

$ docker exec -it oracle23ai sqlplus sys/root as sysdba

$ SQL> STARTUP;

$ SQL> CREATE PFILE='/opt/oracle/oradata/FREE/abd/init.ora' FROM SPFILE;

$ SQL> SHUTDOWN IMMEDIATE;

$ SQL> EXIT;

```

  

Entramos a la bash del contenedor con el objetivo de copiar el contenido del archivo `init.ora`. El contenido copiarlo en un editor de texto.

  

``` title:'Accediendo al archivo init.ora' ln:false

$ docker exec -it oracle23ai bash

$ cd /opt/oracle/oradata/FREE/abd/

$ cat init.ora

```

  

Dentro del archivo, modificamos el contenido de este agregando el nuevo control file.

  

```wrap title:'init.ora' info:17

FREE.__data_transfer_cache_size=0

FREE.__datamemory_area_size=0

FREE.__db_cache_size=922746880

FREE.__inmemory_ext_roarea=0

FREE.__inmemory_ext_rwarea=0

FREE.__java_pool_size=0

FREE.__large_pool_size=16777216

FREE.__oracle_base='/opt/oracle'#ORACLE_BASE set from environment

FREE.__pga_aggregate_target=536870912

FREE.__sga_target=1610612736

FREE.__shared_io_pool_size=83886080

FREE.__shared_pool_size=553648128

FREE.__streams_pool_size=0

FREE.__unified_pga_pool_size=0

FREE._instance_recovery_bloom_filter_size=1048576

*.compatible='23.0.0'

*.control_files='/opt/oracle/oradata/FREE/control01.ctl','/opt/oracle/oradata/FREE/control02.ctl','/opt/oracle/oradata/FREE/control01dkr.ctl'

*.db_block_size=8192

*.db_name='FREE'

*.diagnostic_dest='/opt/oracle'

*.dispatchers='(PROTOCOL=TCP) (SERVICE=FREEXDB)'

*.enable_pluggable_database=true

*.local_listener=''

*.nls_language='AMERICAN'

*.nls_territory='AMERICA'

*.open_cursors=300

*.pga_aggregate_target=512m

*.processes=200

*.remote_login_passwordfile='EXCLUSIVE'

*.sga_target=1536m

*.undo_tablespace='UNDOTBS1'

```

  

Una vez hecho esto, creamos un nuevo archivo `init2.ora`. Dentro de este se pegará el contenido recién modificado. Si se crea el archivo con cat, se escribe `cat > init2.ora` y a continuación se mostrará una línea en blanco, donde se puede pegar el contenido. Una vez hecho esto, se sale del editor de cat con `ctrl+D`. Después, se sale de bash y volvemos a entrar en SQL Plus.

  

Se inicia la base de datos haciendo uso del archivo PFILE editado. Hecho esto, es posible verificar si la configuración ha sido aplicada correctamente por medio del comando `{sql icon} SHOW PARAMETER CONTROL`, pero si la base de datos no se enciende, pues no fue aplicada correctamente. Una vez encendida con el archivo modificado, hay que reiniciarla.

  

``` title:'Configurando base de datos' ln:false

$ docker exec -it oracle23ai sqlplus sys/root as sysdba

$ SQL> STARTUP PFILE='/opt/oracle/oradata/FREE/abd/init2.ora';

$ SQL> SHUTDOWN IMMEDIATE;

$ SQL> STARTUP;

```

# Arquitectura de Oracle

Sabemos que Oracle está compuesto por una [[UCA/Ciclo_04/Administración de Bases de Datos/Notas de Mauricio/Tablespaces y Datafiles#Instancia de la base de datos|instancia de la base de datos]] y la base de datos como tal. La instancia está compuesta principalmente por la SGA, la cual componentes como el *Shared Pool, Buffer Cache, Redo Log Buffer*.

  

1. Cuando se realiza una consulta desde la PGA, la consulta es procesada por la SGA de la instancia. Esta consulta es almacenada en la Shared Pool (incluyendo planes de ejecución y estructuras de datos), para que en caso de realizarse la misma consulta otra vez, el resultado pueda ser recuperado instantáneamente. Esto optimiza procesamiento.

2. Los datos recuperados para resolver la consulta son extraídos desde la base de datos y depositados en el Buffer Cache.

3. Si llega a modificarse los datos recuperados de la consulta, estos cambios se hacen en el Buffer Cache, no en la base de datos directamente.

4. Cualquier modificación hecha en los datos es almacenada en un registro temporal, que es el Redo Log Buffer.

5. Cuando se realiza un commit, el registro de los cambios en el Redo Log Buffer es ahora guardada de manera permanente en los archivos Redo Log. Luego, se actualizan en los **archivos de control** para reflejar los cambios, y se registra como un punto de control.

6. Creado el punto de control, los datos modificados que se encontraban en el Buffer Cache son sobrescritos en los datafiles por medio del proceso DBWn (Database Writter). Los datos anteriores al punto de control son considerados archivables en los archivos Redo Log y son escritos físicamente, dando espacio a guardar cambios en el Redo Log online.

# Etapas de inicialización de la instancia

Para poder trabajar con los archivos de la base de datos, lo mejor es que la instancia de la base de datos esté apagada. Cualquier proceso que ocurra en lo que se está trabajando con los archivos corre el riesgo de causar discrepancias en los datos, o en el peor de los casos, corromperlos.

  

Hay diferentes formas en las que se puede apagar la instancia, y estas se describen en la siguiente tabla:

  

| Modo de apagado        | Desconexión de usuarios            | Transacciones Activas  | Tiempo de Apagado | Seguridad de Datos        |

| ---------------------- | ---------------------------------- | ---------------------- | ----------------- | ------------------------- |

| SHUTDOWN NORMAL        | Espera a que se desconecten solos  | Espera a que finalicen | Largo             | Alta                      |

| SHUTDOWN IMMEDIATE     | Inmediata                          | Rollback automático    | Moderado          | Alta                      |

| SHUTDOWN TRANSACTIONAL | Después de finalizar transacciones | Espera a que terminen  | Moderado          | Alta                      |

| SHUTDOWN ABORT         | Inmediata                          | Ninguna (abortadas)    | Inmediato         | Recuperación al reiniciar |

  

Ahora bien, una vez apagada la instancia, es posible inicializar la instancia en diferentes etapas:

- **NOMOUNT**: Para tareas de mantenimiento, inicializa la instancia pero no monta la base de datos.

- **MOUNT**: Inicia la instancia y monta la base de datos, pero no permite que los usuarios trabajen en ella. Es usada para tareas de backup y recuperación.

- **OPEN**: Es la inicialización de la base de datos normal. La instancia es iniciada, la base de datos es montada, y se permite el acceso a los usuarios.