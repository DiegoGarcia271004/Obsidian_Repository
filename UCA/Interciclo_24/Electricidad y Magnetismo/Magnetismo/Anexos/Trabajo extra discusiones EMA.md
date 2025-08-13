---
tags:
  - EMA
---

> [!warning] Trabajo duro
> Cabe aclarar que todo esto se hizo en latex, lo que fue un dolor de cabeza, no es q fuera copiado >:(


6) 
![[Ejercicio6.png|center]]

**a)**
Para que nosotros encontremos el campo magnético en el centro $C$, pues podemos separar las figuras en dos semicírculos, uno de radio $R_{1}$ y otro de radio $R_{2}$, al sumar el campo magnético de estas dos figuras, podemos encontrar el campo magnético total, y también su dirección.
$$
B_{total}=B_{semi_{1}}+B_{semi_{2}}
$$
Para encontrar el campo magnético puede ser mediante la utilización de la forma diferencial del campo magnético:
$$
d\vec{B}=\frac{\mu_{0}}{4\pi} \frac{I\,d\vec{l}\times \vec{r}}{r^{2}}
$$
Así que busquemos resolverla.
Primeramente, un semicírculo no sigue una línea recta, más bien una curva, de tal manera que tendremos que buscar un equivalente de la longitud de curva del semicírculo:

Ya sabemos que la longitud de una sección de un círculo está dado por:
$$
l=\theta R
$$
donde $r$ es el radio del círculo y $\theta$ es el ángulo (de aquí podemos saber que si queremos saber el perímetro de todo un círculo, tenemos que tomar todo el ángulo, es decir $2\pi$ por lo que queda $2\pi r$) entonces trabajando en su forma diferencial:
$$
dl=R\,d\theta
$$
de esta forma encontramos una equivalencia, de tal forma obtenemos:
$$
d\vec{B}=\frac{\mu_{0}}{4\pi} \frac{IR\,d\theta \times \vec{r}}{R^{2}}
$$
Sin embargo, si trabajamos con la simetría del semicírculo, entonces obtenemos que la componente en $x$ del campo magnético del semicírculo se anula, quedándonos únicamente la componente vertical perpendicular al $dl$ y al $R$ del círculo:
$$
d\vec{B}_{z}=\frac{\mu_{0}}{4\pi} \frac{I\sin (\theta)\, d\theta}{R}
$$
finalmente buscamos integrar esta expresión para encontrar la magnitud del campo:
$$
\int _{0}^{B_{z}} d\vec{B}_{z}=\frac{\mu_{0}I}{4\pi R}\int _{0}^{\pi}\sin \theta \, d\theta  
$$
tras realizar la integral obtenemos:
$$
B_{z}=\frac{\mu_{0}I}{2\pi R}
$$
Ya obtenida la expresión del campo magnético del semicírculo, entonces podemos seguir con la idea propuesta al principio, el campo producido por el primer y segundo semicírculo respectivamente sería de:
$$
B_{semi_{1}}=\frac{\mu_{0}I}{2\pi R_{1}} \qquad B_{semi_{2}}=-\frac{\mu_{0}I}{2\pi R_{2}}
$$
Con la diferencia de que para el segundo semicírculo, por la dirección de la corriente, el campo será negativo, por lo que:
$$
\begin{align*}
B_{tot}&=\frac{\mu_{0}I}{2\pi R_{1}}-\frac{\mu_{0}I}{2\pi R_{2}}\\
&=\frac{\mu_{0}I}{2\pi}\left( \frac{1}{R_{1}}-\frac{1}{R_{2}} \right)
\end{align*}
$$

Por lo que la magnitud del campo magnético es de:
$$
\boxed{B=\frac{\mu_{0}I}{2\pi}\left( \frac{1}{R_{1}}-\frac{1}{R_{2}} \right)}
$$
Y en cuanto a la dirección, debido a que la magnitud del campo magnético del semicírculo de radio $R_{1}$, es mayor a la del otro semicírculo, entonces el campo magnético total (por regla de la mano derecha) **saldría de la página**.

