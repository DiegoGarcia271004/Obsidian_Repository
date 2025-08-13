---
tags:
  - EMA
---
# Preguntas y temas

1. [[Temario parcial (con número de pregunta y todo) + Resumen#Reglas de Kirchhoff|Reglas de Kirchhoff]]
2. [[Temario parcial (con número de pregunta y todo) + Resumen#Circuitos RC|Circuitos RC]]
3. [[Temario parcial (con número de pregunta y todo) + Resumen#Circuitos RC|Circuitos RC]]
4. [[Temario parcial (con número de pregunta y todo) + Resumen#Campos magnéticos Fuerza sobre una carga en movimiento|Fuerza sobre una carga en movimiento]]
5. [[Temario parcial (con número de pregunta y todo) + Resumen|Fuerza sobre una carga en movimiento]]
6. [[Temario parcial (con número de pregunta y todo) + Resumen#Fuerza magnética sobre un conductor que transporta corriente|Fuerzas magnéticas]]
7. [[Temario parcial (con número de pregunta y todo) + Resumen#Fuentes del campo magnético|Fuentes del campo magnético]]
8. [[Temario parcial (con número de pregunta y todo) + Resumen#Ley de Ampere|Ley de Ampere]]
9. [[Temario parcial (con número de pregunta y todo) + Resumen#Ley de Ampere|Ley de Ampere]]
10. Flujo magnético
11. Faraday y FEM inducida
12. FEM en movimiento
13. Ley de Lenz
14. Ley de Faraday con campo eléctrico
15. Leyes de Maxwell (why do I hear boss music??)

---

# Resumen de los temas


## [[Reglas de Kirchhoff]]

Las reglas de Kirchhoff son de gran ayuda para trabajar con circuitos más complejos que no se pueden expresar en resistencias o capacitancias equivalentes, o circuitos con más de una FEM.
### Primera regla

Para cualquier nodo de un circuito se cumple que la suma algebraica de las corrientes entrantes  y salientes a este serán igual a 0.
$$
\boxed{\sum I=0}
$$
### Segunda regla

Para cualquier sub-malla (o malla cerrada en general) de un circuito se cumple que al recorrer toda la malla, la suma algebraica del potencial será igual a 0.
$$
\boxed{\sum V=0}
$$
---

## [[Circuitos RC]]

Los circuitos RC son una variación de los circuitos convencionales que incluyen resistencias y capacitores, este está dividido en dos etapas: La carga del capacitor y la descarga del capacitor.

### Carga del capacitor

**Idealmente** si no hay resistencias, entonces el capacitor se carga en el mismo instante en el que la FEM se conecta, pero cuando el circuito incluye resistencias, estas ejercen una caída de potencial lo que puede variar el tiempo en el que el capacitor se descarga.

Cuando el circuito RC no está conectado a una FEM, por convención en $t=0$ la carga del capacitor es 0 y no existe una corriente dentro del circuito.
Una vez la FEM se conecta al circuito, una corriente se genera y el capacitor se empieza a cargar mientras que la resistencia genera una caída de voltaje lo que frena la corriente que pasa al capacitor.
Conforme el capacitor se carga, este aumenta su voltaje hasta llegar al mismo valor de la FEM, una vez se alcanza este valor, la corriente que pasa por el circuito es 0. Si utilizamos la regla de Kirchhoff durante este lapso en que se carga el capacitor, la expresión que lo representa es la siguiente:
$$
\varepsilon=iR+\frac{q}{C}
$$
Teniendo en cuenta que la intensidad es la diferencia de la carga respecto al tiempo, entonces se puede expresar de la siguiente manera:
$$
\varepsilon=\frac{dq}{dt}R+\frac{q}{C}
$$
La cual resulta en una ecuación diferencial de primer grado (se anima al lector a hacerla por su cuenta), que al resolverla se obtiene:
$$
\boxed{q(t)=C\varepsilon(1-e^{-t/RC})}
$$
A partir de esta expresión, podemos llegar a diversas conclusiones:

- Si $t=0$ la carga del capacitor es 0, esto debido a que el sistema se encuentra descargado.
- En $t\to\infty$ (usualmente expresado como que ha pasado mucho tiempo), la carga del capacitor será igual a $C\varepsilon$, implicando la carga total del capacitor.
- Cuando $t=RC$ el capacitor será $C\varepsilon(1-e^{-1})$, por lo que el capacitor estará cargado en un $63.2\%$ 

### Descarga del capacitor

Es este momento, el capacitor se encuentra completamente cargado, por lo que la batería se desconecta del circuito, dejándonos únicamente la FEM almacenada en el capacitor, y a su vez, la corriente generada por la descarga del capacitor será en el sentido contrario en la que corría con la batería conectada.

En este momento, la FEM será únicamente producida por el capacitor, por lo que si seguimos las reglas de Kirchhoff, entonces obtenemos la siguiente expresión:
$$
V_{c}=-IR
$$
Como decíamos, la corriente irá en sentido contrario a la original, de esta forma, obtenemos de vuelta una ecuación diferencial:
$$
\frac{q}{C}=-\frac{dq}{dt}R
$$
Al resolverla, obtenemos una expresión para la descarga del capacitor:
$$
\boxed{q(t)=C\varepsilon e^{-t/RC}}
$$

De igual forma, podemos extraer cierta información al expresar la carga del capacitor de esta forma.

- Si $t=0$, entonces la carga del capacitor es máxima, ya que está completamente cargado.
- Si $t\to \infty$, entonces el capacitor se encuentra completamente descargado, ya que se descargó (duh).
- Si $t=RC$, entonces el capacitor se encuentra a un $36.8\%$ de su capacidad.

### Corriente del circuito

Si hemos obtenido la carga del capacitor mientras se descarga, de igual forma podemos encontrar la forma de expresar la intensidad de corriente del circuito.
Recordemos que la intensidad es el cambio de la carga del circuito:
$$
I=\frac{dq}{dt}
$$
Por lo que si tenemos una función de la carga respecto al tiempo, al derivarla deberíamos obtener la función de la intensidad:
$$
I(t)=-\frac{\varepsilon}{R}e^{-t/RC}
$$
### Potencial en el circuito

El potencial en el circuito inicia como el mismo que el del capacitor, pero irá disminuyendo respecto al tiempo hasta llegar a 0, por lo que:
$$
V_{c}(t)=\varepsilon e^{-t/RC}
$$
### Voltaje en el resistor

Como establecimos anteriormente, el voltaje del capacitor, será de igual magnitud pero con distinto signo que el del resistor, por lo que:
$$
V_{R}(t)=-\varepsilon e^{-t/RC}
$$
---


## [[Campos magnéticos|Fuerza sobre una carga en movimiento]]

Al trabajar con el campo magnético, este afecta a cargas únicamente si estas se encuentran en movimiento, es decir que para una carga estática, esta no se ve afectada por el campo magnético.
Por lo que el campo magnético ejercerá una fuerza sobre una carga en movimiento proporcional a **la magnitud del campo magnético**, **a la velocidad que posea la partícula** y **a la componente perpendicular al campo magnético de la velocidad**.

Por lo que la fuerza que es ejercida por el campo magnético sobre esta es igual a:
$$
\boxed{\vec{F}=q\vec{v}\times \vec{B}}
$$
Como podemos ver, estamos trabajando con la carga de la partícula por lo que tomaremos su signo y esto afectara a la dirección de la fuerza, es decir, si es una carga positiva, entonces seguirá la regla de la mano derecha.
En cambio si esta es una carga negativa, seguirá el inverso de la mano derecha. Es decir que si seguimos la regla con una carga negativa, y la fuerza nos apunta hacia arriba, entonces la fuerza realmente irá para abajo.

### Movimiento de partículas cargadas en un campo 

Como vimos anteriormente, si una partícula cargada se mueve dentro de un campo magnético, entonces existe una fuerza perpendicular a la velocidad de la partícula y el campo magnético. Pero si el campo se mantiene constante apuntando al plano donde se mueve la partícula, la fuerza siempre será perpendicular a la velocidad, por lo que la fuerza solo se mantendrá cambiando la dirección de la partícula, más no alterando su velocidad, es decir que el movimiento de la partícula solamente mantiene una componente radial de la aceleración, más no tangencial, es decir que la trayectoria que formaría sería la de una circunferencia. 

Recordando la segunda ley de Newton:
$$
F=ma 
$$
Pero en este caso, sabemos que la aceleración de la fuerza es únicamente radial, por lo que cumple:
$$
a=\frac{v^{2}}{R}
$$
Donde $v$ es la velocidad a la que se mueve la partícula y $R$ es el radio de la circunferencia que forma.
Con esto en mente:
$$
F=m \frac{v^{2}}{R}
$$
Y como ya conocemos cual es el valor de la fuerza producida por el campo magnético:
$$
qvB=m \frac{v^{2}}{R}
$$
simplificando:
$$
\boxed{R=\frac{mv}{qB}}
$$

Y pues como somos bien, pero que bien enfermos. Entonces podemos aplicar esta ecuación a todo el movimiento angular:
$$
\omega=\frac{v}{R}=v \frac{qB}{mv}=\frac{qB}{m}
$$
$$
f=\frac{\omega}{2\pi}=\frac{qB}{2\pi m}
$$
$$
T=\frac{1}{f}=\frac{2\pi m}{qB}
$$
---

## Fuerza magnética sobre un conductor que transporta corriente

Anteriormente, hemos descrito la fuerza magnética sobre una partícula cargada, siendo que esta depende de la velocidad de dicha partícula. 
Sin embargo, en la vida real no se trabajan con partículas singulares, por lo que necesitamos una forma de encontrar la fuerza magnética en flujos de carga mayores.

Pero no podemos simplemente ignorar el conocimiento sobre partículas cargadas, sino que utilizaremos lo planteado para generalizarlo a cualquier tipo de carga.

Planteemos un cable que posee una flujo de carga, sabemos que la carga se mueve a través del cable a una velocidad $v_{b}$, pero estas cargas se mueven en conjunto sobre todo el cable, por lo que esto genera una corriente eléctrica. Así que como un paralelismo a la velocidad de la partícula, tenemos la intensidad de corriente.

Finalmente como una expresión generalizada para la fuerza magnética tenemos:
$$
\boxed{\vec{F}=I\vec{l}\times \vec{B}}
$$
Donde $I$ es la intensidad, $\vec{l}$ es el vector longitud del cable y $\vec{B}$ el campo magnético.

Esto se da para un alambre recto, pero si tenemos un cable con una forma irregular, podemos dividirlo en pequeñas fracciones de longitud y obtener el campo magnético de ese punto, y sumarlos todos, por lo que podemos tener:
$$
B=I\int d\vec{l}\times \vec{B} 
$$
o en su forma diferencial:
$$
\boxed{d\vec{B}=Id\vec{l}\times \vec{B}}
$$
---


## Fuentes del campo magnético

### Partículas cargadas

Ya establecimos anteriormente que un campo magnético afectará a una partícula solamente si esta se encuentra en movimiento. Pero ¿Por qué es que sucede esto? Esto es debido a que el campo magnético se comporta de manera similar al campo eléctrico al momento de interactuar con otros objetos y es que el campo magnético no es que haga algún efecto sobre la partícula, sino que la partícula posee un campo magnético y el campo externo hace efecto sobre este otro campo magnético:
$$
\text{partícula} \stackrel{\text{genera}}{\Longrightarrow}\text{Campo A}\stackrel{\text{afecta}}{\iff} \text{Campo B} \stackrel{\text{genera}}{\Longleftarrow}\text{partícula}
$$
Bajo esta premisa, si una partícula en movimiento es afectada por un campo magnético, entonces la partícula en movimiento debe crear un campo magnético.

Una de las características del campo magnético producido por una partícula cargada en movimiento, es que este siempre formará circunferencias perpendiculares a la velocidad de la partícula.

Si se quiere obtener cual es el valor del campo eléctrico producido por una partícula en movimiento en un punto, es necesario entender que el campo magnético es un campo vectorial que forma circunferencias perpendiculares a la velocidad de la partícula, por lo que la dirección en la que se encuentra el punto y la dirección de la velocidad a donde se dirige la partícula es muy importante para los cálculos, ya que no solo debemos conocer la magnitud del campo, sino hacia donde se dirige en este punto.

![[Campo|center]]
Por esto mismo, debemos conocer el vector director de la posición de la partícula $\vec{r}$, y el vector velocidad $\vec{v}$.
Con lo que podemos obtener tanto la magnitud como la dirección del vector del campo magnético en ese punto con la siguiente expresión:
$$
\boxed{\vec{B}=\frac{\mu_{0}}{4\pi} \frac{q\vec{v}\times \vec{r}}{r^{2}}}
$$

### Elemento de corriente

De igual forma que con la fuerza, usualmente no solemos encontrar partículas cargadas en la vida real, sino más bien elementos de que poseen corriente y estas, de igual forma, crean campos magnéticos, por lo que si se quiere obtener el campo magnético producido por un elemento de corriente en un punto, se utiliza la siguiente expresión:
$$
\boxed{d\vec{B}=\frac{\mu_{0}}{4\pi} \frac{Id\vec{l}\times \vec{r}}{r^{2}}}
$$
Mediante la utilización de esta ecuación, podemos encontrar el valor y dirección del campo magnético de distintos cuerpos:

1. Campo de un conductor recto y largo:
$$
\boxed{B=\frac{\mu_{0}I}{2\pi r}}
$$
2.  Fuerza entre conductores paralelos
$$
\boxed{\frac{F}{L}=\frac{\mu_{0}II'}{2\pi r}}
$$
3. Campo dentro de una espira conductora:
$$
\boxed{B=\frac{\mu_{0}NI}{2r}}
$$

---

## Ley de Ampere

La ley de Ampere establece una integral de línea cerrada sobre el campo magnético, y que el resultado de esta integral cuando exista una corriente en el interior de la "superficie" amperiana será igual al producto entre la constante magnética y la intensidad de corriente:
$$
\boxed{\oint \vec{B}\cdot d\vec{l}=\mu_{0}I_{enc}}
$$
Esta puede tener una similitud con respecto a la Ley de Gauss, con la gran diferencia que en este caso es una *curva* cerrada, al contrario de la ley de Gauss para electrostática que establece una **superficie**. Esto debido a la misma ley de Gauss para el magnetismo, ya que esta si se establece en una superficie cerrada.

Con la ley de ampere se puede simplificar en gran manera el proceso de encontrar el campo magnético de un generador de campo magnético sin la necesidad de la ley de Biot y Savart, ya que solamente necesitamos una curva cerrada y encontrar de esta forma el campo magnético.

Es de suma importancia entender que la ley de ampere se cumple para toda curva cerrada con **corriente en su interior**, si no existe ninguna corriente en el interior de la figura, entonces la integral de línea dará 0.

### Una corriente encerrada

Otro punto importante, es que con la integral de línea, al plantear la curva amperiana esta sigue un sentido, y esto influye en el resultado.

Si el campo magnético producido por la corriente interna gira en el mismo sentido que el de la curva planteada, entonces el resultado será:
$$
\oint\vec{B}\cdot d\vec{l}=\mu_{0}I_{enc}
$$
Sin embargo, si la curva va en sentido contrario a la dirección del campo eléctrico, entonces será de misma magnitud pero de signo contrario:
$$
\oint\vec{B}\cdot d\vec{l}=-\mu_{0}I_{enc}
$$
### Varias corrientes encerradas

Si dentro de la curva amperiana tenemos más de una corriente la ley se sigue cumpliendo, como se estableció, la corriente que se utilizará en la ley es la **corriente encerrada en la curva**, por lo que si se tienen varias corrientes encerradas, la corriente que se utilizará en la ley será la suma algebraica de las corrientes.

Para esta suma se deberá seguir las reglas vistas en la sección anterior. Si la corriente se encuentra en el sentido contrario al sentido de la curva amperiana, entonces su signo será negativo, mientras que si va en el mismo sentido, entonces será positivo.

**Ejemplo:**
![[Ley de Ampere|center]]

En la imagen tenemos una figura cerrada $l$, y dentro de ella tenemos encerradas 3 corrientes y una afuera de la curva. Si queremos obtener la integral de línea del campo magnético entonces tendremos que obtener la corriente encerrada.

Primeramente, la ley de ampere solo toma en cuenta las corrientes encerradas dentro de la curva cerrada, por lo que la $I_{4}$ que no se encuentra adentro no se tomará en cuenta.

Ya que sabemos que solo tomaremos en cuenta las corrientes $I_{1},\,I_{2}\,\text{y }I_{3}$, entonces la corriente encerrada deberá ser:
$$
I_{enc}=I_{1}+I_{2}+I_{3}
$$
Pero tenemos que tener en cuenta que la $I_{2}$ se encuentra entrando a la figura, por lo que para conocer el sentido de su campo magnético utilizaremos la regla de la mano derecha, el cual nos dice que su campo gira en sentido horario, lo que es en sentido contrario a la formación de la curva amperiana, por lo que sabemos que su signo será negativo.

Finalmente podemos llegar a una expresión de la corriente total, y por consecuente a una expresión para la intensidad de corriente:
$$
\begin{align*}
I_{enc}&=I_{1}-I_{2}+I_{3}\\
\oint\vec{B}\cdot d\vec{l}&=\mu_{0}(I_{1}-I_{2}+I_{3})
\end{align*}
$$

