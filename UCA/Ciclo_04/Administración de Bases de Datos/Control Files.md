---
tags:
  - Abd
---
## ¿Qué son los Control Files?

Los **Control Files** son archivos binarios críticos, los cuales almacenan información, fundamental de la **estructura** de la base de datos.
Estos archivos contienen metadatos esenciales que permite que Oracle gestione y recupere la base de datos de manera adecuada en caso de que sucedan fallos.
Por su gran importancia, es recomendable mantener múltiples copias de los Control Files en distintos discos para mantener la integridad de la base en caso de que algún otro falle.

## ¿Qué contienen los control Files?

Los control files poseen datos importantes de la base de datos como mencionamos anteriormente, a continuación se enlistarán algunos de estos elementos:

- El nombre de la base de datos
- Nombre y ubicación de los archivos de datos y Redo Log
- Fecha y creación de la base de datos 
- Redo logs disponibles
- Información de Checkpoints
- Entre otra información importante.

## Buenas prácticas al trabajar con Control Files

Es fundamental la aplicación y uso de las buenas prácticas al trabajar con control files para poder garantizar la disponibilidad, recuperación y rendimiento adecuado de la base de datos, a continuación se mencionarán alguna de las principales buenas prácticas al trabajar con las control files:

- **Multiplexeado:** Es recomendable el mantener múltiples copias de los control files
- **Distribución en discos diferentes:**  De la mano con la buena práctica anterior, las copias de los control files se deberían de encontrar ubicadas en distintos discos, es decir, físicamente separados.
- **Respaldos:** Se recomienda también el estar realizando copias de los control files frecuentemente, para evitar tener versiones obsoletas de la base de datos.
- **Supervisión:** Es importante mantener y monitorear el buen funcionamiento de las control files periódicamente para poder asegurarse de que las copias sean accesibles y actualizadas.
- **Evitar modificaciones manuales de las control files**
- **Monitorización de estado:** Asegurarse que el espacio de los discos en donde se almacenarán las control files posean espacio suficientes, con el fin de prevenir errores de escritura en estos.

## Trabajando con Control Files

### Vistas útiles

```sql
SELECT * FROM V$CONTROLFILE;
SELECT * FROM V$DATABASE;
```

### Multiplexeo de una Control File

1. Ingresar a SQL Plus e iniciar sesión
```
User: SYS AS SYSDBA
Password: <Contraseña de administrador>
```
2. Se crea un archivo PFILE a partir del archivo SQPFILE de Oracle
```sql
CREATE PFILE='C:\Oracle23ai\oradata\FREE\abd\init.ora' FROM SPFILE;
```
**init.ora** Es un archivo de texto plano precursor del SPFILE, considerado inseguro.

3. Se apaga la instancia de la base de datos
```sql
SHUTDOWN IMMEDIATE;
```
4. Copiar manualmente un archivo control file, pegar el archivo en la carpeta "/abd/". Renombrar el archivo copiado como 'ABDCONTROL01.CTL'
En este proceso se "crea" una control file a partir de otra file integra.

5. Abrir con un editor de texto el archivo PFILE creado en el paso 2, y agregar la ruta del nuevo control file.
```sql
"*.control_files='C:\Oracle\oradata\ORCL\control01.ctl','C:\Oracle\oradata\ORCL\control02.ctl','C:\Oracle\oradata\ORCL\seccion01\controlfile_backup\ABDCONTROL01.CTL'"
```

6. Probar la configuración, para ello, iniciar la base de datos utilizando el archivo PFILE. 
```sql
STARTUP PFILE='C:\Oracle23ai\oradata\FREE\abd\init.ora';
```
Se inicializa la base de datos a través del archivo init.ora para verificar que todo esté correcto.

7. Si la base de datos inicia sin problemas, la configuración ha sido aplicada correctamente, es posible verificar la configuración con la siguiente instrucción:
```sql
SHOW PARAMETER CONTROL;
```

8. Apagar la instancia de base de datos
```sql
SHUTDOWN IMMEDIATE;
```

9. Actualizar el archivo SPFILE a partir del archivo PFILE creado en el paso 2.
```sql
CREATE SPFILE FROM PFILE='C:\Oracle23ai\oradata\FREE\abd\init.ora';
```
Se crea un nuevo SPFILE a partir del archivo init.ora modificado.

10. Apagar la instancia de base de datos
```sql
SHUTDOWN IMMEDIATE;
```

11. Iniciar la base de datos
```
STARTUP;
```

## Etapas de inicialización de una instancia en Oracle

1. **SHUTDOWN:** Apaga la instancia de base de datos
2. **STARTUPNOMOUNT:** Este modo se usa cuando se desea crear una nueva base de datos o ejecutar procedimientos como la restauración del archivo de control.
3. **STARTUP MOUNT:** Este modo es útil para operaciones de mantenimiento, como la recuperación de la base de datos, la adición de archivos de datos o la administración de archivos de redo logs.
4. **STARTUP OPEN:** Es el modo estándar en el que se inicia la base de datos para que esté disponible para los usuarios.

## Modos de apagado de instancia de Oracle 

|    **Modo de Apagado**     |    **Desconexión de Usuarios**     | **Transacciones activas** | **Tiempo de apagado** |  **Seguridad de datos**   |
| :------------------------: | :--------------------------------: | :-----------------------: | :-------------------: | :-----------------------: |
|    **SHUTDOWN NORMAL**     | Espera a que se desconecten todos  |  Espera a que finalicen   |         Largo         |           Alta            |
|   **SHUTDOWN IMMEDIATE**   |             Inmediata              |    Rollback automático    |       Moderado        |           Alta            |
| **SHUTDOWN TRANSACCIONAL** | Después de finalizar transacciones |   Espera a que terminen   |       Moderado        |           Alta            |
|     **SHUTDOWN ABORT**     |             Inmediata              |    Ninguna (Abortadas)    |      Muy rápido       | Recuperación al reiniciar |

