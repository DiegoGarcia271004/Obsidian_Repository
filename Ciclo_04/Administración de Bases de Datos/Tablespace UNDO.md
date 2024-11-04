---
tags:
  - Abd
---
## ¿Qué es?

En Oracle, un tablespace UNDO es un espacio  de almacenamiento especializado en la base de datos, que maneja y contiene la información de la acción de deshacer (undo) de las transacciones.
Cada vez que se inicia una transacción, Oracle guarda en este tablespace los cambios realizados, en caso de querer revertir la operación mediante un rollback explícito, o en caso de haber fallos.

## Principales funciones

- **Control de transacciones:** Facilita el rollback de una transacción en curso para poder revertir los cambios realizados antes de que se confirme (commit).
- **Recuperación de fallos:** Permite recuperar la base de datos en el dado caso que haya ocurrido un error o falla durante la transacción.
- **Lectura consistente:** Proporciona a las consultas una vista consistente de los datos sin interferir con las transacciones en curso.

## Trabajando con el tablespace UNDO

### Mostrando datos generales

```sql
SHOW PARAMETERS UNDO
```

Mostrando lista de tablespaces y verificando el tablespace UNDO
```sql
SELECT * FROM DBA_TABLESPACES
```

### Creando un tablespace UNDO

```sql
CREATE UNDO TABLESPACE ABD_UNDO 
DATAFILE 'C:\Oracle23ai\oradata\FREE\abd\ABD_UNDO.DBF'
SIZE 64M AUTOEXTEND ON NEXT 8M MAXSIZE 256M;
```

Comprobando la existencia de la tablespace:
```sql
SELECT * FROM DBA_TABLESPACES
```

### Seleccionando otro tablespace UNDO

```sql
ALTER SYSTEM SET UNDO_TABLESPACE = ABD_UNDO SCOPE = BOTH;
```

> [!tip] Nota
>El parámetro SCOPE especifica cómo y dónde se aplicará el cambio. Puede tener tres posibles valores:
>
MEMORY: Aplica el cambio solo en la instancia actual, lo que significa que cuando la instancia se reinicie, la configuración se perderá.
SPFILE: Guarda el cambio en el archivo de parámetros de la base de datos (SPFILE), por lo que se aplicará cuando se reinicie la base de datos.
BOTH: Aplica el cambio de inmediato en la memoria y también lo guarda en el archivo SPFILE, por lo que será persistente después de reiniciar la base de datos.

### Configuración de la retención de datos

```sql
ALTER SYSTEM SET UNDO_RETENTION=1200;
SHOW PARAMETERS UNDO;
-- Configurando la retención de datos eliminados hasta 20 minutos
-- Se debe tener cuidado con esta configuración 
-- el tipo de configuración por defecto no garantiza que se cumpla el tiempo porque
-- Oracle prioriza la ejecución de consultas CRUD sobre el proceso de almacenamiento UNDO

ALTER TABLESPACE ABD_UNDO RETENTION GUARANTEE; 
SHOW PARAMETERS UNDO;
-- Esta configuración prioriza el tiempo de almacenamiento, si nos quedamos sin espacio
-- y se realiza una consulta que actualiza datos, la consulta fallará
```

### Eliminar tablespaces UNDO

```sql
SELECT * FROM DBA_TABLESPACES;
ALTER SYSTEM SET UNDO_TABLESPACE=UNDOTBS1 SCOPE=BOTH;
ALTER SYSTEM SET UNDO_RETENTION=900;
ALTER TABLESPACE ABD_UNDO RETENTION NOGUARANTEE; 
DROP TABLESPACE ABD_UNDO INCLUDING CONTENTS AND DATAFILES;
SHOW PARAMETERS UNDO;
```

## Buenas prácticas al trabajar con tablespaces UNDO

Al trabajar con tablespaces UNDO es importante seguir ciertas prácticas para asegurar el correcto funcionamiento, rendimiento óptimo y gestión eficaz de transacciones, a continuación se describen algunas buenas prácticas.

- **Ajuste del tamaño adecuado:** Se sugiere configurar un tamaño adecuado para el tablespace en función del volumen de las transacciones y duración media de estas. Es posible utilizar la tabla V$UNDOSTAT para obtener métricas avanzadas que ayuden a estimar el tamaño adecuado.
- **Monitoreo regular:** Establecer un plan para revisar las vistas para revisar las vistas de rendimiento como V$UNDOSTAT, DBA