---
tags:
  - Calculo3
---
1. La integral Gaussiana es una herramienta que se utiliza grandemente en el cálculo en distintas áreas, además de ser una integral que no tiene una antiderivada elemental, por lo que: Demuestre que la integral Gaussiana cumple la siguiente igualdad:
$$
\int _{-\infty}^{\infty} e^{-x^{2}} \, dx=\sqrt{ \pi } 
$$
$$
\begin{align}
I&=\int _{-\infty}^{\infty} e^{-x^{2}}\,dx\\
I^{2}&=\left( \int _{-\infty}^{\infty} e^{-x^{2}}\,dx\\ \right)\left( \int _{-\infty}^{\infty} e^{-x^{2}}\,dx\\ \right)\\
&=\left( \int _{-\infty}^{\infty} e^{-x^{2}}\,dx \right)\left( \int _{-\infty}^{\infty} e^{-y^{2}}\,dy\\ \right)\\
&=\int _{-\infty}^{\infty}\int _{-\infty}^{\infty}e^{-x^{2}}e^{-y^{2}} \, dx  \, dy\\
&=\int _{-\infty}^{\infty}\int _{-\infty}^{\infty} e^{-(x^{2}+y^{2})}\,dx\,dy \\
&= \iint e^{-r^{2}} \, dA\\
&= \int _{0}^{2\pi}\int _{0}^{\infty}e^{-r^{2}}\cdot r \, dr  \, d\theta \\
 &=\int _{0}^{2\pi}\left[ -\frac{e^{-r^{2}}}{2} \right]_{0}^{\infty} \, dx  \\
&=\int _{0}^{2\pi} \, d\theta \cdot\left( -\frac{e^{-\infty}}{2}+\frac{e^{0}}{2}  \right) \\
&=2\pi\cdot \frac{1}{2} \\
&=\pi \\
I^{2}&=\pi \\
&\boxed{I=\sqrt{ \pi }}
\end{align}
$$

2. ¿Cuál es el valor de la siguiente integral?
$$
\int _{0}^{4}\int _{x/2}^{2} e^{y^{2}} \, dy  \, dx
$$

$$
\begin{gather*}
0\leq x\leq 2y\\
0\leq y\leq 2\\
\int _{0}^{2}\int _{0}^{2y}e^{y^{2}} \, dx  \, dy\\
\int _{0}^{2}e^{y^{2}}2y \, dy\\
u=y^{2}\quad y\to 0, \,u\to 0\quad y\to2,\, u\to 4\\
\int _{0}^{4} e^{u} \, du=e^{4}-1 
\end{gather*}
$$

3. Resuelva la siguiente integral:
$$
\int _{0}^{\sqrt{ 2 }/2}\int _{y}^{\sqrt{ 1-y^{2} }} \frac{y^{2}}{\sqrt{ x^{2}+y^{2} }} \, dx  \, dy 
$$
$$
\begin{gather*}
\iint r\sin ^{2}\theta \,dA\\
\int _{0}^{\frac{\pi}{4}}\int _{0}^{1} r^{2}\sin ^{2} \theta \, dr  \, d\theta\\
\frac{1}{3} \int _{0}^{\frac{\pi}{4}} \sin ^{2}\theta \, d\theta\\
\frac{1}{6}\int _{0}^{\frac{\pi}{4}} 1-\cos(2\theta) \, d\theta\\
\frac{1}{6}\left[ \theta-\frac{\sin(2\theta)}{2} \right]_{0}^{\frac{\pi}{4}}\\
\frac{1}{6}\left[ \frac{\pi}{4}-\frac{1}{2} \right]\\
\frac{\pi-2}{24}
\end{gather*}
$$
