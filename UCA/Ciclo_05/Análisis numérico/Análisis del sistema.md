
## Encontrando puntos de equilibrio

Retomando las ecuaciones del sistema de Lorentz:
$$
\left\{ \begin{align*}
\dot{x} &= \sigma(y-x) \\
\dot{y}&= x(\rho-z)-y \\
\dot{z}&=xy-\beta z
\end{align*} \right.
\tag{1}
$$
Si buscamos encontrar un punto de equilibrio, podemos definir este sistema como un vector de ecuaciones. Lo que procederemos a igualar a 0 y resolvemos:
$$
\begin{gather*}
F=\langle \sigma(y-x),x(\rho-z)-y,xy-\beta z \rangle \tag{2} \\
F=0
\end{gather*}
$$
Encontrando una forma general:
$$
\left\{ \begin{align}
0 &= \sigma(y-x) &(3)\\
0&= x(\rho-z)-y &(4)\\
0&=xy-\beta z &(5)
\end{align} \right.
$$

Despejando $y$ de $(3)$:
$$
\begin{gather}
0=\sigma(y-x)\\
0=y-x\\
y=x \tag{6}
\end{gather}
$$
Sustituyendo $(6)$ en $(4)$:
$$
\begin{gather}
0=x(\rho-z)-x\\
0=x(\rho-z-1) \tag{7}
\end{gather}
$$
Esta resolución nos presenta dos casos distintos:
$$
\begin{cases}
x=y=0 &(8)\\
z=\rho-1&(9)
\end{cases}
$$
Para obtener el punto de equilibrio, sustituimos $(8)$ y $(9)$ en $(5)$:

- Sustituyendo $(8)$ en $(5)$
$$
\begin{gather}
0=(0)(0)-\beta z\\
0=-\beta z\\
z=0
\end{gather}
$$
	Con este valor, podemos decir entonces que el primer punto de equilibrio es: $(0,0,0)$ 

- Sustituyendo $(9)$ en $(5)$
$$
0=xy-\beta z
$$
	Ya que sabemos que $x=y$, entonces:
$$
\begin{gather}
0=x^{2}-\beta (\rho-1)\\
x^{2}=\beta(\rho-1)
\end{gather}
$$
	Este resultado también nos proporciona dos casos:

$$
x=y=\sqrt{ \beta(\rho-1) }\qquad x=y=-\sqrt{ \beta(\rho-1) }
$$
Por lo que podemos obtener otros 2 puntos de equilibrio, siendo estos: $(\sqrt{ \beta(\rho-1) },\sqrt{ \beta(\rho-1)},\rho-1)$ y $(-\sqrt{ \beta(\rho-1)}, -\sqrt{ \beta(\rho-1)},\rho-1)$

Por lo que de forma ordenada:
$$
\begin{cases}
(0,0,0) \\
(\sqrt{ \beta(\rho-1)},\sqrt{ \beta(\rho-1)},\rho-1) \\
(-\sqrt{ \beta(\rho-1)},-\sqrt{ \beta(\rho-1)},\rho-1)
\end{cases}
\tag{10}
$$
---

## Analizando la estabilidad

Según lo dicho por Domingo [1], si queremos analizar la estabilidad de las soluciones (puntos fijos) dado un sistema de ecuaciones diferenciales homogéneas con coeficientes constantes que sigue la forma:
$$
x'=A\cdot x
$$
Donde $x'$ es el sistema de ecuaciones diferenciales, $A$ una matriz de constantes, y $x$ una matriz de constantes, entonces debemos de encontrar $p(\lambda)$, siendo este el polinomio característico que posee la siguiente forma:
$$
p(\lambda)=\det(J-\lambda I)
$$
Donde $J$ representa la matriz jacobiana del campo vectorial formado por el sistema de ecuaciones diferenciales. Y de las raíces de dicho polinomio característico se cumplen las siguientes afirmaciones:

1. Si todas las raíces de $p(\lambda)=0$ tienen la parte real negativa, todas las soluciones del sistema $x'=A\cdot x$ son asintóticamente estables.
2. Si al menos una de las raíces de $p(\lambda)=0$ tiene parte real positiva, todas las soluciones del sistema $x'=A\cdot x$ son inestables.

Por lo que procederemos a obtener una expresión general para $p(\lambda)$:

Primeramente buscaremos plantear nuestro matriz jacobiana:
Sea $F$ nuestro campo vectorial (o nuestro sistema de ecuaciones diferenciales de Lorentz), entonces:
$$
\begin{align}
J(F)&=\begin{pmatrix}
\dot{x}_{x} & \dot{x}_{y}&\dot{x}_{z} \\
\dot{y}_{x}&\dot{y}_{y}&\dot{y}_{z} \\
\dot{z}_{x}&\dot{z}_{y}&\dot{z}_{z}
\end{pmatrix} \\
&=\begin{pmatrix}
-\sigma&\sigma&0 \\
\rho-z&-1&-x \\
y&x&-\beta
\end{pmatrix}
\end{align}
$$
Planteando la expresión $\det(J-\lambda I)$ donde $I$ es la matriz identidad:
$$
\begin{align*}
\det(J(F)-\lambda I)&=\det\left(\begin{pmatrix}
-\sigma&\sigma&0 \\
\rho-z&-1&-x \\
y&x&-\beta
\end{pmatrix}-\lambda \begin{pmatrix}
1&0&0 \\
0&1&0 \\
0&0&1
\end{pmatrix}\right)\\
&=\det\begin{pmatrix}
-\sigma-\lambda&\sigma&0 \\
\rho-z&-1-\lambda&-x \\
y&x&-\beta-\lambda
\end{pmatrix} \tag{11}
\end{align*}
$$
Esta matriz será la que nos devolverá nuestro polinomio característico. Por motivos de orden, la dejaremos expresada en forma de matriz y una vez evaluemos los valores, entonces resolveremos el determinante.

---

## Evaluando los parámetros dados y analizando los resultados.

1. $\rho=28$, $\sigma=10$, $\beta=8/3$

Debido a que ya obtuvimos una expresión general para los puntos fijos, procederemos a evaluar los parámetros en $(10)$ para obtenerlos:
$$
\begin{cases}
(0,0,0) \\
(6\sqrt{ 2 },6\sqrt{ 2 },27) \\
(-6\sqrt{ 2 },-6\sqrt{ 2 },27)
\end{cases}
$$
Estos valores los evaluaremos en nuestra matriz $(11)$, y encontraremos los polinomios respectivos:

- $(0,0,0)$
$$
\begin{gather}
p(\lambda)=-\lambda^{3}-\frac{41}{3}\lambda^{2}+\frac{722}{3} \lambda+720
\end{gather}
$$
Resolviendo $p(\lambda)=0$ obtenemos los valores de:
$$
\lambda_{1}=-22.83 \quad \lambda_{2}=-2.67 \quad \lambda_{3}=11.83
$$
Al observar estos datos, podemos decir que cumple nuestra segunda condición, por lo que concluimos que para nuestro primer punto fijo, **las soluciones son inestables**.

- $(6\sqrt{ 2 },6\sqrt{ 2 },27)$
$$
p(\lambda)=-\lambda^{3}-\frac{41}{3}\lambda^{2}+\frac{304}{3} \lambda-1440
$$
Resolviendo $p(\lambda)=0$:
$$
\lambda_{1}=0.093+10.2i\quad \lambda_{2}=0.093-10.2i\quad \lambda_{3}=-13.855
$$
Las raíces también cumplen la segunda condición, por lo que una vez más, **las soluciones son inestables**.

- $(-6\sqrt{ 2 },-6\sqrt{ 2 },27)$
$$
p(\lambda)=-\lambda^{3}-\frac{41}{3}\lambda^{2}-\frac{304}{3} \lambda-1440
$$
Resolviendo $p(\lambda)=0$
$$
\lambda_{1}=0.093+10.2i\quad \lambda_{2}=0.093-10.2i\quad \lambda_{3}=-13.855
$$

2. $\rho=18$, $\sigma=9$, $\beta=10/3$

Evaluando los parámetros en $(10)$ para encontrar los puntos fijos:
$$
\begin{cases}
(0,0,0) \\
(\sqrt{ 503 }/3,\sqrt{ 503 }/3,17) \\
(-\sqrt{ 503 }/3,-\sqrt{ 503 }/3,17)
\end{cases}
$$
Evaluando los puntos y parámetros en $(11)$ y encontrando los polinomios:

- $(0,0,0)$
$$
p(\lambda)=-\lambda^{3}-\frac{40}{3}\lambda^{2}-\frac{359}{3} \lambda+510
$$
Resolviendo $p(\lambda)=0$:
$$
\lambda_{1}=-18.34\quad \lambda_{2}=-3.33 \quad \lambda_{3}=8.34
$$
Por la naturaleza de los signos de las raíces, concluimos que las soluciones son **inestables**.

- $(\sqrt{ 503 }/3,\sqrt{ 503 }/3,17)$
$$
p(\lambda)=-\lambda^{3}-\frac{40}{3}\lambda^{2}-\frac{803}{3} \lambda-1006
$$
Resolviendo $p(\lambda)=0$:
$$
\lambda_{1}=−0.37+8.93i \quad \lambda_{2}=−0.37-8.93i \quad \lambda_{3}=-12.59
$$
En este caso, las respuestas de las raíces cumplen con la primera condición, por lo que las soluciones son **asintóticamente estables**.

- $(-\sqrt{ 503 }/3,-\sqrt{ 503 }/3,17)$
$$
p(\lambda)=-\lambda^{3}-\frac{40}{3}\lambda^{2}-\frac{803}{3} \lambda-1006
$$
Resolviendo $p(\lambda)=0$:
$$
\lambda_{1}=−0.37+8.93i \quad \lambda_{2}=−0.37-8.93i \quad \lambda_{3}=-12.59
$$
Dado a que las raíces son iguales que en el punto anterior, se llega a la misma conclusión. **Las soluciones son asintóticamente estables**.

---

Ok, estoy familiarizado con lo que es un sistema de ecuaciones; que es básicamente un conjunto de ecuaciones relacionadas entre sí para describir una situación en particular, como en el caso de los sistemas de ecuaciones lineales. No se pueden resolver una ecuación por sí misma, sino que se tienen que resolver en conjunto.

  

Ahora, visualizar eso, pero con ecuaciones diferenciales. Damn.

  

Ejemplo de uno es el sistema de ecuaciones diferenciales de un modelo simplificado para la convección atmosférica de Edward Lorenz:

$$\begin{cases}

\dot{x} &= \sigma(y-x) \\ \dot{y} &= x(\rho-z) - y \\ \dot{z} &= xy - \beta z

\end{cases}$$


## Divergencia del sistema de Lorenz

La divergencia de un campo vectorial es útil para describir el "flujo" de los vectores en un punto dado. Una divergencia positiva indica un "origen", así como una divergencia negativa indica un "sumidero"; mientras que una divergencia de cero indica que la cantidad de "flujo" que entra es el mismo del que sale: no es un origen ni sumidero.

  

Para calcular la divergencia del sistema descrito por (1), derivamos parcialmente los componentes de (2) respecto a las variables independientes:

$$\nabla \cdot \mathbf{F}=\frac{ \partial M }{ \partial x } +\frac{ \partial N }{ \partial y } +\frac{ \partial P }{ \partial z } =-(\sigma +\beta+1)\tag{12}$$

(12) describe que la divergencia del sistema es constante y que su valor depende de los parámetros $\sigma$ y $\beta$. Que la divergencia sea una constante negativa (puesto que el sistema de Lorenz asume parámetros positivo) implica que todos los puntos son un sumidero de flujo; es decir, que respecto al tiempo, el espacio de fase experimenta una contracción constante. Geométricamente hablando, si se tiene un sólido en el espacio de fase, conforme pasa el tiempo, este experimentaría una pérdida de volumen, deformando el sólido de manera que el volumen decrece, tendiendo a cero.

  

Esta característica del espacio de fase es el que permite la formación del atractor de Lorenz, que es considerado un elemento fractal sin volumen en el espacio de fase donde las trayectorias quedan atrapadas.

  

![[space-contraction.png]]

  


## Integral de flujo sobre el espacio de fase
$$
\frac{dV(t)}{dt}=\iint\limits_{S(t)} \mathbf{F} \cdot d\mathbf{S}
$$
Si queremos encontrar una expresión para la integral de flujo, entonces podemos aplicar el teorema de divergencia de Gauss, el cuál dicta:
$$
\iint_{\partial S}F\cdot dS=\iiint_{S}\nabla\cdot F\,dV
$$
Debido a que ya conocemos el valor de la divergencia por la ecuación $(12)$, podemos realizar las siguientes operaciones:

$$
\begin{align*}
\frac{dV(t)}{dt}&=\iiint_{V(t)}-(\sigma+1+\beta)\,dV\\
&=-(\sigma+1+\beta)\iiint_{V(t)}dV\\
\frac{dV(t)}{dt}&=-(\sigma+1+\beta )V(t)
\end{align*}
$$
Con esto, hemos llegado a una expresión para la integral de flujo:
$$
\boxed{\frac{dV(t)}{dt}=-(\sigma+1+\beta )V(t)}\tag{13}
$$

## Volumen respecto al tiempo

El resultado de la ecuación $(13)$ nos dio una ecuación diferencial que al resolverla nos permitirá encontrar una expresión para el volumen del espacio de fase. Esta es posible de resolver utilizando un método de separación de variables:
$$
\begin{gather}
\frac{dV}{dt}=-(\sigma+1+\beta)V\\
\frac{dV}{V}=-(\sigma+1+\beta)dt\\
\int \frac{dV}{V}=\int -(\sigma+1+\beta)dt\\
\ln|V|=-(\sigma+1+\beta)t+C\\
V=e^{-(\sigma+1+\beta)t+C}\\
V(t)=Ce^{-(\sigma+1+\beta)t}\tag{14}
\end{gather}
$$

## Campos conservativos

Un campo conservativo $\mathbf{F}$ es aquel campo que representa ser un gradiente de una función potencia $\phi$, es decir, $\mathbf{F}=\nabla\phi$, como se describe J. Stewart [2]. Una de las propiedades de los campos vectoriales conservativos es que las integrales de línea de un punto a otro tienen el mismo resultado independientemente de la trayectoria; y en consecuencia, la integral de línea de una trayectoria cerrada es $0$. Que un campo sea conservativo en la física implica situaciones en la que la energía de las fuerzas que componen al campo se conserva. Para el modelo de convección atmosférica de Lorenz, que el sistema sea conservativo implicaría que no hay disipación de "energía".

  

Un método para verificar si un campo es conservativo, igualmente indicado en [1] es obtener $\nabla \times \mathbf{F}$, el rotacional del campo; y si el campo vectorial $\mathbf{F}$ es irrotacional, es decir, que el $\nabla \times \mathbf{F}=0$, entonces se dice que el campo es conservativo. Esto es porque el rotacional de un campo vectorial describe la tendencia de los vectores a formar espirales o remolinos.

  

Utilizando (1) obtenemos el siguiente rotacional:

$$\begin{align}

\nabla \times \mathbf{F} &=

 \left( \frac{ \partial P }{ \partial y } -\frac{ \partial N }{ \partial z } \right)\mathbf{i}+\left( \frac{ \partial M }{ \partial z } -\frac{ \partial P }{ \partial x } \right)\mathbf{j}+\left( \frac{ \partial N }{ \partial x } -\frac{ \partial M }{ \partial y } \right)\mathbf{k} \\

&= 2x\mathbf{i}-y\mathbf{j}+(\rho-z-\sigma)\mathbf{k} \tag{5n+1}

\end{align}$$

 El campo vectorial $\mathbf{F}$, claramente, no es irrotacional. Por lo tanto, se concluye que el modelo de convección atmosférica de Lorenz **no es un sistema conservativo**. Hay remolinos o espirales en el espacio de fase, el atractor de Lorenz, por lo que solo observando el espacio de fase se podía concluir que el campo no es irrotacional. Sin embargo, obtener (5n+1) sirve como una demostración rigurosa de que el sistema no es conservativo.


# Referencias

[1] Domingo, Alcaraz y Candela. “Estabilidad de ecuaciones diferenciales”. Departamento de Matemática Aplicada y Estadística. Accedido el 13 de junio de 2025. [En línea]. Disponible: [https://www.dmae.upct.es/~paredes/am_ti/apuntes/Tema%203.%20Estabilidad%20de%20Ecuaciones%20Diferenciales.pdf](https://www.dmae.upct.es/~paredes/am_ti/apuntes/Tema%203.%20Estabilidad%20de%20Ecuaciones%20Diferenciales.pdf)

[2] J. Stewart, _Cálculo de varias variables: Trascendentes tempranas_, 7ª ed. México: Cengage Learning, 2012.
