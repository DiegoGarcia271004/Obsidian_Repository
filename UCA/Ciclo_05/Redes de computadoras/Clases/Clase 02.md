---
tags:
  - RedesDeComputadoras
---

**Internetworking:** Son los diferentes procesos para conectar redes a través de dispositivos 
**Red:** Conjunto de equipos conectados por diferentes medios.

## División de redes de datos

**Personal, PAN:** Son los dispositivos que cada persona utiliza por si mismo, podrían ser teléfonos celulares, computadoras, etc.
**Campus, CAN:** Dispositivos ubicados en una zona específica, dispositivos ubicados en una casa, en un departamento, etc.
**Local, LAN:** Dispositivos interconectados en distancias cortas. Como casas, edificios, oficinas, etc.
**Amplia, WAN:** Es la interconexión entre la red LAN y MAN...
**Metropolitana, MAN:** Cubren un área de mayor tamaño, pero deben cumplir ciertos estándares para poder mejorar la conectividad como reducción de la latencia, perdida de calidad de la señal, se utilizan para conectar ciudades.

## Topologías de red

Las topologías de red se pueden dividir en dos tipos:

**Físicas:** Se encuentran conectadas por medios físicos
**Lógicas:** Es el método que utilizan los dispositivos para acceder al medio y comunicarse entre ellos en la red.

### Topologías físicas

**Topología de bus:** Se plantea una línea principal de la cual se hacen las derivaciones para las distintas conexiones necesarias. 
Su problema radicaba en que si el cable principal fallaba o era cortado, el resto de las computadoras perdían su conexión.

**Topología de anillo:** Se generaba un anillo en el que los dispositivos se encontraban conectados entre sí. De igual forma que la topología de bus, si una de las computadoras fallaba, o una conexión entre dos computadoras fallaba, entonces el resto de las computadoras perdían conexión.

**Topología de estrella:** Es un tipo de topología en el cual todas las computadoras eran conectadas a una sola línea central, de esta manera si una de los dispositivos fallaba, el resto no presentaba problemas.

**Topología de malla:** Las computadoras se interconectaban entre sí formando diferentes conexiones, esto permitía que si una conexión fallaba, mediante la conexión con otros dispositivos podía seguir funcionando, el problema era que se generaba un gran gasto de materiales y recursos.

**Topología de árbol:** Esta distribución se basaba en la forma de árbol de la teoría de grafos, donde se tenía un dispositivo raíz que proporcionaba líneas de conexión a dispositivos conectados. Pero con el problema que si fallaba alguna conexión con la raíz, entonces todo el segmento hijo de esa conexión falla.

**Topología mixta:** Son conexiones que utilizan parcialmente o totalmente las topologías anteriores.

### Topologías lógicas

**Broadcast:** Cada host envía sus datos hacia los demás host de la red en la que se encuentra. Como podría ser el modem de una casa.

**Punto a punto:** Es la conexión directa de dos dispositivos, utilizando equipos intermedios de red, formando entre ellos un túnel virtual, donde solo ellos dos mantienen comunicación. Podrían ser conexiones como audífonos y computadoras.

**Acceso múltiple:** Los equipos comparten el mismo medio. Se utiliza la dirección MAC (Media Access Control) para poder identificarse entre si los dispositivos. Son conexiones controladas utilizando la identificación del dispositivo.

**Anillo:** Para poder enviar un mensaje en una red, los dispositivos necesitan un token, el cuál se va rotando...

---
## Dispositivos de red

Las redes en general están compuestas por 3 tipos de dispositivos de red:

**Dispositivos finales:** Son aquellos en donde se recibe la conexión de la red: Computadoras, teléfonos, impresoras, etc.

**Dispositivos intermedios:** Son aquellos por los que pasa la conexión y permite distribuirla igualmente: Routers, Switchs, etc.

**Medios de red:** Son los medios por los que la red puede pasar: Medios inalámbricos, Medios LAN, Medios WAN.