---
tags:
  - Calculo3
---
1. Demuestre que el elipsoide:
$$
S: 3x^{2}+2y^{2}+z^{2}=9
$$
y la esfera
$$
H: x^{2}+y^{2}+z^{2}-8x-6y-8z+24=0
$$
son tangentes entre sí en el punto $P(1,1,2)$

![[Disc3Ej1|1000]]

2. Sea $z(x,y)=g(u,v)$ con $u=x^{2}y^{2}$ y $v=xy$, encuentre $\partial^{2} z/\partial x\partial y$

![[Disc3Ej2|1000]]



3.  Suponga que en una cierta región del espacio el potencial eléctrico V está dado por:
$$
V(x,y,z)= 5x^{2}-3xy+xyz
$$
a) Determine la razón de cambio del potencial en P (3, 4, 5) en la dirección del vector
$$
v=i+j-k
$$
b) ¿En qué dirección cambia V con mayor rapidez en P?
c) ¿Cuál es la razón máxima de cambio en P?
d) ¿Encuentre las direcciones en las que la razón de cambio es 0?

$$
\begin{align*}
a)& \\\\
\nabla \vec{V} &=\frac{\partial V}{\partial x}\hat{\imath}+\frac{\partial V}{\partial y}\hat{\jmath}+\frac{\partial V}{\partial z}\hat{k} \\
\frac{\partial V}{\partial x}&=10x-3y+yz\\
\frac{\partial V}{\partial y}&=-3x+xz\\
\frac{\partial V}{\partial z}&=xy\\
\left . V_{x} \right|_{(3,4,5)}&=30-12+20=38\\
V_{y}|_{(3,4,5)}&=-9+15=6\\
V_{z}|_{(3,4,5)}&=12\\
\\
D_{\hat{u}}V(x,y,z)&=\nabla V \cdot \vec{u}\\
&=\langle 38,6,12 \rangle \cdot \langle 1,-1 ,1\rangle \\
&=38-6+12\\
&=44
\end{align*}
$$

$$
\begin{align*}
b)&\\
\\
\nabla V&=\langle 38,6,12 \rangle \Rightarrow \vec{u} = \hat{\nabla V}\\
\|\nabla V\|&=\sqrt{ 38^{2}+6^{2}+12^{2} }=2\sqrt{ 406 } \approx 40.30\\
\vec{u}_{max}&=\frac{\nabla V}{\|\nabla V\|} \Rightarrow \left\langle  \frac{19\sqrt{ 406 }}{406}, \frac{3\sqrt{ 406 }}{406}, \frac{3\sqrt{ 406 }}{203}  \right\rangle 
\end{align*}
$$
$$
\begin{align*}
c)&\\
\\
D_{\vec{u}_{max}}V(x,y,z)&=\vec{u}_{max}\cdot \nabla V\\
&=\left\langle  \frac{19\sqrt{ 406 }}{406}, \frac{3\sqrt{ 406 }}{406}, \frac{3\sqrt{ 406 }}{203}  \right\rangle \cdot \langle 38,6,12 \rangle\\
&=\frac{361\sqrt{ 406 }}{203}+\frac{9\sqrt{ 406 }}{203}+\frac{36\sqrt{ 406 }}{203} \\
&=2\sqrt{ 406 } 
\end{align*}
$$
d) Para poder encontrar la dirección en la que el  cambio sea 0, entonces debe de cumplir la condición de que: $D_{\vec{u}}=0$ o $\nabla V\cdot \vec{u}=0$
Ya conociendo el valor del gradiente:
$$
\nabla V=\langle 38,6,12 \rangle 
$$
Al aplicarle el producto punto por el vector 
$$
\vec{u}=\langle a,b,c \rangle 
$$
debe de ser 0:
$$
\nabla V\cdot \vec{u}=\langle 38,6,12 \rangle\cdot \langle a,b,c \rangle=0  
$$
Desarrollando
$$
38a+6b+12c=0
$$
Esto es un plano, y representa que cualquier vector que se encuentre en este plano será ortogonal (hará que el cambio sea 0) 

4. Sea la función $f(x,y)=x^{2}y+3xy^{3}$. Aproximar el cambio en $f$ cuando $x$ cambia de 2 a 2.05 y $y$  cambia de 1 a 1.02.

$$

\begin{gather*}
\text{Obteniendo la función en diferenciales }\\
df=\frac{\partial f}{\partial x}dx+\frac{\partial f}{\partial y}dy\\
\text{Calculando las derivadas parciales}\\
\frac{\partial f}{\partial x}=2xy+3y^{2}|_{(2,1)}=7\\
\frac{\partial f}{\partial y}=x^{2}+9xy^{2}|_{(2,1)}=22\\
\text{Obteniendo los diferenciales}\\
dx=(2.05-2)=0.05\\
dy=(1.02-1)=0.02\\
\text{Consiguiendo el valor del diferencial}\\
df=7(0.05)+22(0.02)=\boxed{0.79}
\end{gather*}
$$
