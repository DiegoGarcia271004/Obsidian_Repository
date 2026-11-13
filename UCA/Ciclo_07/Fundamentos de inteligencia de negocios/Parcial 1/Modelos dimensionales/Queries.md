--¿Cuáles son los productos más vendidos?
```SQL
SELECT P.NOMBRE, SUM(F.UNIDADES) UNIDADES 
FROM datawarehouse.fact_ventas F
LEFT JOIN datawarehouse.dim_producto P ON F.PRODUCTOID = P.PRODUCTOID
GROUP BY P.NOMBRE
ORDER BY UNIDADES DESC
LIMIT 5;
```
--¿En qué distritos se generan más ventas?
```SQL
SELECT T.DISTRITO, SUM(F.TOTAL) VENTAS
FROM datawarehouse.fact_ventas F
LEFT JOIN datawarehouse.dim_tienda T ON F.TIENDAID = T.TIENDAID
GROUP BY T.DISTRITO
ORDER BY VENTAS DESC
LIMIT 5;
```
--¿Quienes compran más? hombres o mujeres
```sql
SELECT C.SEXO, COUNT(*) VENTAS
FROM datawarehouse.fact_ventas F
INNER JOIN datawarehouse.dim_cliente C ON F.CLIENTEID = C.CLIENTEID
GROUP BY C.SEXO
ORDER BY VENTAS DESC;
```
--¿Quienes son los vendedores que generan menos ventas?
```sql
SELECT V.NOMBRE, SUM(F.TOTAL) VENTAS
FROM datawarehouse.fact_ventas F
INNER JOIN datawarehouse.DIM_VENDEDOR V ON F.VENDEDORID = V.VENDEDORID
GROUP BY V.NOMBRE
ORDER BY VENTAS ASC
LIMIT 5;
```
--¿En qué mes se hicieron más ventas?
```sql
SELECT 
    T.mes,
    SUM(V.total) as total_ventas,
    COUNT(*) as cantidad_facturas
FROM datawarehouse.fact_ventas V
JOIN datawarehouse.dim_tiempo T ON V.fechaemision = T.tiempoid
GROUP BY T.mes
ORDER BY total_ventas DESC
LIMIT 1;
```
--¿Cual es la subcategoria de productos mas vendida? ¿a que categoria pertenece?
```sql
SELECT 
	P.SUBCATEGORIA,
	P.CATEGORIA,
	COUNT(*) VENTAS
FROM datawarehouse.fact_ventas V
JOIN datawarehouse.dim_producto P ON V.PRODUCTOID = P.PRODUCTOID
GROUP BY P.SUBCATEGORIA, P.CATEGORIA
ORDER BY VENTAS DESC
LIMIT 5;
```
--¿Cual es el promedio de ventas por mes y año?
```SQL
SELECT
	T.MES,
    ROUND(AVG(V.TOTAL), 2) PROM
FROM datawarehouse.fact_ventas V
JOIN datawarehouse.dim_tiempo T ON V.FECHAEMISION = T.TIEMPOID
GROUP BY T.MES
ORDER BY T.MES ASC;

SELECT
	T.ANIO,
    ROUND(AVG(V.TOTAL), 2) PROM
FROM datawarehouse.fact_ventas V
JOIN datawarehouse.dim_tiempo T ON V.FECHAEMISION = T.TIEMPOID
GROUP BY T.ANIO
ORDER BY T.ANIO ASC;
```
--¿Cual es la edad promedio de los clientes por categoria?

--¿Cual es la tienda con mas productos vendidos?

--¿Cuanto es el total de venta por tipo de cliente?

--¿Total de IVA por producto?

--Producto más vendido por cada tienda

--Promedio de unidades vendidas en cada factura

--Clientes que compraron en más de una tienda