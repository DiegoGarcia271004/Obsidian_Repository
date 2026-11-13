
# Problema A

Una secuencia se define por $a_{1}=1$ y $a_{n+1}=a_{n}+n+1$. Encuentra una ecuación de forma cerrada para calcular el valor de $a_{n}$ y determina $a_{100}$.

## Solución

### Re-expresión de la recurrencia

Primeramente, para este problema (con el fin de simplificar el ejercicio y obtener herramientas a utilizar más adelante) reescribiremos la recurrencia de la siguiente forma:
$$
\begin{gather*}
a_{n+1}=a_{n}+n+1\quad a_{1}=1\\
a_{n}=a_{n-1}+n \tag{1}
\end{gather*}
$$
De esta forma, se nos hará más sencillo el trabajar con ella más adelante.
A su vez, buscaremos encontrar otra herramienta con la recurrencia, la cual será el $a_{0}$:
$$
n=0;\quad a_{1}=a_{0}+1 \implies \boxed{a_{0}=0}
$$
Para la resolución de esta recurrencia utilizaremos el método de resolución con ecuaciones generatrices, por lo que asumiremos que el resultado es un termino general de una serie de potencias, entonces iniciaremos definiendo nuestra función $A(x)$.
$$
A(x)=\sum_{n=0}^{\infty}a_{n}x^{n}\tag{2}
$$

Procederemos tomando nuestra recurrencia, multiplicando cada término por $x^{n}$ y sumando para $n\geq 1$:
$$
\sum_{n=1}^{\infty} a_{n}x^{n}=\sum_{n=1}^{\infty} a_{n-1}x^{n}+\sum_{n=0}^{\infty} nx^{n}\tag{3}
$$

A continuación procederemos a transformar las expresiones de los sumatorios en formas más sencillas de resolver.

### Transformación de la primera expresión

Primeramente trabajaremos con $\sum_{n=1}^{\infty}a_{n}x^{n}$. Esta expresión no es muy distinta de $(2)$, solamente desde donde comienza, para expresarla en términos de $A(x)$, podemos seguir el siguiente proceso:
$$
A(x)=\sum_{n=1}^{\infty}a_{n}x^{n}-a_{0}\implies\boxed{ A(x)+a_{0}=\sum_{n=1}^{\infty} a_{n}x^{n}}\tag{4}
$$

### Transformación de la segunda expresión

De igual forma para $\sum_{n=1}^{\infty}a_{n-1}x^{n}$, cambiaremos el valor de inicio del sumatorio, lo que alterará la expresión en su interior; Finalmente, para compensar multiplicaremos todo por $x$ para obtener la forma de $A(x)$.
$$
\sum_{n=1}^{\infty}a_{n-1}x^{n}=\sum_{n=0}^{\infty}a_{n}x^{n+1}=x\sum_{n=0}^{\infty}a_{n}x^{n} \implies \boxed{xA(x)=\sum_{n=1}^{\infty}a_{n-1}x^{n}}\tag{5}
$$

### Transformación de la tercera expresión

Para $\sum_{n=1}^{\infty}nx^{n}$ tendremos que recurrir a otros métodos (debido a que es un término sin recurrencia), en este caso partiremos de la serie de potencias de $\frac{1}{1-x}$, es decir:
$$
\sum_{n=0}^{\infty}x^{n}=\frac{1}{1-x};\qquad |x|<1\tag{6}
$$
Partiendo de $(6)$, diferenciaremos con respecto a $x$ en ambos lados, y tras la diferenciación, multiplicamos por $x$ para encontrar una expresión:
$$
\begin{gather*}
\frac{d}{dx}\sum_{n=0}^{\infty}x^{n}=\frac{d}{dx} \frac{1}{1-x}\\
\sum_{n=1}^{\infty}nx^{n-1}=\frac{1}{(1-x)^{2}}\tag{7}\\
\boxed{\sum_{n=1}^{\infty}nx^{n}=\frac{x}{(1-x)^{2}}}\tag{8}
\end{gather*}
$$

### Integración de expresiones

Ya con las expresiones transformadas, procedemos a sustituir $(4),\,(5)$ y $(8)$ en $(3)$:
$$
\begin{gather*}
A(x)-a_{0}= xA(x)+\frac{x}{(1-x)^{2}}\\
A(x)-xA(x)=\frac{x}{(1-x)^{2}}\\
(1-x)A(x)=\frac{x}{(1-x)^{2}}\\
A(x)=\frac{x}{(1-x)^{3}}\tag{9}
\end{gather*}
$$
### Resolución de la expresión final

