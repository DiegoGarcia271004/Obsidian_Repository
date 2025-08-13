---
tags:
  - Programacion
---
La normalización es un proceso de suma importancia para poder diseñar bases de datos relacionales.
La normalización consiste en aplicar una serie de reglas a nuestro modelo entidad-relación para convertirlo en un modelo relacional.

### ¿Por qué es importante la normalización?
la normalización busca poder optimizar datos dentro del modelo relacional, brindando integridad al modelo.
Algunas de las ventajas que se pueden obtener al normalizar son:
1. Reducción de la redundancia de los datos
2. Mejora del rendimiento de las consultas al acceso de los datos
3. Velar por la integridad de los datos
4. Poseer esquemas más flexibles y que permiten un mantenimiento más sencillo
5. Facilita operaciones concurrentes
6. Optimiza el almacenamiento y el indexado

## Normalización
Para poder normalizar una base de datos se deben aplicar las formas normales, las cuales son el conjunto de reglas que establecen la normalización de la base de datos. Si bien existen varias formas normales, nosotros nos centraremos en aplicar las primeras tres formas normales para nuestras bases de datos.

## Primera forma normal (1FN)
La primera forma normal consiste en garantizar que cada uno de los atributos, solo contengan un valor atómico, es decir que en los atributos de las entidades no deben de existir valores multivaluados, valores repetidos en una fila para una clave primaria, ni datos que puedan formar estructuras dentro de los atributos.

Si aplicamos esta forma normal dentro del modelo relacional, consta en anidar una tabla extra a la entidad con el nombre del atributo multivaluado, con su clave primaria siendo un id del atributo, además de poseer una clave foránea proveniente de la entidad a la que pertenecía anteriormente.

**Ejemplo:**

![[1FN|Normalización|center|1000]]

## Segunda forma normal (2FN)
Para poder aplicar la segunda forma normal, es necesario que el modelo relacional ya se encuentre en la forma de la primera forma normal, una vez aplicada la 1FN, la 2FN indica que cada uno de los atributos de las entidades deben depender **completamente** de la clave primaria (PK) del producto. Es decir, si existen algunos atributos que no dependen en su totalidad de la llave primaria (dependencia parcial), sino de otro de los atributos de la entidad. En el caso que se de esto, se debe de realizar otra tabla con los atributos con dependencia parcial dependan de una clave primaria de un atributo de la entidad, que dependa totalmente de la clave primaria de la entidad.

**Ejemplo:**
![[2FN|center|1000]]

En el caso del ejemplo anterior, el atributo "cargo" podría tomar diversos valores, tales como: tesorero, oficinista, contador, entre otros.

## Tercera forma normal (3FN)
De igual forma que para 2FN, para poder aplicar la 3FN debe de estar ya en la forma de la segunda. Como caso especial de la tercera, se deben evitar las dependencias transitivas, es decir, un atributo que no depende de la clave primaria de la entidad, si no de otro atributo el cual si depende de la clave primaria.
Para evitar estas dependencias transitivas, se crea una nueva tabla que cumple con las mismas características que las tablas creadas de la forma 2FN.

**Ejemplo:**
![[3FN|center|1000]]