**Teorema:** Si $F(x,y)=P(x,y)\hat{\imath}+Q(x,y)\hat{\jmath}$ es un campo vectorial conservativo donde $P$ y $Q$ tienen derivadas parciales continuas de primer orden sobre un dominio $D$, entonces en la totalidad de $D$ tenemos:
$$
\frac{\partial P}{\partial y}=\frac{\partial Q}{\partial x}
$$
1. Dada la función:
$$
F(x,y)=\frac{-y \hat{\imath}+x \hat{\jmath}}{x^{2}+y^{2}}
$$
a) Demuestre que:
$$
\frac{\partial P}{\partial y}=\frac{\partial Q}{\partial x}
$$
b) Demuestre que $\int _{C}F \, dr$ no es independiente de la trayectoria.
(Como sugerencia calcule $\int _{C_{1}}F \, dr$) y $\int _{C_{2}}D \, dr$ donde $C_{1}$ y $C_{2}$ son las mitades superiores e inferiores de la circunferencia $x^{2}+y^{2}=1$ desde $]1,0[$ hasta $]-1,0[$)

---
La función $F$ se puede definir también como:
$$
F(x,y)=-\frac{y}{x^{2}+y^{2}}\hat{\imath}+\frac{x}{x^{2}+y^{2}} \hat{\jmath}
$$
a) Ya identificadas $P$ y $Q$, podemos probar el teorema.
$$
\begin{gather*}
\frac{\partial P}{\partial y}=-\frac{x^{2}+y^{2}-2y^{2}}{(x^{2}+y^{2})^{2}}=\frac{y^{2}-x^{2}}{(x^{2}+y^{2})}\\
\frac{\partial Q}{\partial x}=\frac{x^{2}+y^{2}-2x^{2}}{(x^{2}+y^{2})}=\frac{y^{2}-x^{2}}{(x^{2}+y^{2})^{2}}
\end{gather*}
$$

b)
La curva sobre la que vamos a integrar es $x^{2}+y^{2}=1$, ahora debemos de parametrizar la curva:
$$
r(t)=\cos (t) \hat{\imath}+\sin(t) \hat{\jmath}\qquad 0\leq t\leq 2\pi
$$
Por lo que:
$$
\begin{gather*}
F(r(t))=-\frac{\sin(t)}{1} \hat{\imath}+\frac{\cos(t)}{1} \hat{\jmath}\\
\frac{dr}{dt}=-\sin(t) \hat{\imath}+\cos(t) \hat{\jmath}
\end{gather*}
$$
Por lo que nuestro producto escalar $F\cdot dr$ será:
$$
F\cdot dr=F\cdot \frac{dr}{dt}=(-\sin t)(-\sin t)+(\cos t)(\cos t)=\sin ^{2}t+\cos ^{2}t=1
$$
Entonces:
$$
\int _{C}F\cdot dr=\int _{C}1 \, dr  
$$
Por lo tanto:
- Para la mitad superior $t\in[0,\pi] \implies \int _{C_{1}}F\cdot dr=\int _{0}^{\pi}1 \, dr=\pi$ 
- Para la mitad inferior $t\in[\pi,2\pi]\implies \int _{C_{2}}F\cdot dx=\int _{\pi}^{2\pi}1 \, dr=\pi$ 

El resultado no contradice el teorema. Sin embargo, el campo no es conservativo, esto es debido a que el campo no es simplemente conexo, ya que el campo no está definido en $(0,0)$.


> [!important] Campo simplemente conexo
> Un campo es simplemente conexo si cualquier curva cerrada puede ser contraída en un punto sin salirse del dominio.
> En el ejemplo el campo vectorial no es simplemente conexo porque si se reduce a un punto en el $(0,0)$ se sale del dominio, ya que no está definida en ese punto.

---

