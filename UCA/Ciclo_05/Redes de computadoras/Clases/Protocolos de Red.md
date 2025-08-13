---
tags:
  - RedesDeComputadoras
---
# RS-232 (Transmisión por señales eléctricas [60])

Desarrollado por la TIA en 1960, RS-232 es un estándar de comunicación que define la transmisión de los datos entre dispositivos electrónicos a través de señales eléctricas y una comunicación bit a bit.

Este protocolo sigue siendo usado en ciertas industrias, pero por la existencia de otras tecnologías más avanzadas como USB o Ethernet este ha sido reemplazado, pero aún es utilizado el equipos médicos, instrumentación y control industrial.

Este fue uno de los primeros estándares para la comunicación en serie y no fue basado en un protocolo anterior, pero con el tiempo fueron apareciendo mejoras a este protocolo.
# RJ45 (Conexiones de red [70])

El conector RJ45 se le conoce comercialmente como conector ethernet o conector RJ45, cuyo desarrollo fue encabezado por la AT&T en 1970 para las interfaces telefónicas, con el tiempo se expandieron para abarcar también la transmisión de datos.

Estos conectores fueron introducidos en 1960 con el fin de sustituir los voluminosos conectores telefónicos, con el tiempo estos conectores se ampliaron para incluir la comunicación de datos, con el paso del tiempo estos conectores se volvieron más utilizados para conectar un dispositivo con acceso a internet con otro dispositivo de red.

El conector en la actualidad sigue en vigencia y es ampliamente utilizado en redes de computadoras, telecomunicaciones, centros de datos, etc.

Las conexiones RJ45 vinieron a reemplazar otros tipos de conexiones que se usaban hasta el momento, como el conector RJ11, conectores coaxiales, conector DB-15.

# ATM (Celdas [80])

El protocolo ATM (Asynchronous Transfer Mode) es una tecnología de transferencia de datos diseñada para la transmisión de voz, video y datos en una misma red de alta velocidad.

Desarrollada por la ITU-T en la década de 1980 y conforme el paso de los años se fue desarrollando. Este desarrollo fue impulsado por la necesidad de una tecnología que transportara el trafico de datos y de voz de una manera eficiente en redes de alta velocidad, ya en los años 90 se adoptó este protocolo como base para las redes de banda ancha.

El protocolo ATM sigue siendo utilizado en la actualidad, aún si su uso se ha visto reducido en gran medida debido a las nuevas tecnologías se sigue utilizando en algunas redes de comunicación antigua, cajeros automáticos y algunas aplicaciones gubernamentales y militares.

La comunicación de este protocolo se basa en el envió de **celdas** (paquetes de datos de 53 bytes) que poseen información de donde vienen y a donde deben ir mediante un identificador llamado VPI, una vez llegada la información a su destino, esta se reconstruye para formar la información original.

**Este protocolo no fue una mejora de otro protocolo directo**, más fue desarrollado como una tecnología diseñada para unificar redes informáticas y de telecomunicaciones, gestionando el tráfico de datos digitales y la comunicación de voz.

Como se mencionó anteriormente, este protocolo utiliza paquetes de tamaño fijo para la transmisión de datos llamados celdas; con el fin de minimizar la latencia de la transmisión de datos.
Originalmente, el protocolo ATM buscaba ser el futuro de internet (es decir volverse la base de todas las telecomunicaciones). Sin embargo fue superado por IP y Ethernet, ya que eran más flexibles y económicos.

## Resumen

El protocolo ATM, desarrollado por el ITU-T en la década de los 80 es una tecnología de transferencia de datos diseñada para la transmisión eficiente de información de audio, y video en redes de alta velocidad. Se basa en el modelo de descomponer la información, transferir paquetes de datos con tamaño fijo llamados celdas y una vez en el destino, la información es reconstruida. Se diseñó para ser la base de todas las telecomunicaciones, pero fue superada por tecnologías como IP y Ethernet.

# MAC/LLC (Acceso y control lógico [83])

