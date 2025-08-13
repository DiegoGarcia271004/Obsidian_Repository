---
tags:
  - Calculo3
---
1. Determine el límite, si existe, o demuestre que no existe:
a) 
$$
\lim_{ (x,y)\to(0,0) } \frac{y^{2}\sin ^{2}x}{x^{4}+y^{4}} 
$$
Resolución:
Primeramente tomaremos las trayectorias dadas por el límite:
$$
\begin{gather*}
\lim_{ (x,y)\to(0,0)} \frac{0^{2}\sin^{2}(0)}{0+0}=\frac{0}{0}
\end{gather*}
$$
$$
\begin{gather*}
x=my\\
\lim_{ y\to 0} \frac{y^{2}\sin^{2}my}{m^{4}y^{4}+y^{4}}\\
\lim_{ y \to 0 } \frac{y^{2}\sin^{2}my}{y^{4}(m^{4}+1)}\\
\lim_{ y \to 0 } \cancelto{ m^{2} }{ \frac{\sin^{2}my}{y^{2}} } \cdot \frac{1}{m^{4}+1}\\
\lim_{ y \to 0 } \frac{m^{2}}{m^{4}+1}\\
\boxed{\frac{m^{2}}{m^{4}+1}}
\end{gather*}
$$


b)
$$
\lim_{ (x,y) \to (1,0) } \frac{xy}{\sqrt{ x^{2}+y^{2} }}
$$
Resolución:
$$
\begin{gather*}
x=r\cos \theta\qquad y=r\sin \theta\\
\lim_{ r \to 0 }  \frac{(r\cos \theta)(r\sin \theta)}{\sqrt{ (r\cos \theta)^{2}+(r\sin \theta)^{2} }}\\
\lim_{ r \to 0 } \frac{r^{2}\sin \theta \cos \theta}{\sqrt{ r^{2}(\cancelto{ 1 }{ \cos ^{2} \theta +\sin ^{2}\theta}) }}\\
\lim_{ r \to 0 } \frac{r^{2}\sin \theta \cos \theta}{r}\\
\lim_{ r \to 0 } r\sin \theta \cos \theta\\
\boxed{0}
\end{gather*}
$$


c) 
$$
\lim_{ (x,y) \to (1,0) } \frac{xy-y}{(x-1)^{2}+y^{2}}
$$
Resolución:
$$
\begin{gather*}
y=m(x-1)\\
\lim_{ x \to 1 } \frac{mx(x-1)-m(x-1)}{(x-1)^{2}+m^{2}(x-1)^{2}}\\
\lim_{ x \to 1 } \frac{m(x-1)(x-1)}{(x-1)^{2}(1+m^{2})}\\
\lim_{ x \to 1 } \frac{m(x-1)^{2}}{(1+m^{2})(x-1)^{2}}\\
\lim_{ x \to 1 } \frac{m}{1+m^{2}}\\
\boxed{\frac{m}{1+m^{2}}}
\end{gather*}
$$
2. Calcule las primeras derivadas parciales de las siguientes funciones:
a) 
$$
f(x,t)=\sqrt{ x }\ln t
$$
Resolución:
$$
\begin{gather*}
\frac{\partial f}{\partial x}=\frac{1}{2\sqrt{ x }}\ln x\\
\frac{\partial f}{\partial t}=\frac{\sqrt{ x }}{t}
\end{gather*}
$$
b) 
$$
f(x,y)=\frac{ax+by}{cx+dy}
$$
Resolución:
$$
\begin{align*}
\frac{\partial f}{\partial x}&=\frac{a(cx+dy)-c(ax+by)}{(cx+dy)^{2}}\\
&=\frac{ady-cby}{(cx+dy)^{2}}\\
\\
\frac{\partial f}{\partial y}&=\frac{b(cx+dy)-d(ax+by)}{(cx+dy)^{2}}\\
&=\frac{bcx-dax}{(cx+dy)}
\end{align*}
$$
c) 
$$
F(\alpha, \beta)=\int _{\alpha}^{\beta}\sqrt{ t^{3}+1 } \, dt 
$$
Resolución:
$$
\begin{align*}
\frac{\partial F}{\partial \alpha}&=-\sqrt{ \alpha^{3}+1 }\\
\frac{\partial F}{\partial \beta}&=\sqrt{ \beta^{3}+1 }
\end{align*}
$$

3. El elipsoide $4x^{2}+2y^{2}+z^{2}=16$ interseca el plano $y=2$ en una elipse. Encuentre las ecuaciones paramétricas de la tangente a esta elipse en el punto $(1,2,2)$
Resolución:

$$
\begin{gather*}
z=\sqrt{ 16-4x^{2}-2y^{2} }\\
\frac{\partial z}{\partial x}=-\frac{4x}{\sqrt{ 16-4x^{2}-2y^{2} }}\\
\frac{\partial z}{\partial y}=-\frac{2y}{\sqrt{ 16-4x^{2}-2y^{2} }}
\end{gather*}
$$
Ecuaciones:
$$
\begin{align*}
z&=-2(x-1)+2\\
\frac{z-2}{-2}&=x-1=t\\
\end{align*}
$$
$$
\boxed{z=2-2t\qquad x=t+1\qquad y=2}
$$






$$
\begin{gather*}
x^{2}+4y^{2}+z^{2}=9\\
\left\{ \begin{matrix}
x=2-4t \\
y=1+8t \\
z=3-2t
\end{matrix} \right.
\end{gather*}
$$
Obteniendo $\nabla f$:
$$
\nabla f=\langle 2x,8y,2z \rangle 
$$
Obteniendo el vector direccional de la recta (los valores salen a partir de la ecuación simétrica de la recta, donde los cocientes son los valores del vector):
$$
\begin{gather*}
t=\frac{x-2}{-4}=\frac{y-1}{8}=\frac{z-3}{-2}\\
\vec{V}=\langle -4,8,-2 \rangle 
\end{gather*}
$$
Sabemos que la recta posee un vector direccional $\langle -4,8,-2 \rangle$, y que este es perpendicular al plano tangente, por ende, el gradiente debe de ser paralelo a este vector (el gradiente sería un múltiplo del vector de la recta), por lo que $\nabla \vec{f}=k\vec{V}$, así que realizando la igualación:
$$
\begin{gather*}
\langle 2x,8y,2z \rangle =k\langle -4,8,-2 \rangle \\
2x=-4k\quad 8y=8k \quad 2z=-2k\\
x=-2k\quad y=k\quad z=-k\\
\text{Sustituyendo en la ecuación del elipsoide}\\
(-2k)^{2}+4(k)^{2}+(-k)^{2}=9\\
4k^{2}+4k^{2}+k^{2}=9\\
9k^{2}=9\\
k=±1
\end{gather*}
$$
Ya obteniendo los valores de $k$ que cumplen la ecuación, entonces sustituimos en los valores de $x,y \text{ y }z$ que obtuvimos anteriormente, lo que nos da dos puntos:
$$
(-2,1,-1)\quad \text{y} \quad (2,-1,1)
$$
