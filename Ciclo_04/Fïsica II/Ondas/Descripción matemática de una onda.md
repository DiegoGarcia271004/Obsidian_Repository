---
tags:
  - Física_II
---
Las ondas pueden describirse utilizando conceptos conocidos, así como rapidez de onda, amplitud, periodo, frecuencia y longitud de onda.
Si retomamos igualmente el ejemplo de la cuerda, cuando la cuerda está en reposo se puede decir que se encuentra en una línea recta (la cual tomaremos como eje $x$ en un plano de coordenadas), una partícula posicionada en su posición de equilibrio, con el paso de la onda, poseerá un movimiento perpendicular al paso de la onda (teniendo un movimiento en $y$), por lo que el movimiento vertical ($y$) en un instante ($t$), depende de la posición de la partícula ($x$), por lo que podríamos definir que el movimiento de una partícula se puede tomar como una función multivariada $y=f(x,t)$, a esta función la conoceremos como **función de onda**.

Anteriormente declarábamos que [[Ondas periódicas|las ondas se moverían con un MAS]], por lo que si tomamos $y(x=0,t)$, es decir en el punto inicial de la cuerda, deberíamos obtener un movimiento armónico simple. Por lo tanto:
$$
y(x=0,t)=A\cos(\omega t)=A\cos(2\pi ft)
$$
Es decir que la partícula se mueve con un MAS que posee una amplitud $A$ y una frecuencia angular $\omega=2\pi f$ 

$$
\begin{align*}
y(x,t)&=A\cos(kx-\omega t)\\
k&=\frac{2\pi}{\lambda}\\
\omega&=vk
\end{align*}
$$

## Velocidad y aceleración de una onda 

Si queremos obtener la velocidad con la que se mueve una partícula en un punto de un medio afectada por una onda, es necesario obtener la variación de la altura respecto al tiempo, manteniendo la posición constante:
$$
v_{y}(x,t)=\frac{\partial y(x,t)}{\partial t}=-\omega A\sin(kx-\omega t)
$$
Y su aceleración:
$$
a_{y}(x,t)=\frac{\partial^{2}y(x,t)}{\partial t^{2}}=-\omega^{2}A\cos(kx-\omega t)=-w^{2}y(x,t)
$$