MAC o Media Access Control y LLC Logical Link Control son subcapas del modelo IEEE 802 dentro de la capa de enlace de datos del modelo OSI, al igual que el 802.11, fue desarrollado por la IEEE que formaron conjuntos de estándares utilizados en redes como Ethernet y WiFi en 1980 para LLC y 1983 para MAC.

La subcapa MAC se encarga del acceso al medio y a la identificación de dispositivos mediante direcciones MAC, además de definir como los dispositivos compiten por el acceso al canal de comunicación.

La subcapa LLC proporciona un control lógico sobre el enlace de datos, encargándose del multiplexado de protocolos superiores además de implementar el control de flujo y la detección de errores opcionalmente.

A día de hoy sigue siendo vigente, aunque la subcapa LLC ha caído en desuso en el Ethernet moderno, MAC sigue siendo crucial en redes cableadas e inalámbricas.

Tanto MAC como LLC mejoraron el concepto de control de acceso al medio que existía en tecnologías como ALOHA y Token Ring.
LLC fue basado en X.25 y MAC evolucionó con mejoras como CSMA/CD.

## Resumen 

Tanto MAC como LLC son subcapas del modelo IEEE 802.2 en la capa de enlace de datos del modelo OSI, desarrollados por la IEEE en 1980 y 1983. MAC se encarga del acceso al medio por parte de los dispositivos  y LLC del control lógico sobre los enlaces de datos. MAC sigue siendo vigente en las conexiones cableadas, mientras que LLC ha sido descontinuado en los Ethernet actuales. LLC y MAC son mejoras basadas en X.25 y CSMA/CD respectivamente.
# FC (Alta velocidad de datos [88])

FC o Fiber Chanel (nombre en el mercado) es el nombre general de un set de estándares que fue desarrollado por el instituto Nacional Estadounidense de Estándares (ANSI por sus siglas en ingles) en el año de 1988, este protocolo comenzó a desarrollarse y en 1994 ANSI estableció el primer estándar FC. A día de hoy sigue siendo una opción muy utilizada en entornos de manejo de datos que buscan baja latencia, alta fiabilidad y seguridad.

FC es un protocolo de transmisión de información de alta velocidad, su creación está ligada a mejorar el rendimiento en redes de almacenamiento SAN, específicamente se especializa en la conexión de servidores, almacenamiento y redes de datos en entornos de misión crítica.

FC se diseñó como una mejora para protocolos anteriores, principalmente el protocolo SCSI buscando ofrecer una mayor velocidad, confiabilidad y escalabilidad en entornos de almacenamiento empresarial.

## Resumen

El protocolo FC o Fiber Chanel en el mercado son un set de estándares desarrollados por la ANSI en 1988, hasta el establecimiento formal en 1994. A día de hoy es muy utilizado en entornos de manejo de datos que buscan velocidad, eficiencia y baja latencia. Consiste en una serie de estándares de transmisión de datos a alta velocidad, su funcionamiento está ligada a la mejora de redes SAN, centrándose en conexión de servidores, almacenamiento y redes de datos. Se desarrollo como una mejora al protocolo SCSI buscando ofrecer mayor confiabilidad, eficiencia y escalabilidad en entornos. Utiliza tanto alambre de cobre como fibra óptica.

# SDH (Altas velocidades en fibra [88])

SDH el cual tiene una contraparte comercial SONET es un estándar desarrollado por la ITU-T en 1988 con el objetivo de mejorar la interoperabilidad entre diferentes fabricantes y redes de telecomunicaciones a nivel mundial. 

SDH es un conjunto de protocolos de transmisión de datos diseñado para la transmisión de información a altas velocidades en redes de fibra óptica.

SDH surgió como una evolución de PDH, abordando sus limitaciones y mejorando la eficiencia y flexibilidad en las telecomunicaciones, combatiendo las limitaciones de este, como la complejidad en la extracción de señales, problemas de sincronización y las capacidades limitadas de supervisión y gestión .

