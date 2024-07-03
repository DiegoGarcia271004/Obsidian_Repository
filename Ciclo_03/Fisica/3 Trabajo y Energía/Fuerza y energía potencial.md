---
tags:
  - Física
---
En el estudio de los dos tipos de [[Fuerzas conservativas y no conservativas|fuerzas conservativas]] (conservativa y elástica), hemos definido a partir del comportamiento de la fuerza una expresión para su energía potencial, como ejemplo un cuerpo de masa $m$ en un campo gravitacional, la fuerza gravitatoria esta dada por $F=-mg$, y a partir de esta expresión deducimos que la energía potencial gravitatoria es $U_{grav}=mgy$. De igual manera para un resorte, definimos que se necesita (de forma generalizada) una fuerza $F=kx$, y gracias a la tercera ley de Newton, pudimos definir que la energía potencial elástica de un resorte es $U_{el}=\frac{1}{2}kx^{2}$.
Sin embargo, al seguir estudiando la física es posible llegar a encontrarse expresiones de energía potencial respecto a la posición, y a partir de estas expresiones se busca encontrar la fuerza correspondiente, 

Para saber como obtener la fuerza a partir de una expresión de energía potencial, consideremos un movimiento rectilíneo en el eje $x$, y podemos obtener una expresión de la fuerza horizontal respecto a la posición $F_{x}(x)$, y definimos igualmente una función de energía potencial respecto a la posición $U(x)$, de forma más simplificada podemos omitir el parámetro sabiendo que $F_{x}$ y $U$ son funciones respecto a la posición.
De igual manera recordemos que para cualquier desplazamiento, el trabajo es igual al negativo del cambio de energía potencial:
$$
W=-\Delta U
$$
Ahora, gracias a lo visto anteriormente en [[Trabajo y energía cinética]], podemos definir al trabajo como la fuerza por un desplazamiento, entonces esto aplicado a lo antes planteado:
$$
F_{x}(x)\cdot\Delta x=-\Delta U\qquad \Rightarrow \qquad F_{x}(x)=-\frac{\Delta U}{\Delta x}
$$
Ahora, probablemente a este punto usted sepa que es lo que planteamos hacer al acercar $\Delta x$ a 0, en tal caso obtendríamos: 
$$
F_{x}(x)=-\frac{dU(x)}{dx}
$$
Como verificación de esta ecuación podemos intentar obtener la función de fuerza a partir de la energía potencial elástica:
$$
\begin{align*}
U&=\frac{1}{2}kx^{2}\\
-\frac{d}{dx}U&=-\frac{d}{dx}\left( \frac{1}{2}kx^{2} \right)\\
F(x)&=-kx\\
&Q.E.D
\end{align*}
$$
