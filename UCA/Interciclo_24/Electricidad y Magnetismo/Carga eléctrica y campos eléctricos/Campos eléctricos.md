---
tags:
  - EMA
---
Anteriormente ya trabajamos con la [[Ley de Coulomb|ley de Coulomb]] para cargas puntales. Sin embargo, ¿Cómo es que una carga sabe que la otra carga se encuentra ahí?
Bueno, todo esto se lo debemos a que las cargas generan **campos eléctricos** alrededor de ellas. Las partículas forman estos campos, y los campos son lo que interactúan con el resto de las partículas.

Ésta incógnita de los campos eléctricos surgieron a partir de lo que hemos visto en materias anteriores: Si un cuerpo se mueve, este movimiento es el producto de una fuerza ejercida sobre el objeto (primera ley de Newton), por esto mismo, ya que las partículas se están atrayendo o repeliendo entre sí, *debe* de existir una fuerza responsable de este movimiento, es por esto mismo que se empezó a pensar acerca de estos como campos de fuerza.

Con esto en mente, es posible afirmar que para toda partícula puntual cargada, la fuerza que es ejercida sobre ella es debido a los campos eléctricos que otros objetos cargados originan.

Para comprobar si existe un campo eléctrico alrededor de un cuerpo con carga $Q$, es necesario tener una carga de prueba $q_{0}$, entonces el campo eléctrico sobre la carga $Q$ está dado por la siguiente expresión:
$$
\vec{\mathbb{E}}=\frac{\vec{\mathbb{F}}}{q_{0}}
$$
donde $\vec{\mathbb{F}}$ es la fuerza producida entre las cargas y se calcula con la [[Ley de Coulomb|ley de Coulomb]]:
$$
\vec{\mathbb{F}}=\frac{1}{4\pi\varepsilon_{0}} \frac{Qq}{r^{2}}
$$
Con esto obtenido, es posible encontrar el valor del propio campo eléctrico a una distancia $r$ de la partícula que genera el campo:
$$
\vec{\mathbb{E}}=\frac{1}{4\pi \varepsilon_{0}} \frac{Q}{r^{2}}
$$
---

## Carga distribuida

Anteriormente hemos trabajado para encontrar cuál sería el campo eléctrico de una carga puntual. Lastimosamente el mundo no es tan perfecto, ya que no existen las cargas puntuales en la naturaleza, por lo que tendremos que empezar a estudiar como se comportan los campos eléctricos en cargas distribuidas en un cuerpo.

Imaginemos este dicho cuerpo, nosotros no sabemos realmente como obtener el campo eléctrico sobre un cuerpo, pero si sabemos como obtener el campo de una carga puntual.
Por lo que vamos a dividir la carga del cuerpo en una parte muy pequeña de carga, a tal punto que se comporte como una carga puntual, es decir que obtendremos un diferencial de carga $dq$ que a su vez produce una pequeña parte del campo eléctrico del cuerpo, es decir, un diferencial de campo eléctrico $d \vec{E}$, y podemos obtener una expresión que pueda relacionarlas a ambas, siendo esta la forma diferencial del cálculo de campo eléctrico:
$$
d\vec{E}=\frac{1}{4\pi\varepsilon_{0}} \frac{dq}{r^{2}}
$$
Entonces, si queremos obtener como afecta el campo eléctrico del cuerpo sobre un punto en el espacio, es necesario obtener la suma de todos estos diferenciales de campo:
$$
E=\int d\vec{E} 
$$
Es importante mencionar que como estamos buscando como el campo afecta en ese punto, entonces tendremos que encontrar como es afectado el punto desde cada una de las dimensiones espaciales, por lo que también podemos representar el campo eléctrico en sus componentes:
$$
E_{x}=\int  \, d\vec{E}_{x} \qquad E_{y} =\int  \, d\vec{E}_{y} \qquad E_{z}=\int  \, d\vec{E}_{z}  
$$

> [!important] Expresar en componentes
> Preferiblemente al trabajar con la obtención de campos eléctricos es preferible encontrar el campo en sus componentes rectangulares

### Superposición de campos eléctricos

Para las cargas, estas pueden estar distribuidas a lo largo de diversos cuerpos como lo veremos a continuación:

1) **Distribución a lo largo de una línea**: Estos casos se dan en cuerpos como alambres o cables delgados, para estos casos, se utiliza la siguiente igualdad utilizando la *densidad de carga lineal*:
$$
\lambda dx=dq
$$
donde $dx$ sería un diferencial de longitud que esta guiado por la orientación del objeto, y el $dq$ siendo el diferencial de carga donde se sustituye en la ecuación diferencial del campo eléctrico.

2) **Distribución sobre una superficie:** Para casos como podría ser una lámina, se utiliza la *densidad de carga superficial*:
$$
\sigma dA=dq
$$
en este caso, ya no sería un diferencial de longitud, sino un diferencial de área.

3) **Distribución a través de un volumen**: Finalmente, para cualquier sólido con volumen, se utiliza la *densidad de carga volumétrica*:
$$
\rho dV=dq
$$
---
### Ejemplo: 

**Alambre recto de carga uniforme: una carga Q se distribuye uniformemente a lo largo de un alambre desde –a hasta a. Calcule E a una distancia x del origen**