Aunque SDH se siga utilizando en algunas redes, en la actualidad se ve gradualmente reemplazado por tecnologías más modernas como las redes IP y Ethernet, DWDM (O su mejora CWDM) y OTN.
# DSL (Líneas partidas [80-90])

El protocolo DSL o conocido comercialmente como Digital Subscriber Line fue creado a finales de los años 80 y a inicios de los 90 por las compañías AT&T, General Telephone Electronics e International Telecommunication Union. Este protocolo tuvo una vigencia desde su creación (inicios de los 90) hasta aproximadamente el año 2010.

Este protocolo está basado en la transmisión de señales telefónicas a través de cables de cobre. Consiste en separar las señales que provienen de la línea en líneas más bajas (que se utilizan para las redes telefónicas) y otras más altas (utilizadas para la conexión a internet); Al realizar esta separación de las líneas permite realizar llamadas por teléfono y mantener una conexión a internet a la vez.

DSL mejoró el protocolo POTS y dial-up, lo que permitió transmitir datos a alta velocidad sin interrumpir la comunicación telefónica, al contrario de dial-up, que utilizaba módems analógicos pero su velocidad aún se veía limitada y dependía de la calidad de la línea telefónica.

## Resumen

El protocolo DSL, comercialmente conocido como Digital Subscriber Line creado a finales de los 80s y a inicios de los 90s por las compañías AT&T, General Telephone Electronics e International Telecommunication Union, y tuvo una vigencia desde su creación hasta el año 2010. Consistía en un estándar de transmisión de señales telefónicas a través de cables de cobre, separando la línea original para permitir la utilización del teléfono y el internet a la vez. Este protocolo es mejora del protocolo POTS y dial-up, que utilizaba módems analógicos y la velocidad de la navegación se veía limitada por la calidad de la línea telefónica.

# Frame Relay (tramas [90])

Es una tecnología de transmisión de datos, comercialmente utiliza el mismo nombre. Este protocolo creado en 1990 (aunque su desarrollo comenzó en la década de los 80) fue desarrollado por la TIA y la ANSI en conjunto con otras empresas del sector de telecomunicaciones.

Como se mencionó, Frame Relay es un protocolo de red utilizado para la transmisión de datos entre dispositivos a través de un sistema de conmutación de paquetes llamados **frames** (o tramas), lo que define un método económico para la transmisión de los datos sobre redes de área amplia (WAN), como lo serían redes telefónicas o redes de fibra óptica.
Frame Relay fue utilizado ampliamente en las décadas de 1990 y a principios de los 2000. Pero debido a la aparición de tecnologías más avanzadas, fue reemplazado.

Frame Relay puede considerarse como la mejora de algunos protocolos más antiguos como X.25, los dos se encuentran diseñados para la transmisión de datos a través de redes de conmutación de paquetes, pero Frame Relay posee mayor eficiencia y menores costos de implementación.

## Resumen

Frame Relay es una tecnología desarrollada para la transmisión de datos en área amplia (WAN), creado en 1990 pero desarrollado en la década de los 80s por ANSI y TIA en conjunto con otras empresas de telecomunicaciones. Se basa en la transmisión de datos mediante paquetes llamados tramas. Fue ampliamente utilizado en la década de los 90s y a inicios de los 2000, siendo reemplazado por tecnologías más avanzadas. Frame Relay es la mejora de otros protocolos como lo podría ser X.25, ya que posee mayor eficiencia al momento de la transmisión de datos y un menor costo en la implementación.

# irDA (Infrarrojo [93])

La transmisión de datos por infrarrojo irDA es un protocolo desarrollado en 1993 por más de 50 organizaciones entre las cuales se puede destacar a HP e IBM.

irDA es un estándar de comunicación inalámbrica que permite la transferencia de datos mediante el uso de infrarrojos entre distintos dispositivos electrónicos, se desarrollo con el objetivo de estandarizar la comunicación entre dispositivos sin la necesidad de cables.