Ya que tenemos una expresión para $A(x)$ debemos encontrar una forma que se asemeje a la serie de potencias en $(2)$ para encontrar el término general $a_{n}$.
Para esto partiremos de $(7)$ y la diferenciaremos con respecto a $x$ y procederemos a transformarla.
$$
\begin{gather*}
\sum_{n=1}^{\infty}nx^{n-1}=\frac{1}{(1-x)^{2}}\\
\frac{d}{dx}\sum_{n=1}^{\infty}nx^{n-1}=\frac{d}{dx} \frac{1}{(1-x)^{2}}\\
\sum_{n=2}^{\infty}n(n-1)x^{n-2}=\frac{2}{(1-x)^{3}}\\
\sum_{n=0}^{\infty} \frac{(n+2)(n+1)}{2}x^{n}=\frac{1}{(1-x)^{3}}\\
\sum_{n=0}^{\infty} \frac{(n+2)(n+1)}{2}x^{n+1}=\frac{x}{(1-x)^{3}}\\
m=n+1\\
\sum_{n=0}^{\infty} \frac{(m+1)(m)}{2}x^{m}=\frac{x}{(1-x)^{3}}\tag{10}
\end{gather*}
$$
Podemos hacer la igualación de $(9)$ con $(10)$:
$$
\begin{gather}
A(x)=\sum_{m=1}^{\infty} \frac{(m+1)m}{2}x^{m}\\
A(x)=\sum_{n=0}^{\infty}a_{n}x^{n}=\sum_{m=1}^{\infty}a_{m}x^{m}\\
\sum_{m=1}^{\infty}a_{m}x^{m}=\sum_{m=1}^{\infty} \frac{(m+1)m}{2}x^{m}\\
a_{m}=\frac{(m+1)m}{2}\\
m=n+1\\
a_{n+1}=\frac{(n+2)(n+1)}{2}\\
a_{n}=\frac{n(n+1)}{2}
\end{gather}
$$
Por lo que:
$$
\therefore a_{n}=\frac{n(n+1)}{2} \tag{11}
$$

### Cálculo de $a_{100}$

Ya con el término general encontrado, podemos sustituir en $n$ el valor que nos interesa y calcular $a_{100}$:
$$
\begin{align*}
a_{n}&=\frac{n(n+1)}{2}\\
a_{100}&=\frac{100(100+1)}{2}\\
&=\frac{10100}{2}\\
&=5050
\end{align*}
$$
En conclusión:
$$
\boxed{a_{100}=5050}
$$

---
# Problema B

Demuestra que no existe $x\in\mathbb{R}$ que resuelva la ecuación $\sqrt{ 3+x }+\sqrt{ 7-x }=5.$

## Solución

$$
\begin{align*}
\sqrt{ 3+x }+\sqrt{ 7-x }&=5\\
\sqrt{ 3+x }&=5-\sqrt{ 7-x }\\
(\sqrt{ 3+x })^{2}&=(5-\sqrt{ 7-x })^{2}\\
3+x&=25-10\sqrt{ 7-x }+7-x\\
10\sqrt{ 7-x }&=29-2x\\
(10\sqrt{ 7-x })^{2}&=(29-2x)^{2}\\
100(7-x)&=841-116x+4x^{2}\\
700-100x&=841-116x+4x^{2}\\
0&=141-16x+4x^{2}
\end{align*}
$$
Utilizando el discriminante:
$$
\begin{align*}
\Delta&=\sqrt{ b^{2}-4ac }\\
&=\sqrt{ 16^{2}-4\cdot4\cdot 141 }\\
&=\sqrt{ 256-2256 }\\
&=\sqrt{ -2000 }\\
\\
\Delta &\not\in\mathbb{R}\qquad Q.E.D
\end{align*}
$$
En conclusión, ya que el discriminante no se encuentra en los reales, no existe un valor de $x$ que pertenezca a los reales que resuelva la ecuación.

---
# Problema C

Determina el valor numérico de la siguiente expresión sin el uso de una calculadora:
$$
\sum_{k=1}^{3} \frac{\sin\left( \frac{k\pi}{12} \right)+\sin\left( \frac{(6-k)\pi}{12} \right)}{\cos\left( \frac{k\pi}{12} \right)+\cos\left( \frac{(6-k)\pi}{12} \right)}-\prod_{m=1}^{2} \frac{\tan\left( \frac{\pi}{4}+\frac{m\pi}{12} \right)-\tan(\frac{\pi}{4}-\frac{m\pi}{12})}{1+\tan\left( \frac{\pi}{4}+\frac{m\pi}{12} \right)\tan\left( \frac{\pi}{4}-\frac{m\pi}{12} \right)}
$$
## Resolución del sumatorio

