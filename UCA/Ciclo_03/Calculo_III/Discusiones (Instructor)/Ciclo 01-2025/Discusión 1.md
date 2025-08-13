---
tags:
  - Calculo3
---
1. Determine el tipo de superficie que describe la siguiente expresión
$$
28x^{2}-112x+14y^{2}+84y-8z^{2}-16z+286=0
$$
$$
\begin{gather*}
\text{Agrupando términos semejantes y sacando factores comúnes}\\
28(x^{2}-4x)+14(y^{2}+6y)-8(z^{2}-2z)+286=0\\
\text{Completando cuadrados}\\
28(x^{2}-4x+4)-112+14(y^{2}+6y+9)-126-8(z^{2}-2z+1)+8+286=0\\
\text{Simplificando}\\
28(x-2)^{2}+14(y+3)^{2}-8(z-1)^{2}=-56\\
\text{Dividiendo todo por } -56\\
-\frac{(x-2)^{2}}{2}-\frac{(y+3)^{2}}{4}+\frac{(z-1)^{2}}{7}=1
\end{gather*}
$$
Por la forma de la ecuación se puede concluir que es un paraboloide de dos hojas que no se encuentra ubicada en el polo. Esto debido a la ecuación de un paraboloide de dos hojas:
$$
-\frac{x^{2}}{a^{2}}-\frac{y^{2}}{b^{2}}+\frac{z^{2}}{c^{2}}=1\qquad \text{(Paraboloide de dos hojas)}
$$
Debido a que las variables no se encuentran solas, concluimos que esta gráfica se encuentra desplazada, y el centro de esta gráfica se encuentra en el punto $(2,-3,1)$.

2. Determino el dominio de las siguientes funciones en varias variables y haga su respectiva representación gráfica

a) 
$$
f(x,y)=\frac{\sqrt{ x-y+1 }-\sqrt{ y }}{\ln(x^{2}-y)}
$$
Para poder encontrar el dominio, tenemos que encontrar cuales serían las restricciones que posee la función, en este caso, tenemos una unión entre radicales, logaritmos y funciones racionales. A continuación desglosaremos cada una de ellas

$$
\sqrt{ x-y+1 }
$$
Para encontrar las restricciones en esta función tenemos que conocer que es lo que se nos prohíbe, al ser una raíz, sabemos que el argumento no puede ser negativo, por lo que:
$$
\begin{gather*}
x-y+1\geq 0 \\
x\geq y-1
\end{gather*}
$$
Es decir que $x$ tiene que ser siempre mayor a $y-1$.


$$
\sqrt{ y }
$$
De igual forma que en el radical anterior, tenemos la misma restricción, por lo que:
$$
y\geq 0
$$


$$
\frac{1}{\ln(x^{2}-y)}
$$
En este caso tenemos una composición entre funciones racionales y logarítmicas. Sabemos que la función logarítmica no puede poseer valores negativos ni 0, pero por la condición que se encuentra en el denominador, esta tampoco puede ser 0 así que tenemos 2 restricciones:
$$
x^{2}-y>0\qquad x^{2}-y\neq 1
$$

Finalmente tras realizar el dibujo del dominio nos tendría que quedar de la siguiente manera:
![[Discusion1Ej2Lita|1000|center]]

Donde el área sombreada sería el dominio, y la línea verde una asíntota.

b)
$$
f(x,y)=\ln(x-y^{2})+\sqrt{ 1-y^{2}-\frac{x^{2}}{2} }
$$
En esta función tenemos únicamente 2 restricciones, una logarítmica y una radical, así que de igual manera, las trabajaremos individualmente.

$$
\ln(x-y^{2})
$$
Para esta función logarítmica, la única restricción es que el argumento tiene que ser positivo y diferente de 0:
$$
\begin{gather*}
x-y^{2}>0\\
x>y^{2}
\end{gather*}
$$

$$
\sqrt{ 1-y^{2}-\frac{x^{2}}{2} }
$$
Para esta parte de la función, tenemos un radical, con la única restricción que el argumento tiene que ser mayor o igual a 0:
$$
\begin{gather*}
1-y^{2}-\frac{x^{2}}{2}\geq 0\\
1-\frac{x^{2}}{2}\geq y^{2}
\end{gather*}
$$
Tras obtener las restricciones, al graficar el dominio, debería de verse de la siguiente manera:
![[Discusion1Ej2Litb|1000]]

3. Determine el valor del dominio de la siguiente función, haga su representación gráfica y calcule la ecuación de la superficie de nivel para el punto dado.

$$
f(x,y,z)=\int _{x}^{y} \frac{dt}{1+t^{2}}+\int _{0}^{z}  \frac{d\theta}{\sqrt{ 4-\theta^{2} }};\qquad(0,1,\sqrt{ 3 })  
$$
$$
\begin{align*}
f(x,y,z)&=[\arctan(t)]_{x}^{y}+[\arcsin(\theta)]_{0}^{z}\\
&=\arctan(y)-\arctan (x)+\arcsin\left( \frac{z}{2} \right)
\end{align*}
$$
Obteniendo el valor de la superficie de nivel en el punto dado:
$$
\begin{align*}
f(0,1,\sqrt{ 3 })&=\arctan(1)-\arctan(0)+\arcsin\left( \frac{\sqrt{ 3 }}{2} \right)\\
&=\frac{\pi}{4}+\frac{\pi}{3}\\
&=\frac{7}{12}\pi
\end{align*}
$$
Obteniendo la ecuación de la superficie de nivel:
$$
\begin{gather*}
\frac{7}{12}\pi=\arctan(y)-\arctan (x)+\arcsin\left( \frac{z}{2} \right)\\
\frac{7}{12}\pi+\arctan(x)-\arctan(y)=\arcsin\left( \frac{z}{2} \right)\\
z=\sin\left( \frac{7}{12}\pi+\arctan(x)-\arctan(y) \right)
\end{gather*}
$$

