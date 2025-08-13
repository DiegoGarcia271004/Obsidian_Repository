---
tags:
  - Calculo3
---
Calcule el flujo saliente de $\vec{F}=2xy\, \hat{\imath}+zy\,\hat{\jmath}-xz^{2}\,\hat{k}$ a través de $Q$, donde $Q$ es la frontera del sólido encerrado por el hiperboloide circular con ecuación $z=x^{2}+y^{2}$ y la esfera $\rho=5$ :
a. Calcule el flujo mediante la integral de flujo
b. Calcule el flujo utilizando el teorema de divergencia de Gauss
c. Calcule la circulación a través de la curva $C$ utilizando el teorema de Stokes. Donde $C$ es la curva de intersección generada en el intercepto de las dos funciones.

a.
Para encontrar el flujo mediante integrales de flujo, es necesario delimitar la superficie. Con fines de facilitar el trabajo, se trabajará con coordenadas cilíndricas, por lo que tendremos que parametrizar las funciones utilizando este sistema.

Para la esfera $\rho=5$, sabemos que $\rho =\sqrt{ x^{2}+y^{2}+z^{2} }$ por lo que $x^{2}+y^{2}+z^{2}=5^{2}$, al transformar esta ecuación en coordenadas cilíndricas obtenemos: $z=\pm\sqrt{ 25-r^{2} }$, ya que al trabajar con el paraboloide, este solamente toma valores positivos, solo tomaremos la raíz positiva de la esfera: $z=\sqrt{ 25-r^{2} }$ .
Para el paraboloide $z=x^{2}+y^{2}$, su equivalente en coordenadas cilíndricas es: $z=r^{2}$.

Para poder parametrizar estas curvas, debemos utilizar las equivalencias de cada una de las coordenadas en cilíndricas, es decir:
$$
\begin{align*}
x&=r\cos(\theta)\\
y&=r\sin(\theta)
\end{align*}
$$
Finalmente, debemos definir las superficies y sus vectores que las representan. En este ejercicio tomaremos el paraboloide como $S_{1}$ y la esfera como $S_{2}$.


$S_{1}$:
Para parametrizar nuestra primera superficie, tomaremos el vector:
$$
\vec{r}(r,\theta)=r\cos(\theta)\,\hat{\imath}+r\sin(\theta)\,\hat{\jmath}+r^{2}\,\hat{k}
$$
Por lo que nuestro flujo será:
$$
F(\vec{r}(r,\theta))=2r^{2}\cos(\theta)\cdot \sin(\theta)\,\hat{\imath}+r^{3}\sin(\theta)\,\hat{\jmath}-r^{5}\cos(\theta)\,\hat{k}
$$
Como siguiente punto se debe obtener el gradi





Como siguiente paso, necesitamos obtener nuestro $dS$, el cual está dado por $dS=(r_{r}\times r_{\theta})\,dA$:


$$
\begin{align*}
r_{r}\times r_{\theta}&=\left|
\begin{matrix}
\hat{\imath} & \hat{\jmath} &\hat{k} \\
\cos(\theta) & \sin(\theta) &2r \\
-r\sin(\theta) & r\cos(\theta) & 0
\end{matrix}
 \right|\\
&=-2r^{2}\cos(\theta)\,\hat{\imath}-2r^{2}\sin(\theta)\,\hat{\jmath}+r\,\hat{k}
\end{align*}
$$
Para poder realizar la integral es necesario realizar el producto de $F\cdot(r_{r}\times r_{\theta})$:
$$
\begin{align*}
F\cdot(r_{r}\times r_{\theta})&=-4r^{4}\cos ^{2}(\theta)\sin(\theta)-2r^{5}\sin ^{2}(\theta)+r^{6}\cos(\theta)
\end{align*}
$$
Por lo que la integral quedaría de la siguiente manera:
$$
\int_{0}^{2\pi} \int_{0}^{1} (-4r^{4}\cos ^{2}(\theta)\sin(\theta)-2r^{5}\sin ^{2}(\theta)+r^{6}\cos(\theta)) r\, dr  \, d\theta 
$$
Esto nos da:
$$
=-\frac{2\pi}{7}
$$
$S_{2}$:
De igual forma, parametrizando la segunda superficie, obtenemos:
$$
\vec{r}(r,\theta)=r\cos(\theta)\,\hat{\imath}+r\sin(\theta)\,\hat{\jmath}+\sqrt{ 25-r^{2} }\,\hat{k}
$$
Obteniendo el $dS$:
$$
\begin{align*}
r_{r}\times r_{\theta}&=\left|
\begin{matrix}
\hat{\imath} & \hat{\jmath} &\hat{k} \\
\cos\theta & \sin (\theta) & \frac{r}{\sqrt{ 25-r^{2} }} \\
-r\sin(\theta) & r\cos(\theta) & 0
\end{matrix}
 \right|
\end{align*}
$$