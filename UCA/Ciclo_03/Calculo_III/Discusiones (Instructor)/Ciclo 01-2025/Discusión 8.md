1. Una esfera maciza de $R=1$ y densidad variable $\rho=\rho_{0}(x^{2}+y^{2}+z^{2})$. Está centrada en el polo. Utiliza integrales de triples para calcular los momentos de inercia respecto a los ejes $x,y$ y $z$.

---
$$
I_{x}=\iiint_{V}\rho(x,y,z)(y^{2}+z^{2})\,dV\qquad I_{y=}\iiint_{V}\rho(x,y,z)(x^{2}+z^{2})\qquad I_{z}=\iiint_{V}\rho(x,y,z)(x^{2}+y^{2})
$$

$$
\begin{align*}
I_{x}&=\rho_{0}\int _{0}^{2\pi}\int _{0}^{\pi}\int _{0}^{1} \rho^{2}\cdot(\rho^{2}\sin ^{2} \theta \sin ^{2} \phi+\rho^{2}\cos ^{2}\phi)\rho^{2} \sin \phi   \, d\rho  \, d\phi  \, d\theta\\
&=\rho_{0}\int _{0}^{2\pi}\int _{0}^{\pi}\int _{0}^{1}\rho^{6}(\sin ^{2}\theta \sin ^{3}\phi+\cos ^{2}\phi \sin \phi)\,d\rho\,d\phi\,d\theta\\\\
&=\frac{8\pi}{21}\rho_{0}
\end{align*}
$$
$$
\begin{align*}
I_{y}&=\rho_{0}\int _{0}^{2\pi}\int _{0}^{\pi}\int _{0}^{1}\rho^{2}\cdot \rho^{2}(\sin ^{2}\phi \cos ^{2}\theta+\cos ^{2}\theta)\rho^{2}\sin \phi\,d\rho\,d\phi\,d\theta\\
&=\frac{8\pi}{21}\rho_{0}
\end{align*}
$$
$$
\begin{align*}
I_{z}&=\rho_{0}\int _{0}^{2\pi}\int _{0}^{\pi}\int _{0}^{1} \rho^{2}\rho^{2}\sin ^{2}\phi \rho^{2}\sin \phi\,d\rho\,d\phi\,d\theta\\
&=\frac{8\pi}{21}\rho_{0}
\end{align*}
$$

---

2. Una lámina delgada con densidad superficial constante δ ocupa la región triangular delimitada por los puntos $(0,0),(2,0)$ y $(4,0)$. Usa integrales dobles para encontrar el centro de masa de la lámina.

---

$$
\begin{gather*}
0\leq x\leq 2\\
0\leq y\leq -2x+4
\end{gather*}
$$
$$
\begin{gather*}
M=\delta \int _{0}^{2}\int _{0}^{-2x+4}  \, dy  \, dx=4\delta\\
\bar{x}=\frac{1}{M}\int _{0}^{2}\int _{0}^{-2x+4}\delta x \, dy  \, dx=\frac{2}{3}\\
\bar{y}=\frac{1}{M}\int _{0}^{2}\int _{0}^{-2x+4}y\delta \, dx  \, dx= \frac{4}{3}
\end{gather*} 
$$

---

3. 

$$
M=\int _{C}\rho\cdot A(t)\cdot  ds 
$$
$$
x'(t)=\cos t-t\sin t,\qquad y'(t)=\sin t+t\cos t
$$
$$
ds=\sqrt{ t^{2}+1 }dt
$$
$$
M=3\int _{0}^{2\pi} (1+0.5t)\sqrt{ t^{2}+1 } \, dt=192.036 \text{ um} 
$$
