---
tags:
  - Física
  - Vectores
---
Ya habiendo visto el trabajo, hemos podido observar que el trabajo depende de la fuerza y el desplazamiento de un objeto, sin embargo, no hemos podido relacionar el trabajo con una cantidad de tiempo, es decir, si movemos un objeto cierta distancia con cierta fuerza, el trabajo será el mismo ya sea si nos tardamos un segundo, 10 minutos, una hora o cien años. Pero existen ocasiones en las que es necesario que conozcamos con que rapidez se efectuó un trabajo. Es aquí donde definimos esto en términos de *potencia*. 
Puede que en la cotidianidad se le pueda relacionar con la energía o con la fuerza, sin embargo, en física se puede definir la potencia como la rapidez con la que se efectúa un trabajo. Por lo tanto, la potencia (al igual que con el trabajo y con la energía) es escalar.

## Potencia media e instantánea

Si nosotros realizamos un trabajo $\Delta W$ en un intervalo de tiempo $\Delta t$, entonces podemos definir la potencia media de la siguiente forma:
$$
P_{med}=\frac{\Delta W}{\Delta t}
$$
Ahora, si intentamos obtener la potencia en un momento específico, es necesario que el intervalo de tiempo se vuelva infinitamente pequeño, por lo tanto tendríamos que tender la variación del tiempo a 0:
$$
P=\lim_{ \Delta t \to 0 } \frac{\Delta W}{\Delta t}= \frac{dW}{dt} 
$$
Las unidades de medida de la potencia son los *Watts*, que según el sistema SI se definiría como Joules por segundo ($J/s$).

Usualmente los Watts se utilizan para la potencia eléctrica, sin embargo, no es una medida inherente a la electricidad.
El kilowatt-hora es una medida que se utiliza comercialmente para la energía eléctrica. Un kilowatt-hora es el trabajo realizado en una hora.
Cabe recalcar que el kilowatt-hora es una medida de trabajo o de energía, no es una medida de potencia.

Visto desde la mecánica, la potencia se puede expresar en términos de la fuerza y la velocidad.
Si tomamos una fuerza $F$ la cual actúa sobre un cuerpo con un desplazamiento $\Delta s$. Tomando $F_{\parallel}$ como la fuerza tangente (o paralela) al desplazamiento, entonces el trabajo estaría efectuado por $F\Delta s$, ahora, si queremos obtener la potencia tendríamos que tomar este trabajo y obtenerlo respecto a un intervalo de tiempo $\Delta t$:
$$
P_{med}=\frac{F_{\parallel}\Delta s}{\Delta t}=F_{\parallel} \frac{\Delta s}{\Delta t}=F_{\parallel}v_{med}
$$
La potencia instantánea se obtiene a partir de esta expresión cuando $\Delta t \to 0$:
$$
P=\lim_{ \Delta t \to 0 } F_{\parallel} \frac{\Delta s}{\Delta t}=F_{\parallel} \frac{ds}{dt}=F_{\parallel}v
$$
Donde $v$ es la magnitud de la velocidad instantánea, también podemos expresar la potencia como un producto escalar:
$$
P=F_{\parallel}\cdot v
$$
