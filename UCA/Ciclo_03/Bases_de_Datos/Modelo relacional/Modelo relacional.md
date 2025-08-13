---
tags:
  - Programacion
---
El modelo relacional es una forma de representar las relaciones entre las entidades de una forma que permita la independencia física, es decir una libertad al momento de almacenar datos. Además de independizarse lógicamente al momento de modificar los datos, almacenando la información en tablas y una relativa facilidad de realizar los diagramas de este modelo.

Ya que conocemos bien la forma del modelo [[Modelo entidad-relación|entidad relación]], se procederán a mostrar los pasos para poder convertir un diagrama entidad-relación, a un diagrama del modelo relacional.

## Entidades
Para poder convertir una entidad del modelo ER, a modelo relacional, se debe crear una tabla, la cual posea como encabezado el nombre de la entidad, en un apartado especial de la tabla, se agregara la llave primaria, asignado con la abreviatura "PK" (Primary key), en los siguientes apartados se colocarán los demás atributos de la entidad, acompañando con una "M" a los atributos multivaluados.
Cabe aclarar que si se poseen atributos que posean diversas subdivisiones, se colocaran **todas** las subdivisiones ignorando el atributo principal.

**Ejemplo:**

![[Entidad|center|5000]]

## Transformaciones

Una vez obtenidas las diversas tablas que poseen la información de las entidades, es momento de relacionarlas. Las relaciones entre tablas pueden variar dependiendo de la cardinalidad mínima y máxima que posean estas, para esto seguiremos ciertas reglas que nos permitirán transformar de modelo ER a modelo relacional.

### Transformación 1:1 
En los casos donde la cardinalidad máxima sea 1-1 al relacionar ambas entidades, se subdivide en dos casos diferentes:

#### Cardinalidad mínima 1-1
En estos casos, se puede elegir a cualquiera de las dos entidades como la entidad que poseerá la llave foránea, sin embargo, en el caso donde se tenga una entidad fuerte y una débil ((0,1) o (1,0)), la entidad fuerte (quién posea el 0) poseerá la llave foránea.

#### Cardinalidad mínima 0-0
En el caso que se posean dos entidades independientes relacionadas, se creará una tabla extra con el nombre de la relación, la cuál posee como llave foránea las claves primarias de las dos entidades.

### Transformación 1:N 

#### Cardinalidad mínima 1-1
En el caso que se posean dos entidades que posean cardinalidades de dependencia obligatorias, simplemente se enlazaran las entidades, y la entidad a la que esté apuntando la cardinalidad "N" poseerá como clave foránea, la clave primaria de la otra entidad.

#### Cardinalidad mínima 1-0 o 0-1
En el caso que se posean entidades independientes, se crea una tabla la cual poseerá el nombre de la relación, como "PK, FK" la llave primaria de la entidad a la que apunta la "N" y como "FK" la llave primaria de la otra relación.

### Transformación N:N
Para los casos en que sean relaciones de muchos a muchos, no se considera la cardinalidad mínima, sino que automáticamente se genera una tabla con el nombre de la relación entre entidades, la cual posee como "PK, FK" las llaves primarias de las dos entidades.