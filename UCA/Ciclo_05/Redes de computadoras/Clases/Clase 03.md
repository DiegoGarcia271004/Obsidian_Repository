---
tags:
  - "#RedesDeComputadoras"
---

# Ancho de banda

Es la cantidad de datos que se pueden transferir entre dos puntos de una red en un tiempo específico, esto se mide en bits por segundo (Bps).

El ancho de bando se encuentra limitado debido a razones físicas y tecnológicas, esto obviamente no es gratuito, si se quiere aumentar el ancho de banda, el costo aumentará.

### Cálculo de transferencia de datos

Existen dos formulas para trabajar en ese cálculo, el de mejor descarga y el de descarga típica:
- Mejor descarga $T=\frac{S}{BW}$
- Descarga típica $T=\frac{S}{P}$

Donde $BW$ es el máximo ancho de banda teórico del "enlace más lento" entre el dispositivo origen y el dispositivo destino. 
$P$ es la tasa de transferencia real en el momento de la transferencia.
$S$ es el tamaño de archivo en bits.
$T$ es el tiempo en el que se debe producir la transferencia de archivos, medido en segundos.

# Protocolos de red

Los protocolos de red son estándares que especifican el método para enviar y recibir datos entre varios ordenadores.

Los protocolos controlan los aspectos de la comunicación, como podrían ser:
- El cómo se construye la red física
- Cómo las computadoras se conectan a la red
- Como se formatean los datos para su transmisión
- Cómo se envían los datos
- Como se manejan los errores

---

# Modelo OSI

Existen algunos marcos conceptuales que permiten definir las comunicaciones entre sistemas, y entre ellos se encuentra el modelo OSI (Open Systems Interconnection). Este  define el cómo los sistemas de comunicación en red pueden interactuar entre sí. Esta fue creada por la organización internacional de normalización (ISO)para estandarizar la comunicación entre dispositivos de diferentes fabricantes.

El modelo OSI se encuentra compuesto por siete capas, cada una de estas cumple con una función específica:

1. **Capa física:** La capa física se encarga de transmitir bits a través de un medio físico, ya sean cables, fibra óptica, señales inalámbricas, etc. Algunos de estos ejemplos serían el ethernet y el wi-fi.
2. **Capa de enlace de datos (data link):** Esta capa se encarga de la comunicación entre dispositivos que se encuentran en la misma red, controlando el acceso al medio de transmisión. Esta capa esta dividida en subcapas:
	- **LLC (Logical Link Control):** Se encarga del control de errores y flujo
	- **MAC (Media Access Control):** Dirección física
	Algunos ejemplos de esta capa serían los switches.
3. **Capa de red:** Se encarga del enrutamiento y la entrega de datos entre redes diferentes; esta utiliza direcciones lógicas, como bien podrían ser las IP.
4. **Capa de transporte:**  Esta capa se encarga de administrar los datos, controla la segmentación y el reensamblado.
	Esta capa posee dos protocolos muy importantes: 
		- **TCP:** Un protocolo confiable que garantiza la entrega correcta de los paquetes de información
		- **UDP:** Es un protocolo que ofrece una mayor rapidez al momento de entregar los paquetes, con la desventaja de no garantizar la entrega completa del paquete.
5.  **Capa de sesión:** Administra y mantiene las sesiones de comunicación entre aplicaciones. Algunos ejemplos serían: Protocolos como NetBIOS y RPC
6. **Capa de presentación:** Se encarga de la codificación, del cifrado y de la comprensión de datos. Ejemplos de esta capa serían: SSL/TSL, además de formatos como lo serían JPEG y MP3.
7. **Capa de aplicación:** Esta es la capa más cercana al usuario, el cual proporciona los servicios de red a las distintas aplicaciones. Como podrían ser HTTP, FTP y SMTP.