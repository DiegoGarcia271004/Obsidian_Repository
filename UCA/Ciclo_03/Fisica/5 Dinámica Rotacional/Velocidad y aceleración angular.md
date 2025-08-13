---
tags:
  - Física
---
Para poder entender y analizar el movimiento de rotación, pensemos que un cuerpo rígido se encuentra girando alrededor de un eje fijo ubicado en un sistema de referencia el cual en ningún momento cambiará su posición relativa al marco, el cual podría representarse de la siguiente manera mediante la aguja de un velocímetro de un carro:
![[DR1.png|center|300]]
En la imagen se puede observar la aguja de velocidad rotando alrededor del eje ubicado en el punto $O$, y a su vez es perpendicular al plano $xy$, es decir que esta apuntando hacia afuera de la pantalla.

Si queremos seguir el trazo del movimiento de la aguja necesitamos encontrar una forma de describir su movimiento, con este fin existen dos formas de describirlo, la primera es llevando control del sistema de coordenadas del punto $P$, sin embargo este es un método que no es del todo conveniente, por lo que podemos recurrir al segundo método. Podemos observar que en todo momento de la rotación se mantiene a la misma distancia del punto $O$, lo único que cambia es el ángulo $\theta$, el cual nos indica el ángulo que existe entre el segmento $PO$ hasta el eje positivo de las $x$, por lo que podemos tomar únicamente esta variable $\theta$ como nuestro indicador de la posición del objeto.

Esta variable angular puede ser positiva si el movimiento describe una trayectoria antihoraria, y negativa si describe un movimiento en sentido horario.

Es importante remarcar que esta medida angular, será tomada en radianes, y se asume que el lector es lo suficientemente culto en cálculo como para no tener que explicar que es y el porque de su uso.

--- 

## Velocidad angular

Retomando el ejemplo de la manecilla de velocidad, ya que $\theta$ nos indica la posición angular del objeto en un momento específico, la distancia recorrida por la manecilla será dada por la diferencia entre la posición angular final e inicial del cuerpo es decir: $\Delta \theta=\theta_{2}-\theta_{1}$.
Ahora, si queremos definir el cambio de posición de un cuerpo en rotación en un periodo de tiempo $\Delta t = t_{2}-t_{1}$, por lo tanto, la velocidad angular será dada por la razón de la variación de distancia angular respecto al tiempo:
$$
\omega_{med}=\frac{\Delta\theta}{\Delta t}=\frac{\theta_{2}-\theta_{1}}{t_{2}-t_{1}}
$$
Si queremos obtener esta velocidad en un instante específico de la partícula, podemos hacer lo que hemos estado haciendo en las ocasiones anteriores y hacer que $\Delta t \to 0$:
$$
\omega=\lim_{ \Delta t \to 0 }  \frac{\Delta\theta}{\Delta t} = \frac{d\theta}{dt}
$$
De igual forma al ángulo, la velocidad angular puede cambiar de signo dependiendo de la dirección en la que rote el objeto. Sin embargo, de igual forma que en cinemática ordinaria, la rapidez (la magnitud de la velocidad) no puede ser negativa.

### Velocidad angular como vector

Si recordamos, la notación para representar la velocidad angular del objeto alrededor del eje $z$ es $w_{z}$, la cual puede recordar a como denotábamos la componente horizontal del vector velocidad de una partícula en el eje $x$, de la misma manera, $\omega_{z}$ nos indica la componente de la velocidad angular $\vec{\omega}$ respecto al eje de rotación, esta se puede entender de la siguiente manera tomando en cuenta la regla de la mano derecha:
![[Rota.png]]
Por el momento se trabajara con el eje de rotación fijo, por lo que solamente poseerá componentes en el eje $z$, por lo tanto será positivo si gira en sentido antihorario y negativo si va en sentido horario.

--- 
## Aceleración angular

Si para un cuerpo rígido la velocidad angular varía respecto al tiempo, entonces se esta produciendo una aceleración angular, ya sea para aumentar la velocidad de rotación o para disminuirla.
Si $\omega_{1}$ y $\omega_{2}$ son velocidades angulares instantáneas en en $t_{1}$ y $t_{2}$, entonces se define la aceleración angular media $\alpha_{med}$ en el intervalo $\Delta t=t_{2}-t_{1}$ como la velocidad angular dividido por el intervalo $\Delta t$:
$$
\alpha_{med} =\frac{\omega_{2}-\omega_{1}}{t_{2}-t_{1}}=\frac{\Delta \omega}{\Delta t}
$$
Aplicando el truco del almendruco:
$$
\alpha=\lim_{ \Delta t \to 0 } \frac{\Delta\omega}{\Delta t}=\frac{d\omega}{dt}
$$
Como el lector se podrá percatar, estas formas son similares a las vistas en el capitulo de cinemática, siendo $\theta$ la posición, $\omega$ la velocidad y $\alpha$ la aceleración.
Estas comparten características con sus contrapartes lineales, a su vez la velocidad se comporta de la misma manera, si el sentido de la aceleración es igual que el de la velocidad, la velocidad aumenta, pero si es de sentido contrario, esta disminuirá.

---
## Rotación con aceleración angular constante

Para la rotación, las reglas que vimos en la unidad de cinemática se cumplen en su totalidad de manera similar al movimiento rotacional, es decir, que las fórmulas que se utilizarán para movimiento rotacional son las mismas que las vistas en [[1.2 Aceleración media e instantánea#Ecuaciones de movimiento con aceleración constante|cinemática de la partícula]], con la diferencia de que ahora se utilizarán las variables de movimiento rotacional:

$$
\begin{align*}
\alpha _{z}&=\text{Constante}\\
\omega_{z}&=\omega_{0z}+\alpha_{z}t\\
\theta&=\theta_{0}+\omega_{0z}+\frac{1}{2}\alpha\\
\omega_{z}^{2}&=\omega_{0z}+2\alpha_{z}(\theta-\theta_{0})\\
\theta-\theta_{0}&=\frac{1}{2}(\omega_{0z}+\omega_{z})t
\end{align*}
$$
---
## Relación entre cinemática lineal y angular

Para poder seguir en nuestro estudio sobre la rotación, es necesario que podamos conocer el como podríamos obtener velocidad y aceleración lineal a partir de lo que ya conocemos acerca de la rotación de un cuerpo rígido. El obtener estos valores nos permitirá la obtención de algunos datos importantes. Por ejemplo, si queremos obtener la energía cinética en un momento, entonces es necesario utilizar la expresión $K=\frac{1}{2}mv^{2}$, para la cual es necesaria obtener el valor de la velocidad lineal $v$, es por eso que en la siguiente sección buscaremos como obtener estos valores.

### Rapidez lineal en la rotación de un objeto fijo

Al momento que un objeto rota sobre su propio eje, todas las partículas que lo conforman rotan de la misma manera alrededor del eje, por lo tanto podemos concluir que la velocidad lineal de todas estas partículas será directamente proporcional a la velocidad angular de la rotación.

Para poder entender esto, partamos de la ecuación de la distancia durante la rotación:
$$
s=r\theta
$$
Si obtenemos un cambio de estas variables respecto al tiempo, podemos obtener lo siguiente:
$$
\begin{align*}
\frac{ds}{dt}&=r \frac{d\theta}{dt}\\
v&=r\omega
\end{align*}
$$
Debido a que para una partícula dada se mantiene un radio constante, se puede sacar de la derivada.
