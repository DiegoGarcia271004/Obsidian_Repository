1. Dada la ecuación del elipsoide siguiente, encuentre:
$$
\frac{x^{2}}{16}+\frac{y^{2}}{9}+\frac{z^{2}}{4}=1
$$
a) El volumen máximo del paralelepípedo rectangular (ortoedro) encerrado en el elipsoide
b) El volumen del elipsoide como $z=f(x,y)$
c) El volumen del elipsoide como $y=f(x,z)$
d) El volumen del elipsoide como $x=f(y,z)$

a) 

Para poder definir un ortoedro dentro de la figura, podemos definir un ortoedro dentro de uno de los octantes de la siguiente forma:
![[Disc4Ej1|1000]]

Este ortoedro (del cual no conocemos sus dimensiones) será el que tendremos que optimizar, ya que por simetría, si en un octante se obtiene el ortoedro con mayor volumen, en el resto tendrá el mismo volumen por lo que solo tendremos que multiplicar 8 veces el volumen de este ortoedro en un solo octante.

El ortoedro dentro del octante tiene un largo $x$, un ancho $y$, y un alto $z$. Por lo que su volumen será:
$$
V(x,y,z)=xyz
$$

Sin embargo, sabemos que este ortoedro está delimitado por el elipsoide, así que esta será nuestra función restricción.
Recordemos que debemos ponerla en forma $G(x,y,z)=0$, por lo que:
$$
G(x,y,z)=\frac{x^{2}}{16}+\frac{y^{2}}{9}+\frac{z^{2}}{4}-1=0
$$
Con estos elementos, podemos encontrar la función a optimizar:
$$
F(x,y,z,\lambda)=xyz-\lambda\left( \frac{x^{2}}{16}+\frac{y^{2}}{9}+\frac{z^{2}}{4}-1 \right)
$$
**Condición necesaria:**
Para encontrar la condición necesaria, debemos de encontrar los puntos donde las derivadas respecto a cada variable sean igual a 0:
$$
P(x,y,z,\lambda)=
\left\{ \begin{matrix}
\frac{\partial F}{\partial x}=0 \\
\frac{\partial F}{\partial y}=0 \\
\frac{\partial F}{\partial z}=0 \\
\frac{\partial F}{\partial \lambda}=0
\end{matrix} \right.
$$



Tras meter este sistema de ecuaciones en la TI, obtenemos los siguientes puntos (nos da una gran cantidad de puntos, sin embargo no tomaremos los que solo poseen un valor, ya que representan puntos que si bien satisfacen, no tienen sentido en la ecuación. Además solo tomaremos aquellos puntos que se encuentren en el octante $x^{+},y^{+},z^{+}$ ya que es la región establecida):
El único punto que cumple estas restricciones es:
$$
\left( \frac{4\sqrt{3}}{3},\ \sqrt{3},\ \frac{2\sqrt{3}}{3},\ 4\sqrt{3} \right)
$$

Si bien podemos decir que este es el único punto que cumple, verifiquemos para confirmar que es un punto máximo.

**Condición suficiente:**
Para confirmar que este punto es, en efecto, el punto donde el volumen es máximo, debemos obtener el Hessiano coronado:
$$
\overset{ * }{ H } =\begin{vmatrix}
0 & G_{x}&G_{y}&G_{z} \\
G_{x}& F_{xx}& F_{xy}&F_{xz} \\
G_{y}& F_{yx}&F_{yy}&F_{yz} \\
G_{z}& F_{zx}&F_{zy}&F_{zz}
\end{vmatrix}
$$

de estos obtendremos tanto $\Delta_{3}$ y $\Delta_{4}$ siendo cada una de estas deltas el determinante de orden $n\times n$ con $n$ el respectivo subíndice de cada delta, y evaluaremos en cada delta el punto que obtuvimos en la condición necesaria.

$$
\begin{gather*}
\Delta_{3}|_{\left( \frac{4\sqrt{3}}{3},\ \sqrt{3},\ \frac{2\sqrt{3}}{3},\ 4\sqrt{3} \right)}=\frac{8\sqrt{ 3 }}{27}\\
\Delta_{4}|_{\left( \frac{4\sqrt{3}}{3},\ \sqrt{3},\ \frac{2\sqrt{3}}{3},\ 4\sqrt{3} \right)}=-\frac{16}{3}
\end{gather*}
$$
Por el criterio de la segunda derivada y el comportamiento de los deltas:
$$
\Delta_{3}>0,\quad \Delta_{4}<0
$$
Podemos determinar que las dimensiones del ortoedro son de:
$$
x=\frac{4\sqrt{ 3 }}{3}, \, y=\sqrt{ 3 }, \, z=\frac{2\sqrt{ 3 }}{3}
$$
Sin embargo, esto es solo del ortoedro encerrado en el primer octante, así que para obtener el valor del volumen total, tendremos que multiplicar el volumen obtenido a partir de estas dimensiones por $8$, donde el resultado final es:
$$
\boxed{\frac{64\sqrt{ 3 }}{3}\,u^{3}}
$$

b)

