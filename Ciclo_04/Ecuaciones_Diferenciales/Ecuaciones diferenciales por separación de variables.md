---
tags:
  - EcuacionesDiferenciales
---
## Método de separación de variables

Para hacer uso de este método es necesario el utilizar la notación de Leibniz para facilitar el proceso, el método consiste en, como su nombre indica, separar las variables que se tienen en la ecuación, y colocarlas con su diferencial propio (por esto la notación de Leibniz).

---
#### Ejemplo 1:

Resuelva la siguiente ecuación diferencial:
$$
xy'=y
$$
En este ejemplo tenemos una ecuación tal que la derivada de una función multiplicada por una variable $x$ es igual a la función original.
Primeramente debemos pasar la notación a notación de Leibniz.
$$
x \frac{dy}{dx}=y
$$
Una vez cambiada la notación, procedemos a poner todos los diferenciales en numerador, es decir, no debe de haber ningún diferencial en los denominadores, esto se logra pasando el $dx$ a multiplicar al otro lado:
$$
x\,dy=y\,dx
$$
Ahora, procederemos a agrupar las variables con sus respectivos diferenciales:
$$
\frac{dy}{y}=\frac{dx}{x}
$$
De esta forma ya agrupamos las diferentes variables, ahora procederemos a aplicar la integración para obtener las funciones.
$$
\begin{align*}
\int \frac{dy}{y}&=\int \frac{dx}{x}\\
\ln(y)+C_{1}&=\ln(x)+C_{2}
\end{align*}  
$$
Es importante mencionar que al no ser estas integrales definidas, a cada una de las antiderivadas se le debe de sumar una constante.
Ya realizada la integración, se debe de despejar la función original, para esto podemos pasar la constante $C_{1}$ a restar al lado de las $x$, esto dejaría una diferencia $C_{2}-C_{1}$, ya que la restas de dos constantes sigue siendo una constante, se le puede asignar una tercera constante a esta resta.
$$
\begin{align*}
\ln(y)&=\ln(x)+C_{2}-C_{3}\\
\ln(y)&=\ln(x)+C_{3}
\end{align*}
$$
Una vez arreglada las constantes, podemos $e$ a cada lado de la ecuación para deshacernos del logaritmo.
$$
\begin{align*}
e^{\ln(y)}&=e^{\ln(x)+C_{3}}\\
y&=e^{\ln(x)}e^{C_{3}}\\
y&=xe^{C_{3}}
\end{align*}
$$
De la misma manera que paso con la resta de constantes, $e$ elevado a una constante seguirá siendo una constante, por lo que la podemos cambiar también por una constante, quedándonos de esta manera la función.
$$
y=Cx
$$
Esta función cumple con la ecuación diferencial propuesta (la comprobación se deja como ejercicio para el lector). Sin embargo, esta no es una función en específica, sino que es una familia de funciones, puede ser cualquier función que posea esta forma solo cambiándole la constante de esta, a este tipo de solución se le conoce como **Solución general de la ecuación**.

---
#### Ejemplo 2:

Resuelva la siguiente ecuación diferencial con la restricción dada:
$$
xy'=y\qquad \left.\frac{dy}{dx}\right|_{x=0}=4
$$
Esta ecuación diferencial posee una restricción, por lo tanto es necesario que el resultado cumpla esta.

En el ejemplo 1, obtuvimos la familia de funciones que dan solución a la ecuación diferencial, por lo tanto solo debemos buscar que cumpla con la condición.

Ya que dice que la derivada de la función evaluada en 0 debe ser igual a 4, entonces derivamos nuestra función:
$$
\begin{align*}
y&=Cx\\
y'&=C
\end{align*}
$$
La derivada es una constante, por lo que al evaluarla en cualquier punto, siempre dará como resultado la misma constante, así que podemos decir que la constante es igual a 4, quedándonos una solución específica a la ecuación, a la cual también se le conoce como Problema de valor inicial o Problema de Cauchy.
$$
y=4x
$$
---

#### Ejercicios:

Resuelva las siguientes ecuaciones diferenciales:

