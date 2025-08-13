---
tags:
  - Física
---
Anteriormente hemos podido trabajar con movimientos de traslación lineal, hemos abordado la energía necesaria para realizar un trabajo el cual involucraba un desplazamiento de una partícula.
Pero, ¿Qué pasa si lo que estamos haciendo es mover un cuerpo rígido en un movimiento de rotación? Bueno, pues estamos trabajando con lo que denominamos **torque**.

Si queremos inducir un cuerpo a un movimiento de rotación a partir de su estado natural, lógicamente si utilizamos las leyes de Newton, nos vemos en la necesidad de aplicar una fuerza para poder realizar este movimiento.
Si tomamos como ejemplo intentar aflojar una tuerca de un tornillo, usualmente se utiliza una llave inglesa si queremos facilitar el proceso de realizar esta acción (más adelante profundizaremos más en porque razón se facilita más el utilizarla), al hacer uso de la llave inglesa, aplicamos una fuerza, esta fuerza es aplicada sobre el mango de la llave, y al aplicar la fuerza, el tornillo empieza a girar, por ende estamos realizando torque para poder girar tanto el tornillo como la llave.
Empíricamente si al utilizar la llave ejercemos fuerza en el lado más alejado del brazo de la llave, necesitamos menor fuerza para poder empezar a girar la tuerca, por lo contrario, si agarramos la llave más cerca del tornillo, es necesario aplicar una mayor fuerza sobre la llave para poder realizar el mismo movimiento de la tuerca; A partir de esto, podemos decir que a mayor distancia que se aplique la fuerza del eje de rotación, menor fuerza se necesita para realizar el torque, así que el torque es directamente proporcional a la distancia que se aplica la fuerza con respecto al eje de rotación, definiendo así, el torque, el cual se representa como la letra griega tau ($\tau$):
$$
\tau=F\cdot d
$$
Gracias a esta ecuación, podemos ver que si queremos ejercer cierta cantidad de torque, la fuerza crecerá inversamente proporcional a la distancia respecto al eje de rotación donde se aplique, a esta distancia se le conoce como brazo de palanca.


> [!important] Unidades de medida
> Si realizamos el análisis dimensional de la ecuación del torque, podemos concluir que sus unidades son Newton-metro $Nm$ o también como hemos trabajado anteriormente, Joules ($J$).
> Sin embargo, para la torca, no se utilizan los Joules, ya que no se trata de energía o trabajo, sino que se utilizarán simplemente Newton-metro.


---
## Fuerza en el torque

En el torque, la dirección de la fuerza es importante para su realización. Para que una fuerza aporte para la realización del torque, esta debe ser imperativamente perpendicular al vector posición del brazo de palanca, por eso mismo, si se aplica una fuerza en cualquier otra dirección respecto al vector de posición, entonces solamente se tomará en cuenta la componente perpendicular a este.
Con este fin, en el dado caso que la fuerza no se encuentre inicialmente perpendicular al vector de posición, entonces debemos intentar encontrar el valor del ángulo entre la fuerza y el vector de posición, a este ángulo le llamaremos $\phi$.
![[UCA/Ciclo_03/Fisica/Anexos/Diagramas/Torque|center|500]]

Y debido a que buscamos la fuerza que nos interesa (que es la componente vertical), entonces utilizaríamos $F\sin \phi$ con el fin de obtenerla, y esta sería la fuerza que utilizaríamos para obtener el torque.

---
## Torque como vector

Como hemos visto en [[Velocidad y aceleración angular|dinámica del momento rotacional]], sabemos que si un cuerpo rígido rota en el sentido antihorario, entonces posee una rotación positiva y viceversa con el otro sentido. De igual manera, el sentido del torque se ve afectado por la misma rotación, y de igual manera que con la velocidad angular y aceleración angular, el torque también es un vector que se encuentra perpendicular al plano $xy$; Por ende en el ejemplo anterior, el torque se encuentra en el eje de rotación de la palanca y atraviesa la pantalla.
Al igual que con las dos magnitudes de velocidad y aceleración angular, se aplica la regla de la mano derecha con respecto a la torca positiva y negativa.

---
## Torca y aceleración angular de un cuerpo rígido

En capítulos anteriores hemos podido trabajar con diversas fuerzas que son aplicadas sobre un cuerpo, esto haciendo que el cuerpo se mueva o se mantenga en reposo, pero, ¿Qué pasa si estas fuerzas ahora generan un torque sobre el cuerpo en cuestión? pues es lo que nos propondremos a encontrar en esta sección.

Para empezar, tenemos que recordar la definición de torque, el cual es un producto entre la longitud del brazo de rotación y la fuerza tangencial aplicada sobre una la partícula de un cuerpo ($\vec{\tau}=\vec{r}\,F_{\tan}$), pero, la fuerza tangencial es posible expresarla como la masa de la partícula por la aceleración tangencial de la misma, $F_{\tan}=m_{1}a_{\tan}$, a su vez, teniendo en cuenta que la aceleración tangencial es dada por el producto entre la longitud del brazo de rotación y su velocidad angular ($a_{\tan}=\vec{r}\,\alpha_{z}$)  sustituyendo esto en la ecuación del torque anterior obtenemos:
$$
\begin{align*}
\vec{\tau}&=\vec{r}\,m_{1}\,\vec{r}\,\alpha_{z}\\
\vec{\tau}&=m_{1}\,\vec{r}^{2}\,\alpha_{z}
\end{align*}
$$
Siendo esto el torque realizado sobre la partícula de un cuerpo. Sin embargo, si queremos obtener el torque neto aplicado sobre un cuerpo, es necesario la suma de todos los torques sobre todas las partículas de este, ya que la aceleración angular es la misma para todos, podemos obtener:
$$
\begin{align*}
\sum\vec{\tau}&=\sum(m\,\vec{r}^{2})\,\alpha_{z}\\
\sum m\,\vec{r}^{2}&=I\\
\sum \vec{\tau}&=I\alpha_{z}
\end{align*}
$$
Siendo este el torque neto sobre un cuerpo, y a su vez siendo una analogía a la segunda ley de Newton, donde $\sum \vec{F}=ma$.

Cabe aclarar que al asumir que la aceleración angular es constante para todas las partículas del cuerpo, esta ecuación se cumple solamente cuando es un cuerpo rígido.

