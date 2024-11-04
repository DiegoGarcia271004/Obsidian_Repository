---
tags:
  - EcuacionesDiferenciales
---
$y=y'+\sqrt{ 1-(y')^{2} }$
$$
\begin{align*}
y'&=p\\
y=\psi(y')&\Rightarrow y=\psi(p)\\
y&=p+\sqrt{ 1-p^{2} }\\
dy&=1- \frac{p}{\sqrt{ 1-p^{2} }}dp\\
&\begin{cases}
x=\int \frac{\psi'(p)}{p} \, dp \\
y=\psi(p) 
\end{cases}\\
x&=\int \frac{1}{p}-\frac{1}{\sqrt{ 1-p^{2} }} \, dp\\
x&=\ln|p|-\arcsin(p)+c\\
&\begin{cases}
x=\ln|p|-\arcsin(p)+c \\
y=p+\sqrt{ 1-p^{2} }
\end{cases} 
\end{align*}
$$

$y=\frac{3}{2}xy'+e^{y'}$
$$
\begin{align*}
y'&=p\\
dy&=p\,dx\\
y&=x\cdot\phi(y')+\psi(y')\\
y&=x\cdot \phi(p)+\psi(p)\\
dy&=\phi(p)\,dx+x\phi'(p)\,dp+\psi'(p)\,dp\\
p\,dx&=\phi(p)\,dx+x\phi'(p)\,dp+\psi'(p)\,dp\\
(p-\phi(p))\,dx&=(x\phi'(p)+\psi'(p))dp\\
\frac{dx}{dp}&=\frac{\phi'(p)}{p-\phi(p)}\cdot x+\frac{\psi'(p)}{p-\phi(p)}\\
\end{align*}
$$
$$
\begin{align*}
\phi(p)=\frac{3}{2}p&\qquad\psi(p)=e^{p}\\
\phi'(p)=\frac{3}{2}&\qquad\psi'(p)=e^{p}\\
\left( p-\frac{3}{2}p \right)dx&=\left( \frac{3}{2}p+e^{p} \right)dp\\
\frac{dx}{dp}&=\frac{3p}{2\left( -\frac{1}{2}p \right)}x-\frac{2e^{p}}{p}dp\\
I(x)&=e^{\int -3 \, dp }=e^{-3p}
\end{align*}
$$
Un tanque contiene inicialmente 100 L de una solución salina que contiene inicialmente 25 kg de sal. Se vierte agua dulce en el tanque a una velocidad de 4kg/min, mientras que sale del tanque una solución bien mezclada a la misma velocidad. Hallar: 
a) La cantidad de sal en el tanque en cualquier momento t.
b) El tiempo que se necesita para que haya una cantidad de 10 kg de sal. 
c) Si 𝑡 → ∞, averiguar la cantidad de sal que queda en el tanque.

$$
\begin{align*}
Cap&=100L\\
v_{e}&=v_{s}\\
v_{e}&=4\cdot \frac{kg}{min}\\
x_{0}&=25\,kg\\
\frac{dx}{dt}&=c_{e}v_{e}-c_{s}v_{s}
\end{align*}
$$
$$
\begin{align*}
\frac{dx}{dt}&=-\frac{x\,kg}{100\,gal}\left( 4\cdot \frac{gal}{min} \right)\\
\frac{dx}{x}&=\frac{-1}{25} \,dt\\
\ln(x)&=-\frac{t}{25}+c\\
x&=Ce^{\frac{-t}{25}}\frac{kg}{min}\\
C&=25\\
x&=25e^{\frac{-t}{25}}
\end{align*}
$$
$$
\begin{align*}
-25\ln\left( \frac{10}{25} \right)&=t\\
t&\approx 23\,min
\end{align*}
$$
En cierto depósito hay 189 L de solución salina que contiene 10 kg de sal. Se vierte agua en el depósito con una velocidad de 4 L por minuto y sale la mezcla con velocidad de 3 litros por minuto. La concentración se mantiene homogénea. Hallar la cantidad de sal al cabo de media hora.

$$
\begin{align*}
Cant &= 189 L\\
c_{e}&=c_{s}\\
x_{0}&=10kg\\
v_{e}&=4 \frac{L}{min}\\
v_{s}&=3 \frac{L}{min}
\end{align*}
$$
$$
\begin{align*}
\frac{dx}{dt}&=c_{e}v_{e}-c_{s}v_{s}\\
\frac{dx}{dt}&=- \frac{x}{189+(4-3)t\,gal}\cdot 3 \frac{L}{min}\\
\frac{dx}{dt}&=-\frac{3x}{189+t}\\
\frac{dx}{x}&=-\frac{3dt}{t+189}\\
\ln(x)&=-3\ln(t+189)+c\\
x&=\frac{C}{(t+189)^{3}}\\
x&=\frac{6.75\times 10^{7}}{(t+189)^{3}}
\end{align*}
$$


