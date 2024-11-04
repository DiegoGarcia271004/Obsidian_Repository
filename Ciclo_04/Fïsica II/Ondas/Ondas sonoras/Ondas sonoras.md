---
tags:
  - Física_II
---
La principal definición del sonido, es que este es una [[Ondas mecánicas|onda longitudinal]] en un medio. Lo que nos interesa en esto son las ondas sonoras en el aire (Aunque este pueda viajar en otros medios).

Las ondas sonoras más sencillas son las senoidales, las cuales tienen ya definidas su *amplitud, frecuencia y longitud de onda*. El oído humano es sensible a un intervalo de frecuencias, que van desde los 20 a los 20,000 Hz, llamado **gama audible**, se les denominará "sonido" a las ondas que tengan una frecuencia establecida en este intervalo, ultrasónicas a las que posean frecuencias mayores, e infrasónicas a las que poseen menores.

Las ondas sonoras se pueden desplazar en todas las direcciones a partir de la fuente de sonido, que poseen una amplitud que depende de la dirección y la distancia de la fuente.
Si se supone que una onda sonora viaja únicamente en la dirección $+x$ y es una onda senoidal, entonces se puede definir matemáticamente como:
$$
y(x,t)=A\cos(kx-\omega t)
$$

---
## Ondas sonoras como fluctuaciones de presión

Las ondas sonoras se pueden describir en términos de variaciones de presión en varios puntos. Por ejemplo, en una onda senoidal en el aire, la presión fluctúa por arriba y debajo de la presión atmosférica $p_{a}$ en forma senoidal con la misma frecuencia que los movimientos de las partículas de aire.

Si definimos $p(x,t)$ como la variación de presión instantánea en una onda sonora en cualquier punto $x$ en un instante $t$. Es decir que $p(x,t)$ es la variación de presión respecto a la presión atmosférica, la cal puede ser positiva o negativa. Por lo que la presión absoluta en un punto es: $p_{a}+p(x,t)$.

Si buscamos plantear una relación entre la variación de presión $p(x,t)$ y el desplazamiento $y(x,t)$ en una onda sonora que se propaga en la dirección $+x$, entonces consideremos un cilindro imaginario de material (sólido, líquido o gas) con área transversal $S$ y su eje a lo largo de la dirección de propagación. Si no está presente una onda sonora, entonces el cilindro posee una longitud $\Delta x$ y volumen $V=S\cdot\Delta x$. En el caso que una onda esté presente, en el tiempo $t$ el extremo del cilindro que inicialmente estaba en $x$ tiene un desplazamiento dado por $y_{1}=y(x,t)$ (Su desplazamiento cambia dependiendo del tiempo y de la posición en la que estaba), y el extremo que estaba en $x+\Delta x$ experimenta un desplazamiento dado por $y_{2}=y(x+\Delta x,t)$. Si $y_{2}>y_{1}$, entonces el volumen del cilindro aumenta, originando una disminución de la presión. En caso contrario, el volumen disminuye y la presión aumenta. Finalmente si $y_{1}=y_{2}$ entonces el cilindro simplemente se desplaza, no existe ningún cambio de presión ni volumen. La fluctuación de presión depende de la diferencia entre el desplazamiento de puntos vecinos.
Debido a esto, se puede definir cuantitativamente el cambio de volumen $\Delta V$ del cilindro como:
$$
\Delta V=S(y_{2}-y_{1})=S[y(x+\Delta x,t)-y(x,y)]
$$
Por lo que si dividimos entre el volumen original y hacemos que $\Delta x \to 0$, entonces:
$$
\frac{dV}{V}=\lim_{ \Delta x \to 0 }  \frac{S[y(x+\Delta x,t)-y(x,y)]}{S\Delta x}=\frac{\partial y(x,t)}{\partial x}
$$
Finalmente, con unos arreglos físicos (no anote que significaba xd) nos queda:
$$
p(x,t) =-B \frac{\partial y(x,t)}{\partial x}
$$
Donde $B$ representa el módulo volumétrico, que es: $B=-p(x,t)/(dV/V)$, por lo que al despejar $p(x,t)$ obtenemos la ecuación anterior.

El signo negativo es debido  que cuando la parcial de $y(x,t)$ es positiva, el desplazamiento es mayor en $x+\Delta x$ que en $x$, implicando un aumento de volumen, y por consecuente una disminución de presión.

Si evaluamos $\partial y(x,t)/\partial x$ para la onda senoidal del comienzo, obtenemos que:
$$
p(x,t) = BkA\sin(kx-\omega t)
$$
Gracias a esta ecuación podemos definir un punto donde la presión es máxima dada cuando el seno es 1, a este punto se le conoce como **amplitud de presión** denotada como $p_{max}$:
$$
p_{max} = BkA
$$
La amplitud de presión es directamente proporcional al desplazamiento $A$, como era de esperarse, a su vez depende de la longitud de onda (por el número de onda $k=2\pi/\lambda$), las ondas con longitud de onda $\lambda$ más pequeñas tienen mayores variaciones de presión para una amplitud dada, ya que los máximos y mínimos están más cerca unos de otros. Un medio con un módulo volumétrico $B$ grande requieren una amplitud de presión relativamente grande, para una amplitud de presión  de desplazamiento dada, si $B$ es grande, implica un medio menos compresible; es decir que requiere un mayor cambio en la presión para un cambio de volumen determinado.


