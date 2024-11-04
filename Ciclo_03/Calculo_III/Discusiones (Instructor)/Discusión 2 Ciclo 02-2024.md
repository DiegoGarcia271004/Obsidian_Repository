---
tags:
  - Calculo3
---
1) Calcule las primeras derivadas parciales de las siguientes funciones:
$$
F(x,y)=\int _{y}^{x} \cos(e^{t}) \, dx 
$$

$$
\begin{align*}
a) &\frac{\partial}{\partial x}\left(F(x,y)  \right)\\
&\frac{\partial}{\partial x}\left( -\int_{c}^{y} \cos(e^{t}) \, dt+\int _{c}^{x} \cos(e^{t})\, dx  \right)\\
&\cancelto{0}{ -\int_{c}^{y} \cos(e^{t}) \, dt }+\frac{\partial}{\partial x}\left( \int _{c}^{x} \cos(e^{t})\, dx \right)\\
&\cos(e^{x})\\
\\
b)& \frac{\partial}{\partial y}(F(x,y))\\
&\frac{\partial}{\partial y}\left( -\int_{c}^{y} \cos(e^{t}) \, dt+\int _{c}^{x} \cos(e^{t})\, dx  \right)\\
&\cancelto{  0}{ \int _{c}^{x} \cos(e^{t})\, dx  }-\frac{\partial}{\partial y}(\int_{c}^{y} \cos(e^{t}) \, dt)\\
-&\cos(e^{t})

\end{align*}
$$


$$
w=\ln(x+2y+3z)
$$
$$
\begin{align*}
a) &\frac{\partial w}{\partial x}=\frac{x}{x+2y+3z}\\
b)& \frac{\partial w}{\partial y}
=\frac{2}{x+2y+3z}\\
c)& \frac{\partial w}{\partial z}=\frac{3}{z+2y+3z}
\end{align*}
$$

2) Determine el valor de $\frac{\partial z}{\partial x}$ en el punto $(1,1,1)$ si la ecuación $xy+z^{3}x-2yz=0$ describe a la función $z$ como una función de dos variables independientes $x$ y $y$, y la derivada parcial existe.

En este caso, no es posible despejar $z$, por lo tanto tendremos que obtener la derivada mediante el proceso de derivación implícita.
$$
\begin{align*}
xy+z^{3}x-2yz=0\\
\frac{\partial z}{\partial x}(xy+z^{3}x-2yz=0)\\
y+3z^{2} \frac{\partial z}{\partial x}+z^{3}-2y \frac{\partial z}{\partial x}=0
\end{align*}
$$
Despejando $\frac{\partial z}{\partial x}$:
$$
\begin{align*}
y+\frac{\partial z}{\partial x}(3z^{2}-2y)+z^{3}&=0\\
y+z^{3}=-\frac{\partial z}{\partial x}(3z^{2}-2y)&=0\\
\frac{y+z^{3}}{2y-3z^{2}}&=\frac{\partial z}{\partial x}
\end{align*}
$$
Evaluando $(1,1,1)$
$$
\begin{align*}
\left . \frac{\partial z}{\partial x} \right |_{(x,y,z)=(1,1,1)}&=\frac{1+1^{2}}{2(1)-3(1)^{2}}\\
&=\frac{2}{2-3}\\
&=\frac{2}{-1}\\
&=-2
\end{align*}
$$


3) Una ecuación diferencial parcial importante que describe la distribución de calor en una región en el tiempo $t$ se puede representar por una ecuación de calor en una dimensión:
$$
\frac{\partial f}{\partial t}=\frac{\partial^{2}f}{\partial x^{2}}
$$
Demuestre que $u(x,t)=\sin(\alpha x)e^{-\beta t}$ satisface la ecuación de calor; considere $\alpha$ y $\beta$ como constantes.

Derivando $u(x,t)$ respecto a $t$:
$$
\begin{align*}
\frac{\partial f}{\partial t}=-\beta\sin(\alpha x)e^{-\beta t}
\end{align*}
$$
Derivando dos veces $u(x,t)$ respecto a $x$:
$$
\begin{align*}
\frac{\partial f}{\partial x}&=\alpha \cos(\alpha x)e^{-\beta t}\\
\frac{\partial^{2}f}{\partial x^{2}}&=-\alpha^{2}\sin(\alpha x)e^{-\beta t}
\end{align*}
$$

> [!important] Constantes
> Si se evalúa en la ED, la relación se cumple si y solo si $\alpha^{2}=\beta$

