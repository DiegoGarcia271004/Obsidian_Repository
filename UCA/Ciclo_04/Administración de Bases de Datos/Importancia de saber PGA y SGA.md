---
tags:
  - Abd
---
## Importancia de conocer el funcionamiento de la memoria PGA y SGA

Anteriormente hemos podido observar como la PGA y SGA son formas de almacenamiento en las bases de datos de Oracle. Sin embargo, existe una gran importancia en el porque es necesario conocer acerca de estos temas.

Al saber como utilizar estos tipos de almacenamiento, permite llegar a ser mucho más eficiente con el sistema además de mejorar el rendimiento del sistema.
Por ejemplo, si se conoce bien el funcionamiento del almacenamiento SGA, es posible poder mejorar la velocidad de acceso a los datos, a su vez se puede evitar algunas operaciones redundantes como algunas lecturas repetitivas del disco, o algunos bloques de datos que se descargan y se recargan frecuentemente.

A su vez, si no se maneja de manera adecuada, una memoria PGA insuficiente podría generar algunos problemas que conlleven operaciones de disco innecesarias. Por ejemplo, si el PGA no posee suficiente memoria para realizar algunas tareas de ordenación, unión o agrupamiento, estos datos se desbordan a la Tablespace temporal, lo que genera escritura en el disco, lo que puede llevar a ralentizar procesos de consulta, ya que es más lento realizar acceso al disco que el acceso a memoria.

De igual forma, si el administrador de la base de datos conoce como la memoria PGA y SGA funcionan, entonces podrá realizar ajustes necesarios para evitar problemas de agotamiento de memoria y fallos de rendimiento. Además, con la correcta configuración, permite manejar la carga creciente de información sin la degradación del propio servicio, permitiendo la escalabilidad y la adaptabilidad.

## Obtención de información

En el internet es posible encontrar mucha información acerca de qué es y como trabajar con la memoria PGA y SGA, para esta investigación nuestra principal fuente fue la documentación proporcionada por Oracle donde explicaba su funcionamiento y la importancia de esta memoria, además del centro de conocimiento en la página web de Amazon Web Services. A su vez se utilizaron diversos tutoriales y explicaciones en formato de video acerca de los temas.

## Conclusiones

A lo largo de esta presentación hemos podido aprender acerca de las memorias PGA y SGA. Pero, un administrador de bases de datos ¿Qué debería hacer con esta información?

Un administrador debe **conocer** en profundidad el funcionamiento de las memorias PGA (Program Global Area) y SGA (System Global Area), entendiendo su papel fundamental en la gestión y optimización del rendimiento al trabajar con bases de datos. Este conocimiento es clave para garantizar un desempeño adecuado en sistemas complejos.

Además, es crucial que el administrador **comprenda** las implicaciones de una correcta configuración y monitoreo de estas memorias. Una gestión inadecuada podría derivar en inestabilidad, bajo rendimiento o incluso fallos críticos en el sistema.

Por último, el administrador debe **investigar y aplicar** estrategias prácticas basadas en los conocimientos obtenidos, asegurándose de implementar soluciones que maximicen la eficiencia y aseguren la continuidad operativa del sistema de base de datos.