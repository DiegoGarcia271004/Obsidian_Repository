---
tags:
  - EMA
---
A continuación se hará un resumen de todos los temas y un repaso de las fórmulas que se utilizan para la resolución de los ejercicios, las cuales serán señaladas al estas ser encerradas en cajas.

---

## Energía potencial eléctrica

Si recordamos los temas sobre [[Energía potencial|la energía potencial]], entonces podemos encontrar una similitud entre la energía potencial gravitatoria y la energía potencial eléctrica.
Para la [[Energía potencial#Energía potencial gravitatoria|energía potencial gravitatoria]] decíamos que al momento de levantar un objeto, realizábamos un trabajo sobre este objeto, y el objeto almacenaba energía potencial gravitatoria conforme se elevaba para luego, al soltarlo, esa energía potencial se convertía en [[Trabajo y energía cinética#Energía cinética|energía cinética]], lo que generaba un desplazamiento. De igual manera, sabemos que las cargas ejercen una fuerza sobre otras cargas, que al momento de acercar una carga a otra, esta puede generar una fuerza de atracción mayor dependiendo de su distancia a esta, por lo que podemos llegar a una expresión de energía potencial que dependa de la fuerza eléctrica entre cargas:

Primeramente recordemos la fuerza que se genera entre dos cargas gracias a la [[Ley de Coulomb]]:
$$
\vec{F}=\frac{1}{4\pi\varepsilon_{0}} \frac{qq_{0}}{r^{2}}
$$
Con esto en cuenta, recordemos la definición de [[Trabajo y energía cinética#Trabajo y energía con fuerza variable|trabajo]] como la integral de una función de fuerza: 
$$
W=\int _{a}^{b} F(x) \, dx 
$$

En este caso nuestro $dx$ sería un diferencial de distancia entre las cargas, es decir un $dr$:
$$
\begin{align*}
W&=\int_{r_{1}}^{r_{2}} F \, dr\\
&=\int_{r_{1}}^{r_{2}} \frac{1}{4\pi\varepsilon_{0}} \frac{qq_{0}}{r^{2}}  \, dr \\
&=\frac{qq_{0}}{4\pi\varepsilon_{0}}\int _{r_{1}}^{r_{2}} \frac{1}{r^{2}} \, dr\\
&=\frac{qq_{0}}{4\pi\varepsilon_{0}}\left( \frac{1}{r_{1}}-\frac{1}{r_{2}} \right) 
\end{align*}
$$
Ya con esta expresión, sabemos que el trabajo es igual a la diferencia de energía potencial del sistema, y también sabemos que para que una variación se de, entonces debe ir del punto final menos el inicial, por lo que:
$$
\begin{align*}
W&=\frac{qq_{0}}{4\pi\varepsilon_{0}}\left( \frac{1}{r_{1}}-\frac{1}{r_{2}} \right)\\
&=-\frac{qq_{0}}{4\pi\varepsilon_{0}}\left( \frac{1}{r_{2}}-\frac{1}{r_{1}} \right)\\
W&=-\Delta U\\
\Delta U&=\frac{qq_{0}}{4\pi\varepsilon_{0}}\left( \frac{1}{r_{1}}-\frac{1}{r_{2}} \right)\\
-\Delta U&=\frac{qq_{0}}{4\pi\varepsilon_{0}}\left( \frac{1}{r_{2}}-\frac{1}{r_{1}} \right)
\end{align*}

$$
Y ya que la variación de la energía potencial eléctrica es una diferencia, podemos decir que la energía potencial eléctrica a una distancia $r$ entre dos cargas es de:
$$
\boxed{U=\frac{1}{4\pi\varepsilon_{0}} \frac{qq_{0}}{r}}
$$
Ahora, si se quiere tener la energía potencial total entre una carga $q_{0}$ y un conjunto de cargas $q_{i}$
a una distancia $r_{i}$:
$$
\boxed{U_{total}=\frac{q_{0}}{4\pi\varepsilon_{0}} \sum_{i} \frac{q_{i}}{r_{i}}}
$$

### Aclaración post-parcial

Quizás no fue mencionada durante la realización de este resumen. Sin embargo, se puede buscar el valor de la energía potencial eléctrica entre un conjunto de partículas, siendo este la combinación de todas las posibles energías potenciales que se encuentran entre ellas:
$$
\boxed{U_{total}=\frac{1}{4\pi\varepsilon_{0}}\sum_{i<j} \frac{q_{i}q_{j}}{r_{ij}}}
$$


---
## Potencial eléctrico

Anteriormente se estudió la energía potencial eléctrica sobre la carga de prueba $q_{0}$, pero, ¿Qué pasa si queremos encontrar la energía potencial para cada unidad de carga?, pues el potencial eléctrico es quien nos da este valor, siendo que el potencial eléctrico es la energía potencial por unidad de carga:
$$
\boxed{V=\frac{U}{q_{0}}=\frac{1}{4\pi\varepsilon_{0}} \frac{q}{r}}
$$
Sin embargo, de por si el potencial no nos da mucha información, sino que al igual que la energía potencial gravitatoria nos interesa su diferencia, a esta diferencia se le conoce como voltaje:
$$
\Delta V=V_{a}-V_{b}
$$
Esto sale a partir de nuestra expresión del trabajo:
$$
\begin{align*}
W_{a\to b}&=U_{a}-U_{b}\\
\frac{W_{a\to b}}{q_{0}}&=\frac{U_{a}-U_{b}}{q_{0}}\\
\frac{W_{a\to b}}{q_{0}}&=V_{a}-V_{b}=\Delta V=V_{ab}\\
&\boxed{\Delta V=V_{ab}=\frac{W_{a\to b}}{q_{0}}}
\end{align*}
$$
Esto explica que el voltaje (o la variación de potencial) es el trabajo requerido para mover una unidad de carga desde el punto $b$ hasta el punto $a$ **en contra** de la fuerza eléctrica.

### Cálculo de potencial

En la sección de energía potencial eléctrica encontramos diferentes formas de encontrar la energía potencial de las cargas, por lo que podemos utilizar estas con nuestro nuevo conocimiento acerca del potencial para utilizarlas como herramientas:

En esta sección encontramos como calcular el potencial eléctrico contra otra partícula, pero si queremos encontrar el potencial para diversas cargas, tenemos que encontrar el potencial desde un punto contra el resto de las cargas $q_{i}$ a una distancia $r_{i}$:
$$
\boxed{V_{total}=\frac{1}{4\pi\varepsilon_{0}}\sum_{i} \frac{q_{i}}{r_{i}}}
$$
Y como sabemos, si tenemos una sumatoria... ¡¡¡tenemos una integral!!! Así que para una distribución continua de carga, si queremos encontrar el voltaje tenemos que dividir la carga en diversos pedazos de carga $dq$ y sumarlos todos:
$$
\boxed{V=\frac{1}{4\pi\varepsilon_{0}}\int \frac{dq}{r} }
$$
Pero al trabajar con el potencial, tenemos que mencionar que el potencial es una magnitud *escalar*, así que al obtener el potencial de una distribución continua de carga, no se vaya a confundir eliminando componentes como si se hacia en el cálculo del campo eléctrico.

También es posible encontrar el **voltaje** (hoy si hablamos de la diferencia de potencial) utilizando el campo eléctrico.

Recordando:
$$
\begin{align*}
W_{a\to b}&=\int_{a}^{b} \vec{F}\cdot \, dl\\
&=\int _{a}^{b}q_{0}\vec{E}\cdot \, dl  
\end{align*}
$$
Pero también conocemos que el voltaje es el trabajo por unidad de carga, entonces:
$$
\begin{align*}
&-\Delta V=\frac{W_{a\to b}}{q_{0}}\\
&\boxed{V_{a}-V_{b}=\int _{a}^{b}\vec{E}\cdot \, dl =\int _{a}^{b}E\cos \theta \, dl }
\end{align*}
$$

#### Ejemplos

1) Una carga eléctrica positiva Q está distribuida de manera uniforme a lo largo de una línea de longitud $2y$ que se encuentra a lo largo del eje y, entre y = $-y$ y y = $+y$. Determine el potencial eléctrico en el punto P sobre el eje x a una distancia x del origen.

![[Potencial en alambre|center]]
$$
\begin{align*}
V&=\int \frac{1}{4\pi\varepsilon_{0}} \frac{dq}{r} \\
r&=\sqrt{ x^{2}+y^{2} }\\
dq&=\lambda dy\\
\\
V&=\frac{\lambda}{4\pi\varepsilon_{0}}\int _{-y}^{y} \frac{1}{\sqrt{ x^{2}+y^{2} }} \, dy\\
\\
&\int \frac{1}{\sqrt{ x^{2}+y^{2} }} \, dy \qquad y=x\tan(\theta) \,\Rightarrow\,dy=x\sec ^{2}(\theta)\,d\theta\\
&\int \frac{x\sec^{2}(\theta)}{x\sec(\theta)} \, d\theta\\
&\int \sec(\theta) \, d\theta \\
&\ln|\sec\theta+\tan \theta|+c\\
&\ln\left| \frac{\sqrt{ x^{2}+y^{2} }}{x}+\frac{y}{x}\right|+c
\\\\

V&=\frac{\lambda}{4\pi\varepsilon_{0}}\left[ \ln \left| \frac{\sqrt{ x^{2}+y^{2} }}{x}+\frac{y}{x}\right| \right]_{-y}^{y}\\
V&=\frac{\lambda}{4\pi\varepsilon_{0}}\left[ \ln\left| \frac{\sqrt{ x^{2}+y^{2} }}{x}+\frac{y}{x}\right|-\ln\left| \frac{\sqrt{ x^{2}+y^{2} }}{x}-\frac{y}{x}\right| \right]  \\
&\boxed{V=\frac{\lambda}{4\pi\varepsilon_{0}}\ln\left| \frac{\sqrt{ x^{2}+y^{2} }+y}{\sqrt{ x^{2}+y^{2} }-y} \right|}
\end{align*}
$$

2) Se tiene un disco de radio $R$ con una carga continua $Q$ distribuida uniformemente, encuentre el potencial en el punto $p$ a una distancia $z$ del centro del disco.

![[Potencial en disco|center]]
$$
\begin{align*}
d&=\sqrt{ z^{2}+r^{2} }\\
dq&=\sigma\cdot 2\pi r\,dr\\
V&=\frac{1}{4\pi\varepsilon_{0}}\int   \frac{dq}{d}\\
\\
V&=\frac{1}{4\pi\varepsilon_{0}}\int_{0}^{R} \frac{\sigma\cdot 2\pi r}{\sqrt{ z^{2}+r^{2} }}  \,dr\\
V&=\frac{\sigma 2\pi }{4\pi\varepsilon_{0}}\int _{0}^{R} \frac{r}{\sqrt{ z^{2}+r^{2} }} \, dr\\
&=\frac{\sigma}{2\varepsilon_{0}}\left[ \sqrt{ z^{2}+r^{2}} \right]_{0}^{R}\\
&\boxed{V=\frac{\sigma(\sqrt{ z^{2}+R^{2} }-z)}{2\varepsilon_{0}}}
\end{align*}
$$

---
## Capacitancia

Cualquier par de conductores que se encuentren separados por un aislante o el vacío forman un capacitor. Inicialmente (en la mayoría de casos) se encuentran descargados, cuando los electrones son transferidos de un conductor a otro, se le conoce como cargar el capacitor, de esta forma uno de los conductores queda cargado positivamente y el otro negativamente con una carga $Q$.
Es importante mencionar que en conjunto (ambas placas) mantienen una carga neta 0, sin embargo individualmente (si están cargados) posee una carga $Q$ de signo contrario, por lo que si se establece que un capacitor posee esta carga, se refiere a que la magnitud de la carga que posee el capacitor en alguna de sus placas es $Q$.

La carga que puede almacenar un capacitor depende de su capacitancia, y del voltaje que posee, por esto mismo es posible encontrar la capacitancia que posee el capacitor con la siguiente expresión:
$$
C=\frac{Q}{V_{ab}}
$$
La capacitancia se mide en Faradios, la cual es una unidad derivada del cociente entre el coulomb y el voltio $[C/V]$.

### Cálculo de capacitancia

Si poseemos un capacitor formado por dos placas conductoras, si queremos obtener la capacitancia dada por estas dos placas, entonces podemos obtenerla a partir del campo eléctrico.

Para dos placas paralelas, el campo eléctrico es constante y con un valor de:
$$
E=\frac{\sigma}{\varepsilon_{0}}
$$
Ahora utilizando la definición de $\sigma$:
$$
E=\frac{Q}{\varepsilon_{0}A}
$$
Nosotros sabemos que $Ed$ siendo $d$ la distancia a la placa es igual al voltaje, por lo que:
$$
V_{ab}=Ed=\frac{Qd}{\varepsilon_{0}A}
$$
Y con esto, tras unas maniobras utilizando la ecuación de la capacitancia, obtenemos:
$$
\boxed{C=\frac{Q}{V_{ab}}=\varepsilon_{0} \frac{A}{d}}
$$


> [!tip] Cálculo de capacitancia
> Existen diversas formas de encontrar la capacitancia, como vimos anteriormente algunas de ellas.
> Pero, podemos llegar a una forma estandarizada para formas regulares.
>
> El primer paso es el de buscar encontrar el campo eléctrico del cuerpo que se esta utilizando, podemos usar el proceso que se aprendió para [[Campos eléctricos|encontrar el campo eléctrico]], o podemos utilizar la ley de gauss para facilitarnos el proceso.
> $$
\oint \vec{E}\cdot dA=\frac{q_{neta}}{\varepsilon_{0}}
>$$
>Ya obtenido el campo, se realiza el cálculo del voltaje utilizando:
>$$
V_{a}-V_{b}=\int \vec{E}\cdot dl 
>$$
Finalmente se realiza el cociente entre la carga $Q$ y el voltaje obtenido anteriormente:
>$$
C=\frac{Q}{V_{ab}}
>$$


---
### Capacitores en serie y en paralelo

En la vida real, los capacitores ya son fabricados con capacitancias establecidas, pero en las aplicaciones se pueden necesitar distintos valores de de capacitancia, y con este fin se pueden agregar más capacitores y conectarse en una forma en la que se pueda llegar a la capacitancia requerida.

#### Capacitores en serie

Los capacitores en serie es un tipo de conexión en la cual los capacitores son conectados entre si utilizando alambres conductores entre dos puntos como se muestra en la figura:

![[Capacitores1|center]]

Si se aplica una diferencia de voltaje entre los puntos $a$ a $b$, una carga $Q$ viaja hasta la primera placa del capacitor $C_{1}$, la cual se carga con esta carga, de esta forma la placa genera una fuerza que empuja los electrones de la otra placa mediante carga inducida, lo que empuja lo equivalente a la carga $Q$ a la primera placa del segundo capacitor, y así sucesivamente, terminando en que los capacitores, mantendrán la carga que portan entre ellos constante.
Por lo que si queremos obtener la suma de las capacitancias de los dos capacitores, tenemos que hacer la evaluación de los valores que tenemos, buscando una relación entre las diferencias de potencial que conectan los puntos $a,\,b\,\text{ y }c$, entonces tenemos:

$$
\begin{align*}
V_{ac}&=V_{1}=\frac{Q}{C_{1}}&V_{cb}&=V_{2}=\frac{Q}{C_{2}}
\end{align*}
$$
$$
V_{ac}=V_{1}+V_{2}=Q\left( \frac{1}{C_{1}}+\frac{1}{C_{2}} \right)
$$
por lo tanto:
$$
\frac{V}{Q}=\frac{1}{C_{1}}+\frac{1}{C_{2}}
$$
Finalmente, podemos juntar estos dos capacitores como un solo capacitor equivalente que posea la capacitancia resultante de los dos capacitores.
$$
C_{eq}=\frac{Q}{V}\qquad \text{O bien}\qquad \frac{1}{C_{eq}}=\frac{V}{Q}
$$
Con estas expresiones podemos encontrar el valor de la capacitancia equivalente:
$$
\frac{1}{C_{eq}}=\frac{1}{C_{1}}+\frac{1}{C_{2}}
$$
Estas expresión se repetirá aún si se agregan más capacitores con capacitancia $C_{i}$, por lo que generalizando la ecuación:
$$
\boxed{\frac{1}{C_{eq}}=\sum_{i} \frac{1}{C_{i}}}
$$
#### Capacitores en paralelo

Los capacitores de igual forma pueden ser conectado en paralelo entre ellos, al conectarlos de esta forma, si observamos, la diferencia de potencial en ambos extremos de los capacitores es el mismo, es decir que en una configuración en la que los capacitores se encuentren en paralelo, el voltaje permanecerá constante.

![[Capacitores2|center]]

Con esto en mente, podemos buscar la carga a partir de los valores que se tienen:
$$
Q_{1}=C_{1}V\qquad Q_{2}=C_{2}V
$$
$$
Q_{total}=Q_{1}+Q_{2}=C_{1}V+C_{2}V=V(C_{1}+C_{2})
$$
$$
\frac{Q_{total}}{V}=C_{1}+C_{2}
$$
$$
C=\frac{Q}{V}\qquad \Rightarrow\qquad C_{total}=C_{1}+C_{2}
$$
Y de igual forma que se observaba en el apartado de la configuración en serie, generalizando para diferentes capacitores $C_{i}$:
$$
\boxed{C_{total}=\sum_{i}C_{i}}
$$
---
### Almacenamiento de energía en capacitores

Los capacitores se usan en diversas aplicaciones, y muchas de estas dependen de la capacidad del capacitor de almacenar energía potencial eléctrica en su interior, para esto podemos encontrar una expresión del valor de esta energía:

Primeramente tenemos que establecer que la energía potencial eléctrica que almacena el capacitor es **exactamente igual** al trabajo realizado para cargar el capacitor:
$$
W=U
$$
Teniendo esto en cuenta, podemos afirmar que al momento en que un capacitor se encuentra completamente cargado el potencial es igual a:
$$
V=\frac{Q}{C}
$$
Ahora, para saber cuanto potencial posee el capacitor en algún punto durante la carga de este, podemos decir que es:
$$
v=\frac{q}{C}
$$
Durante esta etapa, el trabajo $dW$ requerido para mover un elemento de carga $dq$ es de:
$$
dW=v\,dq=\frac{q\,dq}{C}
$$
De esta forma, podemos encontrar el valor del trabajo:
$$
\int _{0}^{W} dW= \int_{0}^{Q} \frac{q}{C} \, dq 
$$
Asumiendo que el lector ya sabe integrar, obtenemos la siguiente expresión:
$$
W=\frac{Q^{2}}{2C}
$$
Y como anteriormente encontramos que el trabajo para cargar el capacitor es igual a la energía potencial que almacena, podemos encontrar la energía.
También utilizando la relación que $Q=CV$, podemos encontrar diferentes expresiones para la energía:
$$
\boxed{U=\frac{Q^{2}}{2C}= \frac{1}{2}CV^{2}=\frac{1}{2}QV}
$$
#### Densidad de carga 

La densidad de carga es la cantidad de energía potencial que puede almacenar un objeto, en estos casos en específico, el capacitor.
Para el caso específico del capacitor, es la energía potencial ($U$) entre el volumen encerrado entre las dos placas ($Ad$).
$$
u\,\text{(densidad de carga)}=\frac{U}{Ad}=\frac{\frac{1}{2}QV}{Ad}
$$
Tras utilizar algunas de las ecuaciones de la capacitancia ($C=\varepsilon_{0} A/d$) y del potencial relacionado al campo eléctrico: $(V=Ed)$:
$$
\boxed{u=\frac{1}{2}\varepsilon_{0}E^{2}}
$$
### Dieléctricos

La gran mayoría de los capacitores poseen un material no conductor o dieléctricos, lo que puede solucionar diversos problemas, como mantener separadas las placas del capacitor lo más cerca posible sin que se toquen, otra función de los dieléctricos es que estos permiten obtener el máximo la posible diferencia de potencial entre las placas del capacitor.

Algunos materiales permiten obtener un mayor valor de la capacitancia de un capacitor en comparación a tener un capacitor con el vacío entre sus placas. Esto se le conoce como la constante dieléctrica, es decir que la capacitancia sin el dieléctrico ($C_{0}$) será proporcionalmente menor en comparación a la capacitancia con el dieléctrico ($C$), por lo que para obtener esta constante dieléctrica, tenemos que encontrar el cociente entre estas dos capacitancias:
$$
\boxed{k_{e}=\frac{C}{C_{0}}}
$$
Si se mantiene una carga constante, entonces podemos hacer uso de $Q=C_{0}V_{0}=CV$, por lo que haciendo unos arreglos a la ecuación, podemos encontrar una expresión de la constante dieléctrica en términos del potencial:
$$
\boxed{V=\frac{V_{0}}{k_{e}}}
$$
#### Carga inducida y polarización

En un capacitor siempre se forma un campo eléctrico $\vec{E}$ entre las placas, pero al momento de agregarle un dieléctrico al capacitor, las partículas del material buscan alinearse con respecto a este campo eléctrico, lo que resulta en que el material forme un campo eléctrico en sentido contrario, lo que reduce el campo eléctrico original del capacitor en proporción a la constante dieléctrica..

![[Dielectricos|center]]

Como se puede ver en la imagen, al alinearse las cargas dentro del material del dieléctrico, se genera un pequeño campo eléctrico que va en contra del campo eléctrico original, lo que disminuye su magnitud, de esta forma es posible calcular el nuevo campo eléctrico para el dieléctrico:
$$
\boxed{E=\frac{E_{0}}{k_{e}}}
$$

Todo este tiempo, hemos trabajado con la permitividad en el vacío, sin embargo al trabajar con dieléctricos, no estamos trabajando con el vacío entre las placas, sino con un material. Cada material posee su propia permitividad, y esta siempre es una proporción de la permitividad en el vacío, por lo que la permitividad del dieléctrico es dada por:
$$
\boxed{\varepsilon=k_{e}\varepsilon_{0}}
$$
Esto varía varios valores que hemos visto anteriormente, como por ejemplo el campo eléctrico que se encuentra encerrado en un capacitor:
$$
E=\frac{\sigma}{\varepsilon}=\frac{\sigma}{k_{e}\varepsilon}
$$
A su vez la capacitancia del capacitor cuando hay un dieléctrico presente está dada por:
$$
C=C_{0}k_{e}=k_{e}\varepsilon_{0} \frac{A}{d}=\varepsilon \frac{A}{d}
$$
Y también la densidad de carga entre las placas:
$$
u=\frac{1}{2}k_{e}\varepsilon_{0}E^{2}=\frac{1}{2}\varepsilon E^{2}
$$