Para la resolución del sumatorio, deberemos de utilizar las propiedades de la suma, tanto del seno como del coseno, es decir que usaremos:
$$
\begin{gather*}
\sin \alpha+\sin \beta=2\sin \frac{\alpha+\beta}{2}\cdot \cos \frac{\alpha-\beta}{2}\\
\cos \alpha+\cos \beta=2\cos \frac{\alpha+\beta}{2}\cdot \cos \frac{\alpha-\beta}{2}
\end{gather*}
$$
Y por lo que se puede observar en las propiedades, es necesario encontrar tanto $\frac{\alpha+\beta}{2}$ como $\frac{\alpha-\beta}{2}$, por lo que las encontraremos en este momento:

Para este caso $\alpha =\frac{k\pi}{12}$ y $\beta=\frac{(6-k)\pi}{12}$
$$
\begin{align*}
\frac{\alpha+\beta}{2}&=\frac{1}{2} \left[ \frac{k\pi}{12}+\frac{6\pi-k\pi}{12} \right]\\
&=\frac{1}{2} \left[ \cancel{\frac{k\pi}{12}}+\frac{6\pi}{12}\cancel{-\frac{k\pi}{12}} \right]\\
&=\frac{1}{2}\left[ \frac{\pi}{2} \right]\\
&=\frac{\pi}{4}\\
\\
\frac{\alpha-\beta}{2}&=\frac{1}{2} \left[ \frac{k\pi}{12}-\frac{6\pi-k\pi}{12} \right]\\
&=\frac{1}{2} \left[ \frac{k\pi}{12}-\frac{\pi}{2}+\frac{k\pi}{12} \right]\\
&=\frac{1}{2} \left[ \frac{k\pi}{6}-\frac{\pi}{2} \right]\\
&=\frac{\pi}{4}\left( \frac{k}{3}-1 \right)
\end{align*}
$$
Ya obtenidas las combinaciones, podemos proceder a aplicar las propiedades:
$$
\begin{align*}
\sin\left( \frac{k\pi}{12} \right)+\sin\left( \frac{(6-k)\pi}{12} \right)&=2\cancelto{ \frac{\sqrt{ 2 }}{2} }{ \sin\left( \frac{\pi}{4} \right) } \cdot \cos\left( \frac{\pi}{4}\left( \frac{k}{3}-1 \right) \right)\\
&=\frac{2\sqrt{ 2 }}{2}\cos\left( \frac{\pi}{4}\left( \frac{k}{3}-1 \right) \right)\\
&=\sqrt{ 2 }\cos\left( \frac{\pi}{4}\left( \frac{k}{3}-1 \right) \right)
\end{align*}
$$
$$
\begin{align*}
\cos\left( \frac{k\pi}{12} \right)+\cos\left( \frac{(6-k)\pi}{12} \right)&=2\cancelto{ \frac{\sqrt{ 2 }}{2} }{ \cos\left( \frac{\pi}{4} \right) }\cdot \cos\left( \frac{\pi}{4}\left( \frac{k}{3}-1 \right) \right)\\
&=\frac{2\sqrt{ 2 }}{2}\cos\left( \frac{\pi}{4}\left( \frac{k}{3}-1 \right) \right)\\
&=\sqrt{ 2 }\cos\left( \frac{\pi}{4}\left( \frac{k}{3}-1 \right) \right)
\end{align*}
$$
Agregando las expresiones obtenidas al sumatorio:
$$
\sum_{k=1}^{3} \cancelto{ 1 }{ \frac{\sqrt{ 2 }\cos\left( \frac{\pi}{4}\left( \frac{k}{3}-1 \right) \right)}{\sqrt{ 2 }\cos\left( \frac{\pi}{4}\left( \frac{k}{3}-1 \right) \right)} }=\sum_{k=1}^{3}1=\boxed{3}
$$

### Resolución del producto

En el caso del producto, es posible visualizar que en su interior se cumple una de las propiedades de la tangente, la cuál es la siguiente:
$$
\tan (\alpha-\beta)=\frac{\tan (\alpha)-\tan (\beta)}{1+\tan(\alpha)\tan(\beta)}
$$
Donde $\alpha=\frac{\pi}{4}+\frac{m\pi}{12}$ y $\beta=\frac{\pi}{4}-\frac{m\pi}{12}$.

Por lo que calculamos $\alpha-\beta$:
$$
\begin{align*}
\alpha-\beta&=\cancel{\frac{\pi}{4}}+\frac{m\pi}{12}\cancel{-\frac{\pi}{4}}+\frac{m\pi}{12}\\
&=\frac{m\pi}{6}
\end{align*}
$$
Resolviendo el producto:
$$
\prod_{m=1}^{2}\tan\left( \frac{m\pi}{6} \right)=\tan\left( \frac{\pi}{6} \right)\cdot \tan\left( \frac{\pi}{3} \right)=\sqrt{ 3 } \frac{\sqrt{ 3 }}{3}=\boxed{1}
$$