1) $\frac{dy}{dx}+4xy=0$ 
$$
\begin{align*}
\frac{dy}{dx}&=-4xy\\
dy&=-4xy\,dx\\
\frac{dy}{y}&=-4x\,dx\\
\int \frac{dx}{y}&=-4\int x \, dx \\
\ln(y)+C_{1} &=-4\left( \frac{x^{2}}{2} \right)+C_{2}\\
\ln(y)&=-2x^{2}+C_{2}-C_{1}\\
\ln(y)&=-2x^{2}+C_{3}\\
e^{\ln(y)}&=e^{-2x^{2}+C_{3}}\\
y&=e^{-2x^{2}}e^{C_{3}}\\
y&=Ce^{-2x^{2}}
\end{align*}
$$
2) $y'=y$
$$
\begin{align*}
\frac{dy}{dx}&=y\\
dy&=y\,dx\\
\frac{dy}{y}&=dx\\
\int \frac{dy}{y}&=\int  \, dx\\
\ln(y)+C_{1}&=x+C_{2}\\
\ln(y)&=x+C_{2}-C_{1}\\
e^{\ln(y)}&=e^{x+C_{3}}\\
y&=Ce^{x}  
\end{align*}
$$
3) $\frac{dy}{dx}=\frac{x}{y}$
$$
\begin{align*}
y\,dy&=x\,dx\\
\int y \, dy&=\int x \, dx\\
  \frac{y^{2}}{2}+C_{1}&=\frac{x^{2}}{2}+C_{2}\\
\frac{y^{2}}{2}&=\frac{x^{2}}{2}+C_{3}\\
y^{2}&=x^{2}+2C_{3}\\
y&=±\sqrt{ x^{2}+C }
\end{align*}
$$
4) $\frac{dy}{dx}=\frac{y\cos(x)}{1-2y}$
$$
\begin{align*}
(1-2y)dy&=y\cos(x)\,dx\\
\frac{1-2y}{y}dy&=\cos(x)\,dx\\
\left( \frac{1}{y}-2 \right)dy&=\cos(x)\,dx\\
\int \frac{1}{y}-2 \, dy &=\int \cos(x) \, dx \\
\ln(y)-2y+C_{1}&=\sin(x)+C_{2}\\
\ln(y)-2y&=\sin(x)+C
\end{align*}
$$
Esta ecuación en especial, llega hasta aquí, debido a que sale de una derivación implícita de la función $y$.
Sin embargo, se puede resolver con un truco matemático, una función conocida como la W de Lambert, la cual cumple con la siguiente regla: $W(xe^{x})=x$, resolviéndose de la siguiente forma:
$$
\begin{align*}
e^{\ln(y)-2y}&=e^{\sin(x)+C}\\
ye^{-2y}&=e^{\sin(x)+C}\\
-2y\,e^{-2y}&=-2e^{\sin(x)+C}\\
W(-2y\,e^{-2y})&=W(-2e^{\sin(x)+C})\\
-2y&=W(-2e^{\sin(x)+C})\\
y&=-\frac{1}{2}W(-2e^{\sin(x)+C})\\
\end{align*}
$$

5) $\frac{dy}{dx}-e^{x+y}=0$
$$
\begin{align*}
\frac{dy}{dx}&=e^{x+y}\\
\frac{dy}{dx}&=e^{x}e^{y}\\
\frac{dy}{e^{y}}&=e^{x}dx\\
\int \frac{dy}{e^{y}} &=\int  e^{x} \, dx \\
\int e^{-y} \, dy &=\int e^{x} \, dx \\
-e^{-y}&=e^{x}-C_{1}\\
e^{-y}&=-e^{x}-C_{1}\\
-y&=\ln(-e^{x}-C_{1})\\
y&=-\ln(C-e^{x})
\end{align*}
$$