Para encontrar el volumen del elipsoide, debemos de establecer los límites en donde integraríamos.
Ya que es una figura simétrica, entonces podemos obtener el volumen en el primer octante, y multiplicarla por 8.

Si observamos desde arriba elipsoide (o si obtenemos la curva de nivel en $z=0$) tenemos una elipse con la ecuación:
$$
\frac{x^{2}}{16}+\frac{y^{2}}{9}=1
$$
Así podemos definir de mejor manera la región.
Ya que tomamos el primer octante, en 2D sería el primer cuadrante, y para las $x$, podemos observar que varía desde 0 hasta 4, por lo que:
$$
0<x<4
$$
Con el valor de $y$, observamos la variación vertical, esta iría desde  0 hasta la elipse superior, que al despejar su ecuación nos queda:
$$
y=3\sqrt{ 1-\frac{x^{2}}{16} }
$$
Por lo que:
$$
0<y<3\sqrt{ 1-\frac{x^{2}}{16} }
$$
Finalmente, como estamos trabajando con un "techo" que es la tapa superior del elipsoide, entonces despejando $z$ sería:
$$
z=2\sqrt{ 1-\frac{x^{2}}{16}-\frac{y^{2}}{9} }
$$
por lo que el volumen deberá de ser:
$$
8 \int _{0}^{4}\int _{0}^{3\sqrt{ 1- \frac{x^{2}}{16} }}2\sqrt{ 1-\frac{x^{2}}{16}-\frac{y^{2}}{9} } \, dy  \, dx=32\pi \,u^{3}
$$
c)

Al igual que en el literal anterior, trabajaremos con la simetría, en este caso tomaremos la elipse del plano $y=0$, esto nos deja con una elipse:
$$
\frac{x^{2}}{16}+\frac{z^{2}}{4}=1
$$
sabiendo que $x$ varía de 0 a 4:
$$
0<x<4
$$
Y despejando $z$:
$$
z=2\sqrt{ 1-\frac{x^{2}}{16} }
$$
por lo que:
$$
0<z<2\sqrt{ 1-\frac{x^{2}}{16} }
$$
Ahora, para el techo despejamos $y$:
$$
y=3\sqrt{ 1-\frac{x^{2}}{16}-\frac{z^{2}}{4} }
$$
por lo que el volumen es:
$$
8\int _{0}^{4}\int_{0}^{2\sqrt{ 1- \frac{x^{2}}{16} }} 3\sqrt{ 1-\frac{x^{2}}{16}-\frac{z^{2}}{4} } \, dz  \, dx=32\pi \,u^{3}
$$



d)

De igual manera que con los literales anteriores pero con el plano $x=0$
$$
\frac{y^{2}}{9}+\frac{z^{2}}{4}=1
$$
En este caso $y$ variaría desde 0 hasta 3:
$$
0<y<3
$$
Al despejar $z$:
$$
z=2\sqrt{ 1-\frac{y^{2}}{9} }
$$
por lo que:
$$
0<z<2\sqrt{ 1-\frac{y^{2}}{9} }
$$
Despejando $x$:
$$
x=4\sqrt{ 1-\frac{y^{2}}{9}-\frac{z^{2}}{4} }
$$
Finalmente el volumen es:
$$
8\int _{0}^{3}\int _{0}^{2\sqrt{ 1- \frac{y^{2}}{9} }} 4\sqrt{ 1-\frac{y^{2}}{9}-\frac{z^{2}}{4} } \, dz  \, dy=32\pi\,u^{3}
$$


