
## Cables Coaxiales

Con respecto a los cables coaxiales, estos tienen mayor blindaje y un mayor ancho de banda en comparación con aquellos pares trenzados sin blindaje.
De estos tienen diversos tipos, de los más usados podemos encontrar:
- De 50 ohms y 75 ohms
Estos tienen una buena combinación de un alto ancho de banda y una excelente inmunidad al ruido, además de resistir bastante bien a la intemperie.

Existen distintos tipos de cable coaxial, y cada uno se utiliza en aplicaciones distintas

| Tipo     | Aplicaciones                                                                                     | Longitud ideal                      |
| -------- | ------------------------------------------------------------------------------------------------ | ----------------------------------- |
| RG-6     | Son cables usualmente utilizados en las conexiones de televisión, internet y antenas satelitáles | Hasta 100 m para evitar pérdidas    |
| RG-11    | Conexiones ideales para largas distancias debido a su poca pérdida de información                | Más de 100 m, ideal para exteriores |
| RG-59    | Sistemas de cámaras y televisión analógica                                                       | Menos de 30 m para mayor calidad    |
| Triaxial | Mejora la protección contra interferencias agregando una capa más de blindaje                    | Depende de la aplicación            |
| Flexible | Utilizado en aplicaciones móviles o donde se necesite flexibilidad                               | Menos de 10 m                       |

## Pares trenzados

Los cables por pares trenzados constan de dos cables de cobre aislados por lo general de 1mm de grosor. Estos se encuentran trenzados entre sí; esto debido a que un solo cable generaría por si solo una antena, que a su vez generaría un [[Campos eléctricos|campo eléctrico]] que generaría interferencia con la transferencia de datos, por esto mismo al trenzarse entre sí, sus campos magnéticos se anulan entre sí.
Estos cables pueden recorrer varias distancias sin la necesidad de amplificación, pero en distancias mayores ya es requerido el uso de repetidores.

Los cables de par trenzado tienen distintos enlaces:
**Full-Duplex:** Estas pueden ser utilizadas en ambas direcciones al mismo tiempo. (El protocolo de red [[Protocolos de Red#100Base-TX (Doble cable trenzado [95])|100Base-TX]] utiliza este tipo de enlace)
**Half-Duplex:** Los enlaces de igual forma que el full-duplex puede utilizarse en ambas direcciones, con la diferencia que solo se puede una a la vez.
**Simplex:** Solo permite el tráfico de información en una sola dirección.

Estos pueden tener dos tipos de cables:

**Cables planos:** Los cables RJ-45 se utilizan para conectar dispositivos de tipos diferentes, se engastan en cada extremo siguiendo cualquiera de los estándares (568A o 568B) los dos extremos se deben montar siguiendo el mismo estándar.

**Cables cruzados:** Se utilizan para conectar dispositivos del mismo tipo. Para realizar esto, cada extremo del cable deberá de tener un estándar distinto, al hacer esto, se obtiene un cable cruzado. Estas conexiones se utilizan para conectar dos dispositivos sin necesidad de un concentrador de cableado intermedio o cableado troncal.

## Fibra óptica 

Es el medio de transporte más novedoso en los últimos tiempos, su uso se está masificando, reemplazando a los cables coaxiales y a los pares trenzados. A día de hoy se pueden ver siendo utilizados en las televisiones por cable y la telefonía.

Mediante la fibra óptica, los datos se transmiten mediante un haz de luz confinado de naturaleza óptica, esto lo hace más caro y más difícil de manejar, pero ofrece una mayor ventaja frente a otros medios, haciéndolo una mucho mejor opción al momento de observar rendimiento y transporte de datos.

Los cables de fibra óptica suelen estar formados por finas fibras de vidrio o plástico; un revestimiento de cristal con propiedades ópticas diferentes a las del núcleo, cada fibra está rodeada por su propio revestimiento para protegerla del entorno.

$$
\begin{gather*}
\int \frac{1}{1+\tan x} \, dx \\
\int \frac{1}{1+\frac{\sin x}{\cos x}} \, dx\\
\int \frac{\cos x}{\cos x+\sin x} \, dx\\
\int \frac{\cos x+\sin x-\sin x}{\cos x+\sin x} \, dx \\
\int 1-\frac{\sin x}{\cos x+\sin x} \, dx\\
x-\int \frac{\sin x}{\cos x+\sin x}\cdot \frac{(\cos x-\sin x)}{(\cos x-\sin x)} \, dx\\
x-\int \frac{\sin x\cos x-\sin ^{2}x}{\cos ^{2}x-\sin ^{2}x} \, dx \\
x-\int 2\frac{\sin(2x)}{\cos(2x)} \, dx +\int \frac{\sin ^{2}x}{\cos 2x} \, dx\\
x-2\int \tan 2x \, dx +\int \frac{1-\cos ^{2} x}{\cos 2x} \, dx\\
x-\sec ^{2}2x
\end{gather*}
$$$$
\begin{gather*}
\int \frac{1}{1+\tan x} \, dx \\
\int \frac{1}{1+\tan x}\cdot \frac{1-\tan x}{1-\tan x} \, dx\\
\int \frac{1-\tan x}{1-\tan ^{2}x} \, dx \\
\int \frac{1-\tan x}{1-(\sec ^{2}x-1)} \, dx\\
\int \frac{1-\tan x}{2-\sec ^{2}} \, dx 
\end{gather*}
$$