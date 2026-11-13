
Estas memorias solo ejecuta la operación de lectura (no se pueden sobrescribir los valores que trae guardados) haciendo que la información guardada sea permanente,

Una ROM $m\times n$ es un arreglo de celdas binarias organizadas en $m$ palabras de $n$ bits cada una. Este tipo de memorias contiene $k$ líneas de entrada de dirección para seleccionar una de $2^{k}=m$ palabras de memoria y $n$ líneas de salida.

Es decir que una de una memoria ROM que posea 10 entradas y 5 salidas se puede obtener lo siguiente:

| Parámetro                   | Valor                       | Descripción                                                                    |
| --------------------------- | --------------------------- | ------------------------------------------------------------------------------ |
| Capacidad de almacenamiento | $2^{10}$ localidades (1 KB) | La memoria posee esta cantidad de filas de datos                               |
| Ancho de palabra            | 5 bits                      | Es el tamaño de cada uno de los datos almacenados                              |
| Capacidad en bits           | $2^{10}\times 5$ bits       | Es la cantidad total de localidades multiplicada por el tamaño de cada palabra |
| Líneas de datos             | 5 líneas                    | Estas se enumeran desde $D_{0}$ hasta $D_{4}$                                  |
| Líneas de dirección         | 10 líneas                   | Enumerándose desde $A_{0}$ hasta $A_{9}$                                       |
A continuación se muestra un diagrama de una memoria ROM de $k=14$ y $n=8$:
![[Pasted image 20260327123546.png|center]]
### Variantes tecnológicas

Por la naturaleza de las ROM una vez fabricadas no es posible alterar el interior de estas, Que en el uso habitual de las ROM de almacenar programas fijos (rutinas en el inicio de una computadora, programa de un controlador de semáforos, etc).
Estos programas poseen correcciones y mejoras constantes, lo que hace poco práctico el producir nuevas ROM cada vez que se debe hacer un cambio. Lo que llevó al desarrollo de nuevas variante de la ROM.

#### PROM

Las PROM son Programable ROM. Siendo una memoria cuyo contenido puede ser definido a posteriori de ser construida.

Estas poseen en sus entradas Dij a las AND de selección una conexión a tierra (0) como a Vcc (1). Estas conexiones están echas con un fusible que se quema al momento de ingresar la información a la memoria. Si se quiere grabar un 1, se quema el fusible de la conexión a tierra, y si se quiere guardar un 0, se quema la conexión a Vcc.

#### EPROM

Si bien las PROM fueron un gran avance, aún el hecho de que no se pudiera regresar representaba una restricción para el uso intensivo de las PROM. De esta misma necesidad nacieron las EPROM, que en esencia son PROMs cuyo contenido puede ser borrado, pero su proceso de borrado es completamente distinto a como se les programa.

Para poder borrar el contenido de una PROM, es necesario exponer el circuito de la memoria a luz ultravioleta por varios minutos. Para esto este tipo de memorias suele traer un panel transparente por el cual se alumbre con luz ultravioleta para borrar el contenido.

#### EEPROM

Si bien las EPROM lograron resolver el problema de la reutilización de las memorias, el proceso para esto es muy inconveniente, complejo, lento y requiere que se remueva la EPROM de donde está conectado.
De esta problemática salieron las EEPROM, que de igual manera son EPROMs pero cuyo proceso de borrado se realiza eléctricamente.
Estas memorias tienen la capacidad de borrar cada bit en forma individual (también hay implementaciones que borran una palabra completa en cada operación de borrado).

#### Flash EEPROM

Estas memorias son unas variantes de las EEPROM que se desarrolló con el objetivo de mejorar el tiempo de borrado y habilitar su uso para aplicaciones de almacenamiento masivo.

---

## Resumen

| Memoria      | Almacenamiento | Descripción                                                                                                                     |
| ------------ | -------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| PROM         | N/E            | Memorias ROM que se pueden programar luego de su fabricación mediante la quema de fusibles internos                             |
| EPROM        | 8 Mbits        | Memorias PROM a las cuales es posible borrar el contenido mediante la exposición del chip a luz ultravioleta                    |
| EEPROM       | 128 kbits      | Memorias EPROM que es posible borrar su contenido mediante señales eléctricas. Estas pueden borrar bits específicos o palabras. |
| Flash EEPROM | 256 Gbits      | Memorias EEPROM que mejora el tiempo de borrado para almacenar aplicaciones de almacenamiento masivo.                           |
