---
tags:
  - Física
---
## Trabajo

Como se conoce debido a la primera ley de Newton, todo cuerpo tiende a mantener su estado (ya sea de movimiento o de reposo) si no se le es aplicada ninguna fuerza externa a este, sin embargo, para ciertos objetos se necesita más fuerza para poder moverlos que para otros más livianos. Para todo esto se puede coincidir el concepto cotidiano de trabajo, el cuál se puede definir como cualquier actividad que requiere un esfuerzo muscular o mental.

Sin embargo en física se puede definir de una manera más específica el concepto de trabajo, el cual podremos descubrir que es, sin importar el tipo de movimiento, **el trabajo total realizado sobre una partícula por todas las fuerzas que actúan sobre ella es igual *al cambio en su energía cinética*** 

Si tomamos ejemplos tales como el de empujar un sofá, empujar un automóvil o levantar una pila de libros, estos poseen algo en común, y es que se realiza trabajo por medio de una fuerza que desplaza el objeto. Claramente el trabajo aumentará si se realiza una fuerza mayor sobre el objeto, o si existe un mayor desplazamiento. Con esto en mente, en una superficie plana, se puede definir el trabajo como la fuerza ejercida sobre un objeto multiplicado por el desplazamiento del objeto.

$$
W=Fs\, \text{ (Una fuerza constante en la dirección de desplazamiento rectilíneo)}
$$

Si hablamos de las unidades de medida en las que se mide el trabajo, estas según el sistema internacional serían los **Joules**, los cuales se definen como Newtons por metro ($N\cdot m$).

## Trabajo con fuerza constante en un ángulo relativo al desplazamiento

Actualmente hemos definido el trabajo en un movimiento rectilíneo, sin embargo, no siempre se poseerá una fuerza la cuál actúe en la misma dirección que el desplazamiento, sino que es posible que la fuerza pueda tener cierto ángulo de aplicación respecto al desplazamiento del objeto. Si seguimos en el patrón del trabajo en el movimiento rectilíneo, se tomará simplemente la componente en dirección al desplazamiento de la fuerza, usualmente la componente en $x$. Y debido a que la fuerza se estaría descomponiendo en su componente horizontal, sería:

$$
W=Fs\cos (\phi)
$$

Esto suponiendo que $F$ y $s$ son constantes durante el desplazamiento, en el caso que la fuerza y el desplazamiento estén en la misma dirección, entonces $\phi=0$, por lo tanto $\cos(\phi)=1$ y volveríamos a la ecuación original planteada en el anterior apartado.
Sin embargo, debido a que sabemos que la fuerza y el desplazamiento son vectores ($\vec{F},\,\vec{s}$) entonces vemos que la fórmula del trabajo toma la forma del producto punto de vectores, por lo tanto podríamos definir que el trabajo es igual al producto punto entre los vectores de fuerza y desplazamiento:
$$
W=\vec{F}\cdot \vec{s}
$$

> [!warning] Cuidado
> Es importante mencionar que el trabajo es un escalar, de ahí que el producto punto devuelva un valor escalar, aún sabiendo que se trabajan con valores vectoriales.

### Dirección de la fuerza respecto al desplazamiento

En el caso de que una fuerza se ejerza sobre un cuerpo pueden existir tres posibles casos:

1. La fuerza $\vec{F}$ posee una componente en la misma dirección que el desplazamiento. En este caso se da que el trabajo es positivo.
2. La fuerza $\vec{F}$ posee una componente en dirección contraria al desplazamiento. En este caso, debido a que el ángulo es más de 90°, al ser $\cos(\theta)$ negativo en el segundo y tercer cuadrante, al ser multiplicado por el desplazamiento devuelve un trabajo negativo.
3. La fuerza $\vec{F}$ es perpendicular al desplazamiento. Debido a que en estos casos la fuerza posee una dirección de 90°, la función coseno se anula. Por lo tanto, cualquier fuerza perpendicular al desplazamiento realiza un trabajo 0.

### Valores del trabajo