6) $(yx-y)dy-(y+1)dx=0$
$$
\begin{align*}
(x-1)y\,dy&=(y+1)dx\\
\frac{y}{y+1}dy&=\frac{dx}{x-1}\\
\frac{y+1-1}{y+1}dy&=\frac{dx}{x-1}\\
\left( 1-\frac{1}{y+1} \right)dy&=\frac{dx}{x-1}\\
\int 1-\frac{1}{y+1} \, dy &=\int \frac{1}{x-1} \, dx \\
y-\ln(y+1)&=\ln(x-1)+C\\
\ln(y+1)-y&=C-\ln(x-1)\\
e^{-y+\ln(y+1)}&=e^{C-\ln(x-1)}\\
(y+1)e^{-y+1-1}&=\frac{C}{x-1}\\
(y+1)e^{-y-1}e&=\frac{C}{x-1}\\
(y+1)e^{-(y+1)}e&=\frac{C}{x-1}\\
(y+1)e^{-(y+1)}&=\frac{C}{ex-e}\\
-(y+1)e^{-(y+1)}&=\frac{-C}{ex-e}\\
W(-(y+1)e^{-(y+1)})&=W\left( \frac{C}{ex-e} \right)\\
y+1&=-W\left( \frac{C}{ex-e} \right)\\
y&=-W\left( \frac{C}{ex-e} \right)-1
\end{align*}
$$
7) $(1+x^{2}+y^{2}+x^{2}y^{2})dy=(1+y^{2})dx$
$$
\begin{align*}
((1+y^{2})+x^{2}(1+y^{2}))dy&=(1+y^{2})dx\\
\cancelto{ 1 }{ (1+y^{2}) }(1+x^{2})dy&=\cancelto{ 1 }{ (1+y^{2}) }dx\\
(1+x^{2})dy&=dx\\
dy&=\frac{dx}{1+x^{2}}\\
\int  \, dy &=\int \frac{1}{1+x^{2}} \, dx \\
y&=\tan ^{-1}(x)+C
\end{align*}
$$
8) $1+e^{-3x}y'=0\qquad y(0)=1$
$$
\begin{align*}
1+e^{-3x} \frac{dy}{dx}&=0\\
e^{-3x} \frac{dy}{dx}&=-1\\
\frac{dy}{dx}&=-\frac{1}{e^{-3x}}\\
\frac{dy}{dx}&=-e^{3x}\\
dy&=-e^{3x}\,dx\\
\int  \, dy &=-\int e^{3x} \, dx \\
y&=-\frac{1}{3}e^{3x}+C\\
y(0)&=1\\
y(0)&=-\frac{1}{3}e^{3(0)}+C\\
1&=-\frac{1}{3}e^{0}+C\\
1&=-\frac{1}{3}+C\\
1+\frac{1}{3}&=C\\
C&=\frac{4}{3}\\
y&=\frac{4}{3}-\frac{1}{3}e^{3x}
\end{align*}
$$
  9) $\frac{dy}{dx}=x^{2}+x^{2}y^{2}$
