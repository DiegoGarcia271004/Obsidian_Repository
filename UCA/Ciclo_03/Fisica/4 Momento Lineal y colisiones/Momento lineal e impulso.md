---
tags:
  - Física
---
Anteriormente pudimos definir la segunda ley de Newton para partículas: $\sum \vec{F}=ma$, a partir de la cual obtuvimos [[Fuerzas conservativas y no conservativas#Ley de conservación de la energía|la ley de conservación de energía]] en términos de energía y trabajo, sin embargo, esta ley se puede aplicar de otra forma.

## Segunda ley de Newton en términos del momento lineal

Si poseemos un cuerpo de masa $m$, y recordando los conceptos vistos en [[1.2 Aceleración media e instantánea]], entonces podemos describir la segunda ley de la siguiente manera:
$$
\sum \vec{F}=m \frac{d\vec{v}}{dx}=\frac{d}{dx}(m\vec{v})
$$
Podemos incluir la masa del objeto dentro de la derivada por la propiedad de que es constante, indicando que la fuerza neta $\sum \vec{F}$ sobre un objeto es igual a la taza de cambio de la masa por la velocidad, a este producto entre masa y velocidad lo denominamos **momento lineal** de la partícula, por lo tanto:
$$
\vec{p}=m\vec{v}
$$
Donde $\vec{p}$ es el momento lineal. Gracias a esta expresión podemos intuir que a mayor masa, o mayor velocidad, el momento lineal aumentar proporcionalmente a estos.

Cabe mencionar que el momento lineal es una expresión vectorial que es paralela a la velocidad de la partícula, por lo tanto su orientación si importa. Podemos definir un ejemplo de un automóvil que se mueve a 20 m/s hacia el norte, este tendrá la misma magnitud de momento lineal que un automóvil de la misma masa que se mueve a la misma velocidad pero al sur, pero, la dirección de la velocidad a la que va cada carro será diferente.
Con esto en mente, podemos entender que es posible expresar el momento lineal de la partícula respecto a sus componentes rectangulares de velocidad:
$$
p_{x}=mv_{x} \qquad p_{y}=mv_{y}\qquad p_{z}=mv_{z}
$$
## Teorema del impulso y momento lineal

Podemos observar que tanto el momento lineal $\vec{p}=m\vec{v}$ como la energía cinética $K=\frac{1}{2}mv^{2}$ dependen de la velocidad, pero, ¿Qué diferencia a estas dos cantidades? Matemáticamente hablando, las diferencia en que el momento lineal es una cantidad vectorial proporcional a la magnitud de la velocidad, mientras que la energía cinética es una cantidad escalar que aumenta proporcionalmente al cuadrado de la velocidad de la partícula.
Sin embargo, desde el punto de vista físico es posible definir esta diferencia, pero para eso es necesario introducir un concepto relacionado íntimamente con el momento lineal, *el impulso*.

### Impulso

Consideremos un cuerpo de masa $m$ sobre el cual actúa una fuerza en un intervalo de tiempo $\Delta t$, desde un tiempo $t_{1}$ hasta un tiempo $t_{2}$. Dado estas variables, definimos el impulso de la fuerza neta $\vec{J}$ como el producto de la fuerza neta por el intervalo de tiempo:
$$
\vec{J}=\sum \vec{F}(t_{2}-t_{1})=\sum \vec{F}\Delta t
$$
El impulso es una magnitud vectorial cuya dirección está dada por la dirección de $\sum \vec{F}$ y su magnitud dada por el producto de la fuerza neta y la masa del objeto.

Para poder relacionar el impulso con el momento lineal, regresemos a la segunda ley de newton planteada en términos de momento lineal.
Si $\sum \vec{F}$ es constante, por lo tanto $\frac{d\vec{p}}{dt}$ también será constante, así que $\frac{d\vec{p}}{dt}$ es igual al total de momento lineal $\vec{p}_{2}-\vec{p}_{1}$ durante el lapso $t_{2}-t_{1}$:
$$
\sum \vec{F}=\frac{\vec{p}_{2}-\vec{p}_{1}}{t_{2}-t_{1}}
$$
Ahora si pasamos a multiplicar el cambio de tiempo:
$$
\sum \vec{F}(t_{2}-t_{1})=\vec{p}_{2}-\vec{p}_{1}
$$
Esta expresión es la que anteriormente definimos como el impulso, por lo tanto obtenemos el resultado conocido como el **teorema del impulso y el momento lineal**:
$$
\vec{J}=\vec{p}_{2}-\vec{p}_{1}
$$
Este teorema se cumple incluso si la fuerza no es constante, podemos demostrar esto si tomamos a la suma de las fuerzas como variable $\sum \vec{F}=\frac{d\vec{p}}{dt}$, e integramos:
$$
\int _{t_{1}}^{t_{2}} \sum \vec{F} \, dt=\int _{t_{1}}^{t_{2}} \frac{d\vec{p}}{dt} \, dt =\int _{\vec{p}_{1}}^{\vec{p}_{2}} \, d\vec{p}= \vec{p}_{2}-\vec{p}_{1} 
$$
Por lo tanto, la integral anterior es igual al impulso, así que, generalizando:
$$
\vec{J}=\int_{t_{1}}^{t_{2}} \sum \vec{F} \, dt 
$$

## Comparación entre momento lineal y energía cinética

La energía cinética y el momento lineal pueden tener ciertas similitudes entre ellas, sin embargo, estas no son iguales ni mucho menos, pero se pueden obtener información a partir de las características que ellas comparten.
El trabajo, como vimos en [[Trabajo y energía cinética]] se puede expresar como la diferencia de energía cinética del sistema, y la energía cinética como $K=\frac{1}{2}mv^{2}$.
Si tenemos un cuerpo de masa $m$ que parte del reposo (es decir $v_{1}=0$) entonces tanto la energía cinética inicial como el momento lineal inicial del cuerpo es 0, donde una fuerza constante $\vec{F}$ actúa sobre el cuerpo, se mueve en un intervalo de tiempo $\Delta t$, desde un punto $x_{1}$ a un punto $x_{2}$. Por ecuaciones tenemos que:
$$
\vec{p}_{2} =\vec{p}_{1}+\vec{J}=\vec{J}
$$
Entonces podemos afirmar que la potencia de un cuerpo es igual al impulso que actuó sobre el objeto a partir del reposo hasta la rapidez actual, entonces el impulso es el producto de la fuerza por el tiempo requerido para acelerarlo. Mientras que con el trabajo es el producto de la fuerza por la distancia, y la energía cinética en $t_{2}$ es igual al trabajo total efectuado sobre la partícula para moverla desde el reposo.

## Conservación del momento lineal

Si existen dos objetos que interactúan entre sí, el concepto de momento lineal toma una gran importancia.
Para entender el porque, imaginemos un sistema ideal en donde dos cuerpos interactúan entre ellos, como dos astronautas que flotan en el espacio uno a otro, al impactar, gracias a la tercera ley de newton podemos afirmar que la fuerza contraria realizada por el choque es de la misma magnitud pero de signo contrario a la fuerza con la que se realizo el choque, por lo tanto el *impulso* entre ellos es de misma magnitud y opuestos en sentido.
Evaluemos lo anterior con ciertos términos nuevos.
A las fuerzas realizadas por la interacción de los objetos la denominaremos **fuerzas internas**, mientras que las fuerzas ejercidas por cualquier otro medio serán consideradas como **fuerzas externas**. En el ejemplo de los astronautas no existía ninguna fuerza externa, por lo tanto es un sistema aislado.

Si se posee un sistema cuyas fuerzas externas sea 0, entonces se afirma que el momento lineal de todas las partículas pertenecientes al sistema será constante, esto debido a:
$$
\sum F_{ext}  = \frac{d\vec{p}}{dt}=\frac{d}{dt}\left( \sum\vec{p} \right)=0
$$
Como lo vimos anteriormente, esto sigue funcionando sin importar la cantidad de partículas con momento, si la suma de las fuerzas externas es 0.



> [!important] Revelación
> Gracias a esto, si la suma de las fuerzas externas es 0, entonces el cambio del momento lineal en el sistema será 0, por lo tanto el momento lineal del sistema al inicio, será exactamente igual al momento lineal del sistema final.
> $$
\sum \vec{F}=0\,\Rightarrow\,m_{a_{0}}v_{a_{0}}+m_{b_{0}}v_{b_{0}}+\dots=m_{a_{f}}v_{a_{f}}+m_{b_{f}}v_{b_{f}}+\dots $$


### Conservación en las componentes

Si el momento lineal se conserva en todo el sistema, entonces el momento se conservará en cada una de las componentes del movimiento:
$$
\begin{align*}
\vec{p}_{x}&=p_{ax}+p_{bx}+\dots\\
\vec{p}_{y}&=p_{ay}+p_{by}+\dots\\
\vec{p}_{z}&=p_{az}+p_{bz}+\dots
\end{align*}
$$
Si la suma de las fuerzas externas es 0, entonces $P_{x},\,P_{y},\,P_{z}$ son constantes.

