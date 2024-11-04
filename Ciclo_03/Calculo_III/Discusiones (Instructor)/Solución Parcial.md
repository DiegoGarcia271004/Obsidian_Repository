---
tags:
  - Calculo3
---
1. 
$$
\begin{align*}
\delta(x,y,z)&=15\sqrt{ y+2 }\\
r(t)&=(t^{2}-1)\hat{\jmath}+2t\hat{k}\\
-1\leq &t\leq 1
\end{align*}
$$

$$
\begin{align*}
m&=\int _{C}\rho(x,y,z) \, ds\\
m&= \int _{-1}^{1}15\sqrt{ (t^{2}-1)+2 }\cdot \sqrt{ 4t^{2}+4 } \, dt\\
 m&=30\int _{-1}^{1} \sqrt{ t^{2}+1 }\sqrt{ t^{2}+1 }\, dt\\
m&= 60\int _{0}^{1} t^{2}+1\, dt\\
m&=60\left.\left( \frac{t^{3}}{3}+t \right)\right|_{0}^{1}\\
m&=60\left( \frac{4}{3} \right) \\
m&=80
\end{align*}
$$
$$
\begin{align*}
\bar{y}&=\frac{1}{m}\int _{C}y\,\delta(x,y,z) \, ds \\
&=\frac{15}{80}\int _{-1}^{1}(t^{2}-1)(t^{2}+1) \, dt\\
&=\frac{60}{80}\int _{0}^{1}t^{4}-1 \, dt\\
&=\frac{3}{4}\left.\left( \frac{t^{5}}{5}-t \right)\right|_{0}^{1}\\
&=\frac{3}{4}\left( -\frac{4}{5} \right)\\
&= -\frac{3}{5}
\end{align*}
$$

4. $$
\int _{C} \vec{F}\cdot d\vec{r}  
$$ 