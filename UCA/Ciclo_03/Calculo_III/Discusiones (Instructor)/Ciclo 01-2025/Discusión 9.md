1. Utilice el teorema de Green para evaluar la integral de línea en $C$.
$$
\int _{C}(y+e^{\sqrt{ x }}) \, dx +(2x+\cos y^{2})dy
$$
Donde $C$ es la región entre las parábolas $y=x^{2}$ y $x=y^{2}$

---
El teorema de Green dice que:
$$
\oint_{C} Mdx+N dy =\iint_{D} \left( \frac{\partial N}{\partial x}- \frac{\partial M}{\partial y} \right)dA
$$
Y sabemos que la curva $C$ es una curva cerrada, por lo que se cumple el teorema.
Así que:
$$
\int _{C}(y+e^{\sqrt{ x }}) \, dx +(2x+\cos y^{2})dy=\iint_{D}\left( 2-1 \right) dA
$$
$$
\begin{gather*}
\int _{0}^{1}\int _{y^{2}}^{\sqrt{ y }}(2-1) \, dx  \, dy\\
\int _{0}^{1}\sqrt{ y }-y^{2} \, dy\\
\left( \frac{2y^{3/2}}{3}-\frac{y^{3}}{3} \right)_{0}^{1}\\
\frac{1}{3}
\end{gather*} 
$$
---

$$
x=5\cos t-\cos 5t \qquad y=5\sin t-\sin 5t\quad [0,2\pi]
$$

Por Green, podemos tomar cualquiera de las siguientes formas:
$$
A=\int_{C} x \, dy=-\int_{C} y \, dx=\frac{1}{2}\int x \, dy-y\,dx   
$$
En este caso usaremos la primera, por lo que:
$$
A=\int _{C}x \, dy=\int _{0}^{2\pi} (5\cos t-\cos 5t)(5\cos t-5\cos 5t) \, dx=30\pi  
$$

---

$$
\iint_{S}F \cdot d\vec{s}=\iint_{D}F(x,y,f(x,y))\nabla \vec{f}\,dx\,dy
$$
1. Se obtiene el gradiente.
2. Se sustituye la superficie en la función del campo vectorial
3. Se obtiene el producto punto entre el campo vectorial y el gradiente
4. Expandir e integrar

---