Este protocolo fue bastante popular a finales de los 90 y a inicios de los 2000, hasta ser descontinuado por protocolos que no utilizaban medios físicos, como el bluetooth y WiFi, aunque aún es utilizado en algunos ambientes con interferencias que inutilizan los protocolo inalámbricos.

En si mismo, irDA no es una mejora de otro protocolo, sino que surgió como un alternativa inalámbrica a las conexiones por cable utilizadas en computadoras y dispositivos.

## Resumen

irDA es un protocolo que se basa en la transmisión de datos mediante infrarrojos, desarrollada en 1993 por más de 50 organizaciones, resaltando HP e IBM. Si bien fue popular en su momento, así mismo fue descontinuada por otras tecnologías que no utilizan medios físicos.
# 100Base-TX (Doble cable trenzado [95])

Este protocolo es un estándar de Ethernet, el cual consiste en **transmitir datos a través de dos pares de cables trenzados** (uno para cada dirección) este proporciona un funcionamiento **full-duplex** con un rendimiento de 100 Mbits/s en cada dirección.

Fue desarrollado por el **IEEE en 1995**. 
Este protocolo es una parte de la familia 100BASE-T que comprende diversos estándares de Fast Ethernet para cables de par trenzado.

Originalmente, con la conexión coaxial, solo una de las computadoras conectadas podía enviar información a la vez; Con la implementación de este protocolo, **se logró que ambas pudieran transmitir información, aumentando la velocidad de las redes y evitando la colisión de datos en las redes.**

El protocolo 100Base-TX son basados de los sistemas 10Base-T,  permitiendo agregar modificaciones sencillas y actualizaciones desde el protocolo anterior.

A día de hoy sigue siendo usado en todo el mundo, mayormente en dispositivos con redes antiguas.

La terminación TX significa que trabaja con un cable UTP CAT5 de conexión directa que utiliza dos de los 4 pares disponibles, admitiendo velocidades de hasta 100Mb con una conexión máxima de 100 m.
La configuración de las redes de 100Base-TX son similares a las de su protocolo base, al utilizarse en redes locales, los dispositivos se conectan a un hub o switch mediante una topología de estrella.

## Resumen

El protocolo 100Base-TX es un estándar de conexión ethernet (mediante cables trenzados) con dos cables, cada uno para una de las direcciones que permite mayor velocidad y menor colisión de datos. Fue desarrollado por el IEEE en 1995. Se baso en el protocolo 10Base-T, siendo una especie de incorporación a este protocolo. Su terminación TX significa la utilización de cables UTP de categoría 5 con una longitud máxima de 100 m y mínima de 2.5 m. Los dispositivos que utilizan este protocolo se encuentran en una distribución de estrella.

# IEEE 802.11 (Normas de conexión inalámbrica [97])

El protocolo 802.11 o también conocido como IEEE 802.11 es un protocolo que engloba diversas normas WLAN que son utilizadas en la mayoría de  dispositivos con la capacidad de conexión, este fue desarrollado por la IEEE en 1997.

Este protocolo (como se dijo ya) es un conjunto de normas orientado a las redes inalámbricas, definiendo como los dispositivos inalámbricos pueden comunicarse en la red local, este es especificado en en la capa física (y subcapa MAC) del modelo OSI, además de trabajar con frecuencias de 2.4 a 5 GHz, esta define mecanismos de modulación, encriptación, autenticación y control de acceso al medio para mejorar la eficiencia y la seguridad.

A día de hoy es la tecnología más usada y conocida para las redes inalámbricas, todo gracias a su constante actualización tras los años.

El protocolo 802.11 es una mejora al protocolo WaveLan que utilizaba frecuencias menores al protocolo, permitía una velocidad aceptable pero carecía de los mecanismos de seguridad y modulación eficiente del 802.11.

## Resumen