2. Encuentre el centro de masa de un alambre delgado colocado a lo largo de la curva
$$
r(t)=t \hat{\imath}+2t \hat{\jmath} +\frac{2}{3}t^{\frac{3}{2}\hat{k}},\,0\leq t\leq 2
$$
Si su densidad es $\delta=3\sqrt{ 5+t }$.
---
Encontrando la masa:
$$
m=\int _{a}^{b}\delta(t)\|r'(t)\| \, dt 
$$
Encontrando $r'(t)$:
$$
r'(t)=\hat{\imath}+2 \hat{\jmath}+t^\frac{1}{2}\hat{k}
$$
Encontrando $\|r'(t)\|$:
$$
\|r'(t)\|=\sqrt{ 1^{2}+2^{2}+(t^{1/2})^{2} }=\sqrt{ 5+t }
$$
Entonces la masa es:
$$
m=\int _{0}^{2}3\sqrt{ 5+t }\sqrt{ 5+t } \, dr=3\int _{0}^{2}5+t \, dr=36  
$$
El centro de masa es dado por:
$$
\bar{x}=\frac{1}{m}\int _{a}^{b}x(t)\delta(t)\|r'(t)\| \, dr \qquad \bar{y}=\frac{1}{m}\int _{a}^{b}y(t)\|r'(t)\| \, dr \qquad \bar{z}=\frac{1}{m}\int _{a}^{b}z(t)\|r'(t)\| \, dr 
$$

Coordenada en $x$:
$$
\bar{x}=\frac{3}{36}\int _{0}^{2}t\sqrt{ 5+t }\sqrt{ 5+t } \, dr =\frac{3}{36}\int 5t+t^{2} \, dr =\frac{19}{18}
$$
Coordenada en $y$:
$$
\bar{y}=\frac{3\cdot2}{36}\int _{0}^{2}t\sqrt{ 5+t }\sqrt{ 5+t } \, dr=\frac{6}{36}\int _{0}^{2} 5t+t^{2} \, dr=\frac{19}{9} 
$$
Coordenada en $z$:
$$
\bar{z}=\frac{2}{36}\int _{0}^{2}t^{3/2}\sqrt{ 5+t }\sqrt{ 5+t } \, dr=\frac{4\sqrt{ 2 }}{7}
$$
Por lo que el punto es:
$$
\boxed{\left( \frac{19}{18}, \frac{19}{9}, \frac{4\sqrt{ 2 }}{7} \right)}
$$
---

3. Encuentre:
$$
\int _{\Omega}  \frac{ds}{(2y^{2}+1)^{\frac{3}{2}}} 
$$
donde $\Omega$ es una parábola que se forma de la intersección de las superficies:
$$
z^{2}=x^{2}+y^{2}\qquad x+z=1
$$
---

Encontrando $\Omega$:
$$
\begin{gather*}
z=1-x\\
(1-x)^{2}=x^{2}+y^{2}\\
1-2x+x^{2}=x^{2}+y^{2}\\
1-2x=y^{2}\\
x=\frac{1-y^{2}}{2}\\
z=1-x\\
z=1-\frac{1-y^{2}}{2}\\
z=\frac{1+y^{2}}{2}\\
r(t)=\left( \frac{1-t^{2}}{2},t, \frac{1+y^{2}}{2} \right)\quad t\in\mathbb{R}
\end{gather*}
$$
Obteniendo $r'(t)$:
$$
r'(t)=(-t,1,t)
$$
Obteniendo $\|r'(t)\|$: 
$$
\begin{gather*}
\|r'(t)\|=\sqrt{ (-t)^{2}+1^{2}+t^{2} }\\
=\sqrt{ 2t^{2}+1 }
\end{gather*}
$$
Por lo que el $ds$ será:
$$
ds=\sqrt{ 2t^{2}+1 }\,dt
$$
Sustituyendo en la integral:
$$
\begin{gather*}
\int _{-\infty}^{\infty } \frac{\sqrt{ 2t^{2}+1 }}{(2t^{2}+1)^{\frac{3}{2}}} \, dr\\
\int _{-\infty}^{\infty} \frac{1}{2t^{2}+1} \, dr\\
\frac{1}{\sqrt{ 2 }}\arctan(u)|_{-\infty }^{\infty}\\
\frac{1}{\sqrt{ 2 }}\left( \frac{\pi}{2}+\frac{\pi}{2} \right)\\
\frac{\pi}{\sqrt{ 2 }}
\end{gather*}
$$