El trabajo como se veía anteriormente esta condicionado respecto al desplazamiento de un cuerpo, sin embargo si ciertas fuerzas se aplican en distintas direcciones respecto al desplazamiento, el trabajo puede cambiar su valor.
1. En general, si una fuerza está en la misma dirección a la que apunta el desplazamiento, entonces se generará un trabajo positivo, ya que se está moviendo en la misma dirección.
2. De la misma manera, si la fuerza está en sentido contrario al desplazamiento, entonces se está generando un trabajo negativo, por ende si se llega a encontrar un trabajo negativo, es porque la fuerza está en contra del desplazamiento.
3. Sin embargo, si a un objeto en movimiento (o también podría estar quieto) se le aplica una fuerza perpendicular al desplazamiento, entonces se dice que esta realizando un trabajo 0, debido a que la fuerza no está aportando al movimiento del cuerpo.

### Trabajo total

Hasta el momento hemos visto el trabajo si una solo fuerza actúa sobre un objeto. Pero, ¿Y si hay más de una fuerza involucrada? Para estos casos se puede proceder de dos maneras:
1. Primeramente, utilizar las ecuaciones planteadas anteriormente para obtener el trabajo individual de cada una de las fuerzas, y finalmente sumarlas de manera algebraica.
2. Realizar la suma vectorial de cada una de las fuerzas que se involucran sobre el objeto, y sustituir esta suma en la fórmula de $W=\vec{F}\cdot \vec{s}$.
## Energía cinética

### Teorema trabajo-energía