IEEE 802.11 es un protocolo es un protocolo que engloba diversas normas WLAN, desarrollado por la IEEE en 1997. A día de hoy sigue siendo muy utilizado en todos los dispositivos que trabajen con conexión inalámbrica. Este protocolo se especifica en la capa física del modelo OSI, utilizando frecuencias entre 2.4 y 5 GHz, además de definir mecanismos de modulación y seguridad para los dispositivos.

# OTN (Transporte en fibra [2001])

Optical Transport Network (OTN) fue desarrollado por la ITU-T en 2001 donde su primera edición fue aprobada. 

OTN es una tecnología de red óptica diseñada para proporcionar un marco eficiente y estandarizado para el transporte de datos a través de redes de fibra óptica, estas se componen de varias capas jerárquicas que facilitan la transmisión, multiplexación, enrutamiento y monitoreo de señales digitales.

Este protocolo a día de hoy sigue siendo vigente y en constante evolución, lo que le ha permitido adaptarse a las necesidades crecientes de las redes de comunicaciones.

El protocolo OTN se considera la evolución del tradicional SDH/SONET, introduciendo mayor eficiencia en el uso del ancho de banda.
## Resumen

El protocolo OTN es una tecnología de red óptica diseñada por la UIT-T en 2001, que permite proporcionar un marco eficiente para el transporte de datos a través de la fibra óptica, componiéndose en diferentes capas jerárquicas que facilitan trabajar con estas señales. Este protocolo es considerado la evolución de SDH/SONET.
# CWDM (Longitudes de onda variables [2002])

El protocolo CWDM es una tecnología de multiplexación por división de longitud de onda, esta es utilizada en redes de fibra óptica para aumentar la capacidad de transmisión sin la necesidad de agregar más fibras físicas.

Fue desarrollada por la ITU-T en el año 2002.
Actualmente se sigue utilizando en las redes de telecomunicaciones, especialmente en redes metropolitanas y de acceso, este protocolo es una alternativa más económica y eficiente para medianas y cortas distancias en comparación con el protocolo DWDM.

Como se mencionó anteriormente, este protocolo es una técnica de multiplexación por división de longitudes de onda de la información que pasa por la fibra óptica con el fin de transmitir mayor cantidad de datos sin la necesidad de utilizar más fibras, lográndose mediante el envío de señales a través de la misma fibra con distintas longitudes de onda que van desde los **1270nm hasta los 1610 nm**.

Si bien este protocolo no es una mejora como tal, es una versión más económica y con menor complejidad en comparación con DWDM, que este permite estrechar el espaciado entre los canales y permite enviar mayor cantidad de señales en la misma fibra con el costo del aumento de precio.

## Resumen

El protocolo CWDM es una tecnología de multiplexación de la fibra óptica creado en 2002, su funcionamiento es basado en enviar diversas señales a través de la misma fibra óptica cambiando la longitud de onda de estas señales, las cuales van desde los 1270nm hasta los 1610nm. Si bien no es una mejora de otro protocolo, es una opción más económica al protocolo DWDM.


# HDP (Optimización de transferencias [2010])

High-performance Distributed Protocol o por sus siglas HDP es un protocolo desarrollado por un equipo de investigadores asociados al campo de las redes distribuidas (no se le conoce alguna institución específica) fue desarrollado a principios de la década de 2010.

El protocolo HDP está diseñado para la optimización de la transferencia de datos en redes distribuidas, lo que minimiza la latencia y maximiza el ancho de banda disponible.
A día de hoy sigue siendo relevante en aplicaciones que requieren comunicación de alto rendimiento en sistemas distribuidos, especialmente en los entornos del big data.

Este protocolo se puede considerar como una mejora de los protocolos como TCP/IP en cuanto a términos de rendimiento y eficiencia en entornos distribuidos.

## Resumen

El protocolo HDP es un protocolo desarrollado por un equipo de investigadores relacionados al campo de las redes distribuidas a inicios de la década de 2010. Consistiendo en la optimización de la transferencia de datos buscando minimizar la latencia y maximizar el ancho de banda. Puede considerarse una mejora del protocolo TCP/IP en términos de rendimiento y eficiencia.

