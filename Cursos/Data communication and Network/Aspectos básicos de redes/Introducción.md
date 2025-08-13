# Concepto de comunicación de redes

**Comunicación:** Es el intercambio de información entre personas y cosas.
**Comunicación de redes:** Es la comunicación entre dispositivos terminales mediante una red de computadoras.

Como algunos ejemplos de comunicación de redes, podría ser una computadora descargando información desde otra computadora. O desde un dispositivo descargando información desde la red (que a su vez esta conectado a un servidor), o también computadoras compartiendo información entre sí mediante la conexión a un router.

## Proceso de transferencia de información

Podemos hacer un símil entre la transferencia de información en una red informática con el proceso de transferencia de un paquete en la vida real:

Usualmente si queremos hacer el envío de un pedido, primeramente tomamos qué es lo que queremos enviar, lo empaquetamos, lo mandamos al centro de distribución, mediante una ruta (podría ser terrestre, aérea o acuática) llega al destino llevando al centro de distribución del destino y es aquí donde el paquete es enviado al destinatario.

De igual forma, al comunicarnos mediante una red, nuestro dispositivo genera la información que vamos a enviar, lo almacena en paquetes de datos y es enviada por nuestro router hacia la red, que hace llegar estos paquetes de datos al router del destino y este último provee los datos necesarios a nuestro destinatario.

## Términos comúnmente utilizados

- Dispositivos terminales: Son dispositivos que representan el fin de un sistema de comunicación, como lo podrían ser las computadoras, celulares, entre otros.
- Routers: Dispositivo de red que selecciona y dirige los paquetes a su destino.
- Gateway: Dispositivo de red que provee funciones como la conversión de protocolos, selección de rutas, y cambio de datos.
- Encapsulación: Proceso mediante el cual se le agrega un encabezado y una cola a un payload para formar un nuevo paquete.
- Des encapsulación: Proceso por el cual se remueve el encabezado y la cola del paquete para extraer la información.
- Cola: Segmento de información agregado después de la creación del payload.
- Encabezado: Segmento de información agregado antes de la creación del payload.
- Paquete: Unidad de datos transmitida a la red.
- Payload: información transmitida.


# Concepto de red de comunicación de datos

Una red de comunicación de datos consiste en una serie de dispositivos terminales conectados entre si para poder transmitir información entre ellos, es decir, que el objetivo de la red de comunicación de datos es (redundantemente) implementar la comunicación de datos.

## Dispositivos usados en una red

- **Switches:** Son los dispositivos más cercanos a los usuarios finales, proporciona acceso de red a las terminales.
- **Routers:** Son dispositivos de red que redirigen los paquetes de información en el internet. Una vez recibido un paquete, el router verifica hacia donde es mandado y lo redirige a dicha dirección.
- **Firewalls:** Son dispositivos de seguridad de la red usados para asegurar la seguridad de la comunicación entre dos redes. Monitorea, restringe y modifica el flujo de datos que pasan por el para resguardar información, estructura y estados de redes internas de la red externa.