$$
\begin{align*}
\frac{dy}{dx}&=x^{2}(1+y^{2})\\
\frac{dy}{1+y^{2}}&=x^{2}dx\\
\int \frac{1}{1+y^{2}} \, dy &=\int x^{2} \, dx \\
\tan ^{-1}(y)&=\frac{x^{3}}{3}+C\\
y&=\tan\left( \frac{x^{3}}{3}+C \right)
\end{align*}
$$
10) $\frac{dy}{dx}=x^{2}y^{2}-xy+x^{2}-2y^{2}+2y+xy^{2}-x^{2}y+x-2$
$$
\begin{align*}
\frac{dy}{dx}&=y^{2}(x-2)-y(x-2)+x^{2}(y^{2}-y+1)+(x-2)\\
\frac{dy}{dx}&=(x-2)(y^{2}-y+1)+x^{2}(y^{2}-y+1)\\
\frac{dy}{dx}&=(y^{2}-y+1)(x^{2}+x-2)\\
\frac{dy}{y^{2}-y+1}&=(x^{2}+x-2)dx\\
\frac{dy}{y^{2}-y+\frac{1}{2}^{2}-\frac{1}{4}+1}&=\left( x^{2}+x+\frac{1}{2}^{2}-\frac{1}{4}-2 \right)dx\\
\frac{dy}{\left( y-\frac{1}{2} \right)^{2}+\frac{3}{4}}&=\left( \left( x+\frac{1}{2} \right)^{2}-\frac{9}{4} \right)dx\\
\int \frac{dy}{\left( y-\frac{1}{2} \right)^{2}+\frac{3}{4}}&=\int \left( x+\frac{1}{2} \right)^{2}-\frac{9}{4} \, dx\\
\frac{2}{\sqrt{ 3 }}\tan ^{-1}\left( \frac{2y-1}{\sqrt{ 3 }} \right)&=\frac{\left( x+\frac{1}{2} \right)^{3}}{3}-\frac{9}{4}x+C\\
\tan ^{-1}\left( \frac{2y-1}{\sqrt{ 3 }} \right)&=\frac{\sqrt{ 3 }\left( x+\frac{1}{2} \right)^{3}}{6}-\frac{9\sqrt{ 3 }}{8}x+C\\
\frac{2y-1}{\sqrt{ 3 }}&=\tan\left( \frac{\sqrt{ 3 }\left( x+\frac{1}{2} \right)^{3}}{6}-\frac{9\sqrt{ 3 }}{8}x+C \right)\\
2y-1&=\sqrt{ 3 }\tan\left( \frac{\sqrt{ 3 }\left( x+\frac{1}{2} \right)^{3}}{6}-\frac{9\sqrt{ 3 }}{8}x+C \right)\\
y&=\frac{\sqrt{ 3 }}{2}\tan\left( \frac{\sqrt{ 3 }\left( x+\frac{1}{2} \right)^{3}}{6}-\frac{9\sqrt{ 3 }}{8}x+C \right)+\frac{1}{2}
\end{align*}
$$


## Demostrar que una ecuación diferencial se puede separar

En muchas ocasiones es posible que si queremos resolver una ecuación diferencial, lo primero que queramos intentar será resolverla mediante separación de variables, pero existen algunos problemas, que resulte muy difícil visualizar la factorización, es por esto mismo, que existe un algoritmo que permite saber si una ecuación se puede resolver mediante separación de variables.

Como primer paso, se debe expresar la ecuación en la forma $\frac{dy}{dx}=f(x,y)$, después se deben buscar números $x_{0},y_{0}$ que cumplan $f(x_{0},y_{0})\neq 0$, una vez obtenidos estos valores, podemos seguir con el siguiente paso.

Como segundo paso, debemos calcular con los valores $x_{0},y_{0}$ obtenidos en el paso anterior lo siguiente $f(x_{0},y)\cdot f(x,y_{0})$, una vez obtenida la expresión, pasamos al último paso.

Para finalizar, debemos de comprobar que $f(x_{0},y_{0})\cdot f(x,y)=f(x_{0},y)\cdot f(x,y_{0})$. Si al realizarlo, se cumple la igualdad, entonces la expresión calculada en el segundo paso, es la función factorizada, y se puede pasar a la separación de variables y posteriormente a la resolución de la ecuación diferencial.

#### Ejemplo

$$
\begin{align*}\\
\text{Obteniendo } f(x,y)\\

\frac{dy}{dx}&=x^{2}y^{2}+x^{2}+y^{2}+1\\
f(x,y)&=x^{2}y^{2}+x^{2}+y^{2}+1\\\\
\text{Buscando los valores que cumplan } \\
f(x_{0},y_{0})&\neq 0\\
f(0,0)&=1\\\\
\text{Calculando}\\

f(x_{0},y)\cdot f(x,y_{0})&=(y^{2}+1)(x^{2}+1)\\
\\
\text{Comprobando}\\

f(x_{0},y_{0})\cdot f(x,y)&=f(x,y_{0})\cdot f(x_{0},y_{0})\\
1\cdot f(x,y)&=(y^{2}+1)(x^{2}+1)\\
f(x,y)&=y^{2}x^{2}+y^{2}+x^{2}+1\\
\therefore\text{Es separable}
\end{align*}
$$