**b)**
Para obtener el momento dipolar magnético, es necesario encontrar el área total de la figura, así que solo tenemos que encontrar el área de cada semicírculo:

**Semicírculo 1:**
Este posee un radio de $R_{1}$, por lo que el área de un círculo con este radio es de:
$$
A=\pi R_{1}^{2}
$$
pero ya que necesitamos el área de la mitad de ese círculo, entonces tenemos:
$$
\boxed{A_{1}=\frac{\pi}{2}R_{1}^{2}}
$$
**Semicírculo 2:**
Para el segundo semicírculo con radio $R_{2}$ seguimos el mismo proceso que para el semicírculo anterior:
$$
\boxed{A_{2}=\frac{\pi}{2}R_{2}^{2}}
$$
**Área total:**
Así que el área total de la figura es de:
$$
\begin{align*}
A_{tot}&=A_{1}+A_{2}\\
&=\frac{\pi}{2}R_{1}^{2}+\frac{\pi}{2}R_{2}^{2}\\
&\boxed{=\frac{\pi}{2}(R_{1}^{2}+R_{2}^{2})}
\end{align*}
$$
**Momento dipolar magnético:**
Ya obtenido el área de la figura, entonces solo tenemos que sustituir en la ecuación del momento dipolar magnético:
$$
\mu =IA
$$
Por lo que este es igual a:
$$
\boxed{\mu=\frac{\pi I}{2}(R_{1}^{2}+R_{2}^{2})}
$$
---

12) ¿Qué corriente se requiere en los embobinados de un solenoide que tiene 1 000 vueltas distribuidas uniformemente en toda una longitud de 0.400 m, para producir en el centro del solenoide un campo magnético de magnitud $1.00\times10^{-4}\, \text{T}$?

Para un solenoide, el campo magnético formado en su interior está dado por la expresión:
$$
B=\mu_{0}nI
$$
donde $\mu_{0}$ es la constante magnética, $I$ es la intensidad de corriente y $n$ es la cantidad de espiras por unidad de longitud, así que encontremos este valor:

Para esto tendremos que dividir el número de espiras por la longitud total del solenoide:
$$
n= \frac{\text{\# espiras}}{L}=\frac{1000}{0.4 m}=2500 \frac{\,\text{espiras}}{m}
$$
Con esto, si queremos obtener la corriente que provoca el campo eléctrico mencionado, tenemos que despejar la ecuación:
$$
I=\frac{B}{\mu_{0}n}=\frac{1.00\times 10^{-4}\,\text{T}}{(4\pi \times 10^{-7} N/A^{2})(2500\,\text{espiras}/m)}=\boxed{0.032A}
$$
---
13) Las bobinas magnéticas de un reactor de fusión tokamak tienen forma toroidal con un radio interno de 0.700 m y un radio externo de 1.30 m. El toroide tiene 900 vueltas de alambre de gran diámetro, cada una de las cuales lleva una corriente de 14.0 kA. Determine la magnitud del campo magnético en el interior del toroide a lo largo de a) el radio interno y b) el radio externo.

Para un toroide, el campo magnético está dado por:
$$
B=\frac{\mu_{0}IN}{2\pi r}
$$
donde $I$ es la intensidad, $N$ el número de espiras y $r$ el radio.

De esta forma solo tenemos que sustituir lo valores respectivos en la ecuación para poder encontrar la magnitud del campo magnético:

**Radio interior:**
$$
\begin{align*}
B_{int}=\frac{\mu_{0}(14\times 10^{3}A)(900)}{2\pi(0.7m)}=\boxed{3.6\,T}
\end{align*}
$$
**Radio exterior:**
$$
\begin{align*}
B_{int}=\frac{\mu_{0}(14\times 10^{3}A)(900)}{2\pi(1.3m)}\approx\boxed{1.94\,T}
\end{align*}
$$
