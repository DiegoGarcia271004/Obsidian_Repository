---
tags:
  - Calculo3
---
1. Encuentre el valor de la siguiente integral:
$$
\int x^{2}\sqrt[2]{x\sqrt[3]{ x\sqrt[4]{ x\dots } }  } \, dx 
$$
$$
\begin{align*}
&\int x^{2}x^{\frac{1}{2}}x^{\frac{1}{6}}x^{\frac{1}{24}}\dots \, dx\\
&\int x^{1+1+ \frac{1}{2}+ \frac{1}{6}+ \frac{1}{24}+\dots}  \, dx\\
&\int x^{\frac{1}{0!}+ \frac{1}{1!}+ \frac{1}{2!}+ \frac{1}{3!}+ \frac{1}{4!}+\dots} \, dx  \\
&\int x^{\sum_{k=0}^{\infty} \frac{1}{k!}} \, dx\\
&\int x^{e} \, dx\\
&\frac{x^{e+1}}{e+1}   +C
\end{align*} 
$$
2. Demuestre mediante series de Maclaurin la siguiente propiedad:
$$
e^{ix}=\cos(x)+i\sin(x)
$$
3. Encuentre la serie de Maclaurin de la siguiente función:
$$
f(x)=\sinh(x)
$$
$$
\begin{align*}
f(0)&=0&f'(0)&=1&f''(0)&=0\\
f'''(0)&=1&f^{(IV)}(0)&=0&f^{(V)}(0)&=1\\
\end{align*}
$$

$$
\begin{align*}
\sinh(x)&=\frac{0}{0!}+1 \frac{x}{1!}+\frac{0x^{2}}{2!}+\frac{1x^{3}}{3!}+\frac{0x^{4}}{4!}+\frac{1x^{5}}{5!}+\dots\\
\sinh(x)&=x+\frac{x^{3}}{6}+\frac{x^{5}}{120}+\dots\\
\sinh(x)&=\sum_{k=0}^{\infty} \frac{x^{2k+1}}{(2k+1)!}
\end{align*}
$$
4. Partiendo de la serie encontrada anteriormente, demuestre que:
$$
\frac{e^{x}-e^{-x}}{2}=\sinh(x)
$$
$$
\begin{align*}
e^{x}-e^{-x}
&=\sum_{k=0}^{\infty} \frac{x^{k}}{k!}-\sum_{k=0}^{\infty} \frac{(-x)^{k}}{k!}\\
&=\sum_{k=0}^{\infty } \frac{x^{k}-(-1)^{k}x^{k}}{k!}\\
&=\sum_{k=0}^{\infty } \frac{x^{k}(1+(-1)^{k+1})}{k!}\\
&=\frac{0}{0!}+ \frac{2x}{1!}+ \frac{0x^{2}}{2!}+\frac{2x^{3}}{3!}+\frac{0x^{4}}{4!}+ \frac{2x^{5}}{5!}\\
&=2\sum_{k=0}^{\infty} \frac{x^{2k+1}}{(2k+1)!}\\
\frac{e^{x}-e^{-x}}{2}&=\frac{2}{2}\sum_{k=0}^{\infty} \frac{x^{2k+1}}{(2k+1)!}\\
&=\sum_{k=0}^{\infty} \frac{x^{2k+1}}{(2k+1)!}\\
Q.E.D.
\end{align*}
$$


5. Determinar el polinomio de Maclaurin de $x\tan ^{-1}(x)$ que permita aproximar $\frac{1}{2}\tan ^{-1}\left( \frac{1}{2} \right)$ con un error máximo permisible de $10^{-3}$

