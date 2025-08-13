---
tags:
  - Calculo3
---
4) Suponga que en una cierta región del espacio el potencial eléctrico V está dado por:
$$
V(x,y,z)= 5x^{2}-3xy+xyz
$$
a) Determine la razón de cambio del potencial en P (3, 4, 5) en la dirección del vector
$$
v=i+j-k
$$
b) ¿En qué dirección cambia V con mayor rapidez en P?
c) ¿Cuál es la razón máxima de cambio en P?

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