### Resultado

Ya con el resultado tanto del sumatorio como del producto, solamente nos queda realizar la operación final:
$$
\sum_{k=1}^{3} \frac{\sin\left( \frac{k\pi}{12} \right)+\sin\left( \frac{(6-k)\pi}{12} \right)}{\cos\left( \frac{k\pi}{12} \right)+\cos\left( \frac{(6-k)\pi}{12} \right)}-\prod_{m=1}^{2} \frac{\tan\left( \frac{\pi}{4}+\frac{m\pi}{12} \right)-\tan(\frac{\pi}{4}-\frac{m\pi}{12})}{1+\tan\left( \frac{\pi}{4}+\frac{m\pi}{12} \right)\tan\left( \frac{\pi}{4}-\frac{m\pi}{12} \right)}=3-1=\boxed{2}
$$

---

# Problema D

Prueba que para cada entero positivo $n$, el número $n^{4}+4$ es un número compuesto, excepto para un valor de $n$.

Para poder iniciar con la demostración, debemos de observar que $n^{4}+4$ es posible expresarse de la siguiente manera:
$$
n^{4}+4=(n^{2}+2)^{2}-(2n)^{2}\tag{12}
$$
En $(12)$ podemos visualizar que se cumple en este caso una diferencia de cuadrados, por lo que procederemos a aplicarla:
$$
n^{4}+4=(n^{2}+2+2n)(n^{2}+2-2n)\tag{13}
$$
De esta forma obtenemos dos términos.
Si de los términos que conforman la factorización en $(13)$ logramos demostrar que para cierto valor de $n$ son mayores que $1$, entonces podremos decir con seguridad que el resultado será siempre un número compuesto.

### Demostrando para el primer término

Para resolver la desigualdad, haremos uso de complementación de cuadrados:
$$
\begin{gather*}
n^{2}+2n+2\geq 2\\
n^{2}+2n+1+1\geq 2\\
(n+1)^{2}+1\geq 2\\
(n+1)^{2}\geq 1\\
n+1\geq 1\\
n\geq 0
\end{gather*}
$$
Es decir que para el primer término, siempre que $n$ sea mayor o igual a 0, será mayor que 2.

### Demostrando para el segundo término

De igual forma que para el primer término, utilizaremos complementación de cuadrados:
$$
\begin{gather*}
n^{2}-2n+2\geq 2\\
n^{2}-2n+1+1\geq 2\\
(n-1)^{2}+1\geq 2\\
(n-1)^{2}\geq 1\\
n-1\geq 1\\
n\geq 2
\end{gather*}
$$
Esto nos indica que para el segundo término, si $n$ es mayor o igual que $2$, entonces el término será mayor a $2$.

### Conclusiones

Con todo lo obtenido anteriormente, es posible concluir que para cada valor de $n\geq 2$, $n^{4}+4$ dará un valor compuesto.
Para el caso en específico que $n=1$ se da que es el único número primo que resulta de evaluar en $n^{4}+4$, siendo que al evaluarlo, el resultado será $5$, siendo el único primo que sale de la expresión.


---

# Problema E

Un rectángulo con lados de longitud $a$ y $b$ se corta por una diagonal como se muestra en el dibujo de abajo. Encuentra el perímetro y el área de los dos triángulos formados.

![[Pasted image 20251007114426.png|center]]

## Solución

### Encontrando área

Para encontrar el área de los triángulos, debemos de observar que son triángulos rectángulos de base $b$ y de altura $a$, entonces su área se obtendría utilizando la fórmula del área de un triángulo:
$$
A=\frac{b\cdot h}{2}
$$
Donde $b$ es la base, y $h$ la altura. 
Ya con esto en mente, es posible encontrar una expresión para el área del triángulo formado:
$$
\boxed{A=\frac{ab}{2}}
$$

### Encontrando el perímetro

Para encontrar el perímetro, debemos de sumar la longitud de todos los lados del triángulo, en este caso ya conocemos dos, $a$ y $b$. Por lo que solamente nos queda obtener la longitud de la hipotenusa, que para el caso utilizaremos el teorema de Pitágoras:
$$
a^{2}+b^{2}=c^{2}
$$
Siendo $c$ la longitud de la hipotenusa. Por lo que solo procedemos a despejar $c$ y obtendríamos el valor:
$$
\sqrt{ a^{2}+b^{2} }=c
$$
Ya obteniendo el valor de la hipotenusa, solo debemos encontrar el valor total del perímetro, sumando todos los lados:
$$
\boxed{\text{Perímetro}=a+b+\sqrt{ a^{2}+b^{2} }}
$$
