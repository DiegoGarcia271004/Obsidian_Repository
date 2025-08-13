---
tags:
  - Física
---

En esta sección estudiaremos la física tras los choques, interacciones intensas entre cuerpos con una duración relativamente corta, como por ejemplo, las bolas de billar que chocan entre ellas, accidentes automovilísticos, entre otros casos.
Si en los casos, las fuerzas internas del sistema son mucho mayores que las fuerzas externas, entonces es posible despreciarlas, considerando así un sistema aislado. Por lo tanto, el momento lineal del sistema se mantendría constante tanto al inicio como al final del choque como se vio en [[Momento lineal e impulso#Conservación del momento lineal|la sección de conservación del momento lineal]] Por ejemplo durante el choque entre vehículos, la fuerza ejercida entre ellos durante el momento del choque, será superior en gran manera a la fuerza ejercida por la fricción por el contacto con el pavimento, por lo tanto es posible despreciarla .

## Choques elásticos e inelásticos

Si las fuerzas entre los cuerpos son [[Fuerzas conservativas y no conservativas|conservativas]], entonces la energía cinética del sistema se mantiene constante en todo momento, ya sea antes como después del choque, entonces se considera un **choque elástico**.
Un ejemplo de esto serían dos cuerpos con resortes, los cuales al colisionar, la energía cinética se almacena como energía potencial elástica dentro de los resortes, y al volver a su estado original, la energía potencial se convierte en cinética, conservando así la energía mecánica total del sistema.

En un choque, en donde la energía mecánica inicial sea mayor que la energía mecánica final, lo que puede ser signo de conversión de energía, ya sea como energía térmica o algún tipo de deformación en el cuerpo, a este tipo de choque se le considera un choque inelástico.
Como ejemplo podría ser una bola de plastilina, la cual si se tira al suelo, esta no rebota, sino que se deforma y se detiene en seco.

## Choques completamente inelásticos 

Un choque completamente inelástico se da cuando al momento de un choque entre dos cuerpos, estos se juntan y se vuelven una sola masa y terminan con una misma velocidad en la misma velocidad.
$$
v_{A_{2}}=v_{B_{2}}=v_{2}
$$
Por lo tanto la conservación de energía en un choque totalmente inelástico se da de la siguiente forma:
$$
m_{A}v_{A_{1}}+m_{B}v_{B_{1}}=(m_{A}+m_{B})v_{2}
$$
Cabe aclarar, que en los casos donde sean choques completamente inelásticos, siempre existirá una pérdida de energía cinética, por lo tanto la energía cinética inicial será mayor que la energía cinética total.

## Choques elásticos

En esta sección profundizaremos más en el tema de los choques elásticos.

Como se menciono anteriormente, los choques elásticos se dan cuando las fuerzas entre los cuerpos son conservativas, un ejemplo de esto son las bolas de billas, las cuales al colisionar (si bien no se ve a simple vista) se aplastan un poco, almacenando energía potencial elástica en ellas, para momentos después liberarlas y mantener constante la energía mecánica del sistema.

Si analizamos un choque elástico entre dos cuerpos, debido a que la energía se conserva en todo momento del sistema, podemos decir que:
$$
\frac{1}{2}m_{a}v_{a_{1}}^{2}+\frac{1}{2}m_{b}v_{b_{1}}^{2}=\frac{1}{2}m_{a}v_{a_{2}}^{2}+\frac{1}{2}m_{b}v_{b_{2}}^{2}
$$
A su vez, por las propiedades del choque elástico, el momento lineal del sistema, de igual manera, se conserva:
$$
m_{a}v_{a_{1}}+m_{b}v_{b_{1}}=m_{a}v_{a_{2}}+m_{b}v_{b_{2}}
$$
A partir de estas ecuaciones, podemos encontrar las incógnitas que sean presentadas durante los problemas de este estilo.

### Choques elásticos con un cuerpo inicialmente en reposo

En este caso especial de los choques, uno de los objetos con los que se da el choque, por lo tanto la velocidad inicial del objeto es 0, y al evaluar esto en las ecuaciones que hemos descrito antes, obtenemos:
$$
\begin{align*}
\frac{1}{2}m_{a}v_{a_{1}}^{2}&=\frac{1}{2}m_{a}v_{a_{2}}^{2}+\frac{1}{2}m_{b}v_{b_{2}}^{2}\\\\

m_{a}v_{a_{1}}&=m_{a}v_{a_{2}}+m_{b}v_{b_{2}}
\end{align*}
$$
Si ya con estas ecuaciones buscamos despejar $v_{b_{2}}$, entonces podemos llegar a las siguientes expresiones:
$$
\begin{align*}
m_{b}v_{b_{2}}^{2}&=m_{a}(v_{a_{1}}+v_{a_{2}})(v_{a_{1}}+v_{a_{2}})\\
\\
m_{b}v_{b_{2}}&=m_{a}(v_{a_{1}}-v_{a_{2}})
\end{align*}
$$
Ahora si dividimos la primera ecuación por la segunda obtenemos:
$$
v_{b_{2}}=v_{a_{1}}+v_{a_{2}}
$$
(La neta, esta parte es una gran fumada, en el libro hace un montón de sustituciones, así que iré directo al grano)

$$
\begin{align*}
v_{a_{2}}&=\frac{m_{a}-m_{b}}{m_{a}+m_{b}}v_{a_{1}}\\
v_{b_{2}}&=\frac{2m_{a}}{m_{a}+m_{b}}v_{a_{1}}
\end{align*}
$$
Tras obtener esta ecuación podemos observar ciertos comportamientos con las diferentes masas, por ejemplo, si la masa del objeto $a$ es mucho menor que la del objeto $b$, entonces la primera ecuación muestra que la fracción de la primera ecuación se aproxima a -1, por lo que podemos afirmar que si se dan estas condiciones, entonces la velocidad final del objeto $a$ es aproximada a la velocidad inicial pero con sentido contrario.

A su vez, si tomamos que la masa del objeto $a$ es mucho más grande que la del objeto $b$, la fracción de la segunda ecuación quedará aproximada a 1, entonces la velocidad aplicada al objeto $b$, será casi igual a la magnitud del momento lineal del objeto $a$.

Un caso interesante, es que si las dos masas de los objetos son iguales, entonces por la primera ecuación, nos indica que al momento del impacto, el objeto $a$ va a quedar en reposo, mientras que la velocidad del objeto $b$ será la misma que la velocidad inicial del objeto $a$.