En cuanto al trabajo sobre un cuerpo, este varía dependiendo del desplazamiento del cuerpo, sin embargo, el trabajo también se ve afectado por los cambios de rapidez y viceversa. Si lo vemos como se mencionó en [[Trabajo y energía cinética#Valores del trabajo|los valores del trabajo]], el signo o valor del trabajo está condicionado respecto a la dirección de la fuerza total respecto al desplazamiento del cuerpo, así mismo, la rapidez  del cuerpo se vera afectada debido al trabajo y la fuerza que lo genera.
Por ejemplo imaginemos un bloque que está en movimiento en una superficie sin fricción, si se le aplica una fuerza que va en el mismo sentido del desplazamiento, entonces se genera un trabajo positivo, a su vez, la fuerza está acelerando el bloque, por ende la rapidez del bloque también aumenta.

Ahora si a ese bloque, se le aplica una fuerza pero en dirección contraria al desplazamiento de este (es decir se realiza un trabajo negativo), se estaría frenando al bloque, disminuyendo así su velocidad.
Como último caso, si se aplica una fuerza perpendicular al desplazamiento sobre el bloque, se generaría un trabajo 0, y ya que la fuerza no afecta al movimiento no se estaría realizando ningún cambio en la rapidez del bloque.
En resumen si tenemos un objeto en movimiento y su $W_{tot}>0$ entonces el objeto está acelerando, si $W_{tot}<0$ entonces el objeto está frenándose, y si el $W_{tot}=0$ entonces el objeto mantiene su rapidez.

Intentemos expresar esta teoría en forma cuantitativa:
Si tenemos que un objeto con masa $m$, la cual se mueve constantemente gracias a una fuerza constante $F$ que desplaza el objeto desde un $x_{1}$ hasta un $x_{2}$ con una aceleración constante siguiendo así la segunda ley de Newton ($F=ma$), por ende la rapidez cambiaría de una $v_{1}$ a una $v_{2}$, y su desplazamiento dado por $\Delta x=x_{2}-x_{1}$.
Entonces utilizando una fórmula de movimiento con rapidez constante obtenemos lo siguiente:
$$
\begin{align*}
v_{2}^{2}&=v_{1}^{2}+2a_{x}\Delta x\\
\frac{v_{2}^{2}-v_{1}^{2}}{2\cdot\Delta x}&=a_{x}\\
a_{x}&=\frac{v_{2}^{2}-v_{1}^{2}}{2\cdot \Delta x}
\end{align*}
$$
De esta manera obtenemos la aceleración del cuerpo, ahora, si igualamos está formula a la de la fuerza $F$ se obtiene:
$$
\begin{align*}
F=ma_{x}&=m\left( \frac{v_{2}^{2}-v_{1}^{2}}{2\cdot \Delta x} \right)\\
F\Delta x&=\frac{1}{2}v_{2}^{2}m-\frac{1}{2}v_{1}^{2}m\\
\Delta x&=s\\
Fs&=\frac{1}{2}v_{2}^{2}m-\frac{1}{2}v_{1}^{2}m\\
\end{align*}
$$
El producto $Fs$ es lo que nosotros ya conocemos como trabajo, y debido a que el trabajo es la variación de la energía cinética y tenemos una variación dentro de la fórmula podemos concluir que la energía cinética de la partícula está dada por:
$$
E_{c}=K=\frac{1}{2}v^{2}m
$$
Y por ende:
$$
W_{tot}=\Delta K=K_{2}-K_{1}
$$
Siendo este resultado el **teorema trabajo-energía**.

---
> [!warning] Ojo!
> La energía cinética bajo ningún concepto va a ser negativa, por lo tanto, si al realizar cálculos, ésta resultara negativa, es necesario revisar el procedimiento realizado.

---
### Energía cinética en objetos que parten o terminan en el reposo

Como un caso especial, si se requiere mover un objeto desde el reposo hasta un punto, entonces la energía cinética de este es igual al trabajo realizado para poder mover el objeto hasta esa posición. ya que $K_{1}=0$ entonces:
$$
W_{tot}=K_{2}-0=K_{2}
$$
Sin embargo, existe otra interpretación para la energía cinética la cual es que: La energía cinética es igual al trabajo total que puede generar una partícula al detenerse. En este caso, se tomaría la energía cinética final como 0 ($K_{2}=0$), entonces:
$$
W_{tot}=0-K_{1}=-K_{1}
$$
En este caso, el trabajo sería negativo, ya que como vimos antes, la partícula está desacelerando, por ende, está realizando un trabajo negativo.


## Trabajo y energía con fuerza variable

Hasta el momento, hemos trabajado la energía cinética y el trabajo con una fuerza constante, sin embargo, en la vida cotidiana en muy raras ocasiones se encuentran fuerzas constantes, por esta misma razón es que es necesario trabajar con fuerzas que varían respecto a la posición de un objeto.
En forma general, si uno busca encontrar un trabajo a partir de la fuerza se puede encontrar con la siguiente expresión:
$$
W=\int _{x_{1}}^{x_{2}} \vec{F}(x) \, dx 
$$
Esto se aplica siendo $\vec{F}(x)$ una función de fuerza.
Este tema puede verse de igual manera en las aplicaciones de la integral en el curso de cálculo II en el tema de [[4.3 Aplicaciones de las integrales definidas#Trabajo mecánico|trabajo mecánico]].

Podemos demostrar la fórmula del trabajo a partir de nuestra nueva forma del trabajo.
En los casos ya que decíamos que la fuerza era una constante, nos permite sacar la fuerza de la integral quedándonos:
$$
W=\int _{x_{1}}^{x_{2}}F \, dx=F\int _{x_{1}}^{x_{2}} \, dx=F(x_{2}-x_{1})  
$$
Y ya que conocemos que el desplazamiento es $s=x_{2}-x_{1}$, podemos obtener nuestra fórmula del trabajo con fuerza constante.

### Trabajo al estirar o contraer un resorte

Como se puede comprobar intentando deformar un resorte, conforme se va deformando, cada vez se necesita aplicar una mayor fuerza a este para poder seguir deformándolo, es decir que la fuerza cambia respecto a la elongación del resorte, entonces podemos decir que la función de fuerza para un resorte es:
$$
\vec{F}(x)=kx
$$
Donde $k$ es una constante conocida como constante de fuerza (o constante de resorte), esta puede variar dependiendo del tipo o material del resorte.

Entonces si intentamos encontrar la fórmula del trabajo para estirar un resorte, aplicamos la integral que planteamos antes y le evaluamos la función de fuerza.
Suponiendo que se tiene un resorte que se estirará desde su estado inicial (con elongación 0):
$$
W=\int _{0}^{X} kx \, dx=k\int _{0}^{X} x \, dx=k\left( \frac{X^{2}}{2} -\frac{0^{2}}{2}\right)=\frac{1}{2}kX^{2}  
$$
Sin embargo, si se quiere encontrar el trabajo desde una posición en donde el resorte ya se encuentra estirado:
$$
W=\int _{x_{1}}^{x_{2}}kx \, dx=k\int _{x_{1}}^{x_{2}}x \, dx=\frac{1}{2}kx_{2}^{2}-\frac{1}{2}kx_{1}^{2}  
$$
