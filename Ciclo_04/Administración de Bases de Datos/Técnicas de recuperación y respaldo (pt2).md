---
tags:
  - Abd
---
Se crea un tablespace para trabajar:
```sql
CREATE SMALLFILE TABLESPACE TS_CLASE16
DATAFILE 'ROUTE' SIZE 10M;
```

Se crea un usuario para trabajar:
```SQL
CREATE USER usuario01
IDENTIFIED BY root
DEFAULT TABLESPACE TS_CLASE16
QUOTA UNLIMITED ON TS_CLASE16
```
Dato: Si no se declara un perfil se le asigna por defecto el perfil DEFAULT.
Dato: recordar que para trabajar con usuarios es necesario alterar la sesión `ALTER SESSION SET "_ORACLE_SCRIPT"=TRUE;`.

Se conecta con el usuario.

Se trabajará con los siguientes datos:
```SQL
CREATE TABLE VENTAS (  
    id INT PRIMARY KEY,  
    producto VARCHAR2(50),  
    cantidad INT,  
    precio_unitario NUMBER(10, 2),  
    fecha_venta DATE  
);  
  
INSERT INTO VENTAS VALUES (1, 'Laptop', 2, 1000.00, TO_DATE('2023-01-15', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (2, 'Mouse', 5, 20.00, TO_DATE('2023-01-16', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (3, 'Keyboard', 3, 30.00, TO_DATE('2023-01-17', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (4, 'Monitor', 1, 200.00, TO_DATE('2023-01-18', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (5, 'Printer', 2, 150.00, TO_DATE('2023-01-19', 'YYYY-MM-DD'));  
COMMIT --Se hace un commit
--Creación de respaldo completo de la base de datos
```

Se realiza un respaldo completo:

```powershell
rman target sys@free
backup database;
```


```SQL
INSERT INTO VENTAS VALUES (6, 'Tablet', 4, 300.00, TO_DATE('2023-01-20', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (7, 'Smartphone', 6, 500.00, TO_DATE('2023-01-21', 'YYYY-MM-DD'));  
COMMIT;

INSERT INTO VENTAS VALUES (8, 'Laptop', 1, 1200.00, TO_DATE('2023-01-22', 'YYYY-MM-DD'));
--La base de dato falla!
--Al hacer el cambio de redolog (si es que se borro la datafile) se detectará el fallo
--Al interactuar con la datafile, falla igualmente
--Se hace un cambio de redo log file para encontrar el error
ALTER SYSTEM SWITCH LOGFILE;

--Si es posible reintentar todo
ALTER DATABASE DATAFILE #datafileID OFFLINE DROP;

INSERT INTO VENTAS VALUES (9, 'Mouse', 10, 18.00, TO_DATE('2023-01-23', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (10, 'Keyboard', 5, 25.00, TO_DATE('2023-01-24', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (11, 'Monitor', 2, 180.00, TO_DATE('2023-01-25', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (12, 'Printer', 1, 170.00, TO_DATE('2023-01-26', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (13, 'Tablet', 3, 280.00, TO_DATE('2023-01-27', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (14, 'Smartphone', 4, 520.00, TO_DATE('2023-01-28', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (15, 'Laptop', 2, 1150.00, TO_DATE('2023-01-29', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (16, 'Mouse', 8, 22.00, TO_DATE('2023-01-30', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (17, 'Keyboard', 6, 35.00, TO_DATE('2023-01-31', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (18, 'Monitor', 1, 250.00, TO_DATE('2023-02-01', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (19, 'Printer', 3, 160.00, TO_DATE('2023-02-02', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (20, 'Tablet', 2, 310.00, TO_DATE('2023-02-03', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (21, 'Smartphone', 5, 480.00, TO_DATE('2023-02-04', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (22, 'Laptop', 3, 1100.00, TO_DATE('2023-02-05', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (23, 'Mouse', 12, 19.00, TO_DATE('2023-02-06', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (24, 'Keyboard', 4, 28.00, TO_DATE('2023-02-07', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (25, 'Monitor', 3, 210.00, TO_DATE('2023-02-08', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (26, 'Printer', 1, 155.00, TO_DATE('2023-02-09', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (27, 'Tablet', 5, 320.00, TO_DATE('2023-02-10', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (28, 'Smartphone', 7, 490.00, TO_DATE('2023-02-11', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (29, 'Laptop', 1, 1300.00, TO_DATE('2023-02-12', 'YYYY-MM-DD'));  
INSERT INTO VENTAS VALUES (30, 'Mouse', 15, 17.00, TO_DATE('2023-02-13', 'YYYY-MM-DD'));
```

```SQL PLUS

```
