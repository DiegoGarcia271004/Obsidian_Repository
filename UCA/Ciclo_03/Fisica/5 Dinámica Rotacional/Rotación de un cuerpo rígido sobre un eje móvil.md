---
tags:
  - Física
---
## Energía cinética de un cuerpo en rotación y movimiento

Si bien podemos encontrar varios objetos rígidos que rotan en su propio eje mientras se encuentran quietos como podría ser una polea, también es posible encontrar objetos que rotan a la vez que se están desplazando, uno de los ejemplos más famosos, es el movimiento de la tierra, el cual se encuentra rotando en su propio eje, a la vez que realiza un movimiento de traslación alrededor del sol.

Para los casos donde un cuerpo rote y se desplace al mismo tiempo, su energía cinética poseerá dos componentes, la energía de rotación y la energía de traslación, representado cuantitativamente con la siguiente ecuación:
$$
K=\frac{1}{2}Mv_{cm}^{2}+\frac{1}{2}I_{cm}\omega^{2}
$$
Donde $M$ es la suma de las masas de todas las partículas pertenecientes al cuerpo, $v_{cm}$ la velocidad del centro de masa, $I_{cm}$ el momento de inercia del centro de masa y $\omega$ la velocidad angular del cuerpo.

---

## Rodar sin resbalar

Una condición fundamental para el cumplimiento de un cuerpo rígido en movimiento tanto rotacional como de traslación, esto dado por que el punto donde el cuerpo posea interacción con otro cuerpo, tanto la velocidad del centro de masa como la velocidad relativa al cuerpo (velocidad de rotación) posean misma magnitud pero de sentido contrario, de esta forma, en el punto anteriormente mencionado, el cuerpo posee una velocidad neta 0. Por lo tanto, si se posee una rueda (un caso de este estilo de rodamiento) de radio $R$, y una velocidad angular $\omega$, entonces, si la rueda no resbala, se cumple la siguiente ecuación que se vio anteriormente en [[Velocidad y aceleración angular#Rapidez lineal en la rotación de un objeto fijo|la velocidad de rotación de un objeto fijo]]:
$$
v_{cm} = R\,\omega
$$
Y gracias a este comportamiento es posible demostrar la ecuación de energía cinética del apartado anterior, teniendo en cuenta el teorema de ejes paralelos, tenemos que $I_{p}=I_{cm}+MR^{2}$ y si también se tiene en cuenta la energía de la rueda al rotar en un punto distinto al centro de masa como $K=\frac{1}{2}I_{1}\omega^{2}$ entonces:
$$
\begin{align*}
K&=\frac{1}{2}(I_{cm}+MR^{2})\omega^{2}\\
&=\frac{1}{2}I_{cm}\omega^{2}+\frac{1}{2}MR^{2}\omega^{2}\\
v_{cm}&=R\omega\\
&=\frac{1}{2}I_{cm}\omega^{2}+\frac{1}{2}Mv_{cm}^{2}
\end{align*}
$$
De ahí la importancia que se cumpla que la rueda no resbale.


> [!NOTE] Energía potencial
> Cabe aclarar, si el cuerpo se encuentra con un movimiento vertical, el cuerpo es objeto de la [[Energía potencial#Energía potencial gravitatoria|energía potencial gravitatoria]]. Por lo que se debe aplicar la conservación de la energía mecánica del sistema.
> $$
U=mgy_{cm}
>$$
>

---
## Traslación y rotación combinada: Dinámica

Es posible también analizar los movimientos de rotación y traslación desde el punto de vista de la dinámica, sabemos que $\vec{a}_{cm}$ es la aceleración del centro de masa de un cuerpo de masa $M$ en el que se efectúan todas las fuerzas aplicadas en el cuerpo.
$$
\sum \vec{F}=M\vec{a}_{cm}
$$
A su vez, el momento de rotación alrededor del centro de masa se obtiene mediante el análogo rotacional de la segunda ley de Newton:
$$
\sum \vec{\tau}=I_{cm}\alpha_{z}
$$
Es importante mencionar que esta ecuación aún funciona si el centro de masa se encuentra en movimiento, si y solo si se cumplen ciertas condiciones:
1. El eje de rotación que pasa por el eje de rotación debe ser un eje de simetría.
2. El eje de rotación no debe cambiar de dirección.

---

## Trabajo y potencia en movimiento de rotación

Anteriormente pudimos ver en [[Trabajo y energía cinética|trabajo aplicado linealmente]], que al momento de mover un objeto siempre se realiza un trabajo, de igual manera, si se es aplicada una fuerza sobre un cuerpo rígido que hace que este rote de igual manera se esta realizando un trabajo.

Para entenderlo, debemos saber que para hacer rotar un objeto, se necesita aplicar una fuerza tangencial ($F_{\tan}$) en un brazo de rotación ($R$) en un ángulo infinitesimal $d\theta$ en un instante, por lo que el trabajo $dW$ efectuado por la fuerza está dado por:
$$
dW=F_{\tan }R\,d\theta
$$
Por lo visto anteriormente en [[UCA/Ciclo_03/Fisica/5 Dinámica Rotacional/Torque|torque]] sabemos que es igual al producto de la fuerza tangencial por el radio del brazo de rotación:
$$
dW=\vec{\tau}_{z}\,d\theta
$$
Por lo que resolviendo tenemos:
$$
W=\int _{\theta_{1}}^{\theta_{2}} \vec{\tau}_{z} \, d\theta 
$$
Siendo este el trabajo realizado por una torca.

Si tomamos que se realiza una torca constante, entonces el ángulo cambia en una cantidad finita $\Delta \theta=\theta_{2}-\theta_{1}$, lo cual al resolver la ecuación anterior (la integral) hace sentido.

Conectando lo que ya sabemos acerca del trabajo de un cuerpo, sabemos que el trabajo es igual al cambio de energía cinética de un cuerpo, y de igual manera de lo que sabemos de la energía cinética de rotación, por lo tanto:
$$
W_{tot}=\int _{\theta_{1}}^{\theta_{2}} \vec{\tau}_{z} \, d\theta=\frac{1}{2}I\omega_{2}^{2}-\frac{1}{2}I\omega_{1}^{2} 
$$
Si se diera el caso que el cuerpo de igual manera se encontrara realizando un movimiento de traslación, entonces el trabajo total incluiría las ecuaciones de energía cinética de un cuerpo normal sumado a las de energía cinética del cuerpo en rotación, y de igual manera como se mencionó anteriormente, si se encuentra moviéndose verticalmente, o hay intervención de objetos elásticos, entonces se aplica igualmente la energía potencial del sistema.

Esto nos da una ecuación análoga al [[Trabajo y energía cinética#Teorema trabajo-energía|teorema de trabajo y energía]]. Pero, ¿Qué pasa con la potencia? pues, si volvemos a la ecuación antes de aplicar la integral y buscamos obtener las respectivas variaciones respecto a un instante de tiempo:
$$
\begin{align*}
\frac{dW}{dt}&=\vec{\tau}_{z}\, \frac{d\theta}{dt}\\
P&=\vec{\tau}_{z}\omega_{z}
\end{align*}
$$
Entonces podemos encontrar una expresión para la potencia dada por la rotación.