4) Si tomamos una fotografía de las olas del mar desde la orilla de la playa, la foto muestra un patrón regular de picos y valles en un instante de tiempo, observando un movimiento vertical periódico en el espacio. Si permanecemos en el agua, podemos sentir como sube y baja el agua con las olas. En física, esta hermosa simetría se expresa por la ecuación de onda en una dimensión:
$$
\frac{\partial^{2}w}{\partial t^{2}}=c^{2} \frac{\partial^{2}w}{\partial x^{2}}
$$
Donde, 𝑤 es la altura de la onda, 𝑥 es la variable de la distancia, 𝑡 es la variable de tiempo y 𝑐 es la velocidad con la cual se propagan las ondas. Demuestre que las siguientes ecuaciones satisfacen la ecuación de onda:

$$
\begin{align*}
&w=\sin(x+t)&&w=\tan(2x-2ct)
\end{align*}
$$
Con $w=\sin(x+t)$:
$$
\begin{align*}
\frac{\partial w}{\partial t}&=\cos(x+t)\\
\frac{\partial^{2}w}{\partial t^{2}}&=-\sin(x+t)\\
\frac{\partial w}{\partial x}&=\cos(x+t)\\
\frac{\partial^{2}w}{\partial x^{2}}&=-\sin(x+t)
\end{align*}
$$

> [!warning] Incoherencia
> Si se evalúa en la ED, $c^{2}$ queda sobrando, supongo que no cumple ¯\\__(ツ)__/¯

Con $w=\tan(2x-2ct)$:
$$
\begin{align*}
\frac{\partial w}{\partial t}&=-2c\sec ^{2}(2x-2ct)\\
\frac{\partial^{2} w}{\partial t^{2}}&=8c^{2}\sec ^{2}(2x-2ct)\tan(2x-2ct)\\
\frac{\partial w}{\partial x}&=2\sec ^{2} (2x-2ct)\\
\frac{\partial^{2} w}{\partial x^{2}}&=8\sec ^{2}\tan(2x-2ct)\\
 
\end{align*}
$$

Evaluando en la ED:
$$
8c^{2}\sec ^{2}(2x-2ct)\tan(2x-2ct)=c^{2}(8\sec ^{2}\tan(2x-2ct))
$$
$$
8c^{2}\sec ^{2}\tan(2x-2ct)=8c^{2}\sec ^{2}\tan(2x-2ct)
$$
5) Para la superficie $x^{2}+y^{2}+z-4=0$, encuentre las ecuaciones de las rectas tangentes a la superficie en el punto donde $x=1$, $y=1$ de forma que dichas rectas sean paralelas a los planos $zx$ , $yz$; escriba las ecuaciones de forma explicita con variable dependiente $z$, de la forma $z=f(x)$, $z=g(y)$.

Encontrando el valor de $z$ en $(1,1)$:
$$
\begin{align*}
(1)^{2}+(1)^{2}+z-4&=0\\
2+z-4&=0\\
z-2&=0\\
z&=2
\end{align*}
$$
Despejando $z$:
$$
z=4-x^{2}-y^{2}
$$
Obteniendo $\left . \frac{\partial z}{\partial x}\right|_{(1,1)}$:
$$
\begin{align*}
\frac{\partial z}{\partial x}&=2x\\
\left . \frac{\partial z}{\partial x}\right|_{x=1}&=2(1)\\
&=2
\end{align*}
$$
Obteniendo $\left . \frac{\partial z}{\partial y}\right|_{(1,1)}$:
$$
\begin{align*}
\frac{\partial z}{\partial y}&=2y\\
\left . \frac{\partial z}{\partial y}\right|_{y=1}&=2(1)\\
&=2
\end{align*}
$$
Tangente en $xz$:
$$
\begin{align*}
z-z_{0}&=m_{t}(x-x_{0})\\
z-z_{0}&=\left. \frac{\partial z}{\partial x}\right|_{p_{0}}(x-x_{0})\\
z-2&=2(x-1)\\
z&=2x-2+2\\
z&=2x
\end{align*}
$$
Tangente en $yz$:
$$
\begin{align*}
z-z_{0}&=m_{t}(y-y_{0})\\
z-z_{0}&=\left . \frac{\partial z}{\partial y}\right|_{(1,1)}(y-y_{0})\\
z-2&=2(y-1)\\
z&=2y-2+2\\
z&=2y
\end{align*}
$$