![[Diagrama1|center]]

Primeramente, como estamos trabajando con un alambre, entonces tendremos que utilizar la densidad de carga lineal, para esto es necesario dividir la carga del alambre entre su longitud, por lo que nos quedaría de la siguiente manera:
$$
\begin{align*}
\lambda&=\frac{Q}{l}\\
&=\frac{Q}{2a}
\end{align*}
$$
Ya obtenido lambda ya podemos encontrar cuanto valdría nuestro diferencial de carga, como en este caso el alambre esta sobre el eje $y$, nuestro diferencial de longitud será un $dy$:
$$
\begin{align*}
\lambda dy=dq\\
\frac{Q}{2a}dy=dq
\end{align*}
$$
Ahora, antes de sustituir en nuestro diferencial de campo, tendremos que obtener la distancia $r$ que utilizaremos.
Recordemos que esta distancia es la que se encuentra entre nuestro diferencial de carga hasta el punto $x$, por lo que podemos tratar nuestro diagrama de la siguiente manera:

![[Diagrama1.1|center]]
De esta forma, podemos expresar la distancia entre nuestro diferencial de carga y el punto x, como la hipotenusa de un triángulo cuya altura varía dependiendo de la posición del diferencial y de base constante $x$.
Con estas consideraciones podemos expresar la distancia con el teorema de Pitágoras:
$$
r=\sqrt{ y^{2}+x^{2} }
$$
Ya con todos los valores anteriores (tanto del diferencial de carga como la distancia entre la carga y el punto) podemos encontrar nuestro diferencial de campo eléctrico:

$$
\begin{align*}
d\vec{E}&=\frac{1}{4\pi\varepsilon_{0}} \frac{dq}{r^{2}}\\
d\vec{E}&=\frac{1}{4\pi\varepsilon_{0}} \frac{Q}{2a\,(\sqrt{ y^{2}+x^{2} })^{2}}dy\\
d\vec{E}&=\frac{1}{4\pi\varepsilon_{0}} \frac{Q}{2a\,(y^{2}+x^{2})}dy
\end{align*}
$$
Sin embargo, como mencionamos anteriormente es preferible expresar el campo eléctrico de una carga distribuida en función de sus componentes rectangulares, por lo que buscaremos encontrarlas.

Volviendo a nuestro diagrama, hemos colocado un ángulo $\theta$, a partir de este podremos encontrar las diferentes componentes, ya que a su vez estaríamos trabajando con un triángulo:

$$
\begin{align*}
d\vec{E}_{x}&=d\vec{E}\cos \theta\\
d\vec{E}_{y}&=d\vec{E}\sin \theta
\end{align*}
$$
Y mediante las definiciones de las identidades trigonométricas, podemos encontrar el valor tanto para el seno como para el coseno:
$$
\begin{align*}
\cos \theta&=\frac{\mathrm{Adyacente}}{\mathrm{Hipotenusa}}=\frac{x}{\sqrt{ y^{2}+x^{2} }}\\
\sin \theta&=\frac{\mathrm{\mathrm{Opuesto}}}{\mathrm{Hipotenusa}}=\frac{y}{\sqrt{ y^{2}+x^{2} }}
\end{align*}
$$
Por lo que tenemos:

$$
\begin{align*}
d\vec{E}_{x}&=\frac{Q}{4\pi\varepsilon_{0}\cdot 2a} \frac{x}{(y^{2}+x^{2})^{3/2}}dy\\
d\vec{E}_{y}&=\frac{Q}{4\pi\varepsilon_{0}\cdot 2a} \frac{y}{(y^{2}+x^{2})^{3/2}}dy
\end{align*}
$$
Ya con el valor de los diferenciales, finalmente podemos pasar al proceso de encontrar los valores de las componentes del campo eléctrico.
Ya que estamos variando la posición en $y$ desde la parte más baja del alambre ($-a$) hasta la parte más arriba del alambre ($a$), entonces nuestras integrales quedarían de la siguiente manera:
$$
\begin{align*}
\vec{E}_{x}&=\int \, d\vec{E}_{x} \\
\vec{E}_{x}&=\frac{Q}{4\pi\varepsilon_{0}\cdot 2a}\int_{-a}^{a} \frac{x}{(y^{2}+x^{2})^{3/2}} \, dy\\\\
\vec{E}_{y}&=\int  \, d\vec{E}_{y}\\
\vec{E}_{y}&= \frac{Q}{4\pi\varepsilon_{0}\cdot 2a}\int_{-a}^{a} \frac{y}{(y^{2}+x^{2})^{3/2}} \, dy
\end{align*}
$$
Las integrales quedan como ejercicio para el lector.

Tras la resolución de las integrales, podemos obtener los siguientes valores del campo eléctrico:
$$
\begin{align*}
\vec{E}_{x}&=\frac{Q}{4\pi\varepsilon_{0}\cdot x\sqrt{ x^{2}+a^{2} }}\\
\vec{E}_{y}&=0
\end{align*}
$$
Por lo que el campo eléctrico del alambre se comporta de la siguiente forma:
$$
\boxed{\vec{E}=\frac{1}{4\pi\varepsilon_{0}} \frac{Q}{x\sqrt{ x^{2}+a^{2} }}\hat{\imath}}
$$
