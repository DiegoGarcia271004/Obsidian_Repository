# Problema A

Encuentre todas las raíces reales de la función $g(x)=(x-1)\cdot(x+4)\cdot \ln(x)$

## Solución

Primeramente debemos de establecer el dominio de la función.
Los primeros dos factores de la función: $(x-1)\cdot(x+4)$ no afectan al dominio, por lo que sigue siendo $D=\mathbb{R}$.
El último factor ya nos restringe el domino, siendo que el dominio de la función $\ln (x)$ es $D: (0,\infty)$, haciendo que el dominio de la función completa sea:
$$
D: (0,\infty)
$$
Gracias a los primeros factores de la función, podemos decir que las raíces serían:
$$
x_{1}=1\qquad x_{2}=-4
$$
Sin embargo, debido a la restricción de dominio tenemos que descartar $x_{2}$ por lo que las raíces reales de $g(x)$ son:
$$
\boxed{x=1}
$$
---
# Problema B

Encuentre todos los enteros $n$ tal que esta ecuación sea cierta:
$$
2^{n} + 2^{-n}=\frac{5}{2}
$$
## Solución

$$
\begin{align*}
2^{n}+2^{-n}&=\frac{5}{2}\\
2^{n}+\frac{1}{2^{n}}&=\frac{5}{2}\\
\frac{2^{2n}+1}{2^{n}}&=\frac{5}{2}\\
2^{2n}+1&=\frac{5}{2} \cdot2^{n}\\
x&=2^{n}\\
x^{2}+1&=\frac{5}{2}x\\
x^{2}-\frac{5}{2}x+1&=0
\end{align*}
$$
$$
\begin{gather*}
x=\frac{\frac{5}{2}\pm \sqrt{ \frac{25}{4}-4 }}{2}\\
x=\frac{\frac{5}{2}\pm \frac{3}{2}}{2}
\end{gather*}
$$
%% col-start %%
%% col-break %%
$$
\begin{gather*}
x_{1}=\frac{\frac{5}{2}+\frac{3}{2}}{2}=\frac{\frac{8}{2}}{2}=\frac{8}{4}=2\\
2^{n}=2\\
n=1
\end{gather*}
$$
%% col-break %%
$$
\begin{gather*}
x_{2}=\frac{\frac{5}{2}-\frac{3}{2}}{2}=\frac{2}{4}=\frac{1}{2}\\
2^{n}=\frac{1}{2}\\
n=-1
\end{gather*}
$$
%% col-end %%
$$
\boxed{n=\{1,-1\}}
$$
---
# Problema C

Determina el valor numérico de las siguientes expresiones sin el uso de una calculadora:
$$
\frac{\log_{4}(64)-(-1)^{2026}}{2}+\sum_{k=1}^{4} \frac{\cos\left( \frac{\pi}{2}+k\pi \right)}{(-1)^{k+1}}+\sqrt{ \left( \frac{3}{\sqrt{ 3 }} \right)^{2} }-1
$$
## Solución

%% col-start:sb:0 %%
%% col-break:sb:0 %%
$$
\begin{gather*}
\frac{\log_{4}(64)-(-1)^{2026}}{2}\\
=\frac{3-(-1)^{2(1013)}}{2}\\
=\frac{3-1^{1013}}{2}\\
=\frac{3-1}{2}\\
=\frac{2}{2}\\
=1
\end{gather*}
$$
%% col-break %%
$$
\begin{gather*}
\cos\left( \frac{\pi}{2} \right)=0\\
\cos\left( \frac{\pi}{2}+\pi \right)=0\\
\cos\left( \frac{\pi}{2}+2\pi \right)=0\\
\vdots\\
\cos\left( \frac{\pi}{2} +k\pi\right)=0\\\\
\sum_{k=1}^{4} \frac{\cos\left( \frac{\pi}{2}+k\pi \right)}{(-1)^{k+1}}=0
\end{gather*}
$$
%% col-break %%
$$
\begin{gather*}
\sqrt{ \left( \frac{3}{\sqrt{ 3 }} \right)^{2} }\\
\frac{3}{\sqrt{ 3 }}\cdot  \frac{\sqrt{ 3 }}{\sqrt{ 3 }}\\
\frac{3\sqrt{ 3 }}{3}\\
\sqrt{ 3 }
\end{gather*}
$$
%% col-end %%
$$
\begin{gather*}
\frac{\log_{4}(64)-(-1)^{2026}}{2}+\sum_{k=1}^{4} \frac{\cos\left( \frac{\pi}{2}+k\pi \right)}{(-1)^{k+1}}+\sqrt{ \left( \frac{3}{\sqrt{ 3 }} \right)^{2} }-1\\
1+0+\sqrt{ 3 }-1\\
\boxed{\sqrt{ 3 }}
\end{gather*}
$$
---
# Problema D

Prueba que para todo entero positivo $n$,
$$
1+2026+2026^{2}+\dots+2026^{n-1}
$$
es divisible por $2027$ siempre que $n$ sea múltiplo de $2026$.

## Solución

### Re-expresión del enunciado

Debido a que se presenta una serie, se reescribe la operación como:
$$
\tag{1}
1+2026+2026^{2}+\dots+2026^{n-1}=\sum_{k=0}^{n-1} 2026^{k}
$$
Debido a que se define que $n$ siempre es un múltiplo de 2026, entonces se planteará que:
$$
\tag{2}
n=2026m \qquad \forall m\in\mathbb{Z}^{+}
$$

Al reescribir la expresión juntando $(1)$ y $(2)$ obtenemos:
$$
\tag{3}
\sum_{k=0}^{2026m-1} 2026^{k}
$$
Ya que $(3)$ es una suma geométrica, se puede obtener una expresión generalizada para su suma parcial:
$$
\tag{4}
\sum_{k=0}^{2026m-1} 2026^{k}=\frac{2026^{2026m}-1}{2026-1}=\frac{2026^{2026m}-1}{2025}
$$
Con esta expresión podemos plantear un nuevo enunciado:

> Prueba que para todo entero positivo $m$,$$
\frac{2026^{2026m}-1}{2025}
$$ es divisible por $2027$.

### Definiciones

Si $x$ es un entero positivo par, y $y$ es un entero positivo cualquiera, el producto $xy$ también es un número entero positivo par.

Si $x$ es el máximo común divisor de $a$ y $b$, entonces $x$ divide tanto a $a-b$ como a $b-a$.

El lema de Euclides establece si se tienen tres enteros $n, a$ y $b$, donde $n$ divide a $a\cdot b$ y $n$ es co-primo con $a$ (el máximo común divisor es 1), entonces $n$ divide a $b$.

### Modularidad base 2027 

Primeramente se buscará encontrar si la siguiente proposición es correcta:
$$
2026^{2026m}-1 \text{ es divisible por }2027
$$
Como $2026=2027−1$, se tiene que $2026≡−1\pmod{2027}$. Por lo tanto, para cualquier entero positivo $n$:  
$$2026^n \equiv (-1)^n \pmod{2027}$$  
 Y como $(-1)^n = 1$ si $n$ es par, y $(-1)^n=-1$  si $n$ es impar, se obtiene:  
$$2026^n \bmod 2027 = \begin{cases} 1, & n \text{ par} \\ 2026, & n \text{ impar}\end{cases}$$
Es decir que si $n$ es par, siempre estará a una unidad de ser un múltiplo exacto de 2027.
De igual manera, debido a que definimos la re-expresión de $n$ en $(2)$, y que $2026$ es un número par, por la definición planteada, $n$ siempre será un exponente par, por lo que su modulo con $2027$ siempre será igual a $1$.
Pero como se ha visto en la expresión, esta contiene un $-1$ lo que hace que la expresión completa de $(2026^{2026m}-1)\text{mod}(2027)=0$, es decir que siempre será divisible por $2027$.

### Máximo común divisor

Definimos $d$ como el máximo común divisor de $2025$ y $2027$:
$$
d=\text{gcd}(2025,2027)
$$
Por definición sabemos que $d$ debe poder dividir a la diferencia entre $2025$ y $2027$ es decir $2$. Por lo que $d$ solo puede tomar $2$ valores:
$$
d=\{ 1,2 \}
$$
Debido a que ninguno de los dos números son pares, es posible descartar la opción del número $2$, por lo que quedamos con:
$$
d=\text{gcd}(2025,2027)=1
$$
Por lo que el máximo común divisor entre $2025$ y $2027$ es $1$.

### Lema de Euclides

De las secciones anteriores obtuvimos que $2027\,|\,(2026^{2026m}-1)$. Por otro lado, de $(4)$ sabemos que $2026^{2026m}-1=2025\cdot \left( \frac{2026^{2026m}-1}{2025} \right)$, donde el cociente es un entero (por ser la suma geométrica original). Por lo tanto:
$$2027 \text{ divide a } (2025)\left(\frac{2026^{2026m}-1}{2025}\right)$$

Y como $\text{gdc}(2025,2027)=1$ (demostrado en la sección anterior), por el Lema de Euclides se concluye que 
$$
2027 \text{ divide a }\left(\frac{2026^{2026m}-1}{2025}\right)
$$
Pero por $(4)$, ese cociente es exactamente
$$
\sum_{k=0}^{n-1} 2026^{k}=1+2026+2026^{2}+\dots+2026^{n-1}
$$
por lo tanto:
$$\boxed{2027 \text{ divide a } \left(1+2026+2026^2+\dots+2026^{n-1}\right)} \qquad Q.E.D.$$
---

# Problema E

Un triángulo recto tiene catetos de longitudes $a$ y $b$. Un círculo está inscrito dentro del triángulo. Encuentra el área de la región en el interior del triángulo pero en el exterior del círculo.

![[Pasted image 20260727171700.png|center|300]]

## Solución

Primeramente se define que el círculo tiene un radio $r$ por ende, el área (sin saber la longitud de $r$) será:
$$
A=\frac{ab}{2}-\pi r^{2}
$$
Pero no conocemos $r$, por lo que debemos de encontrar $r$ en función de $a$ y $b$.

Sea $O$ el vértice del ángulo recto, $P$ el vértice del opuesto al cateto $a$ (extremo del cateto $b$), y $Q$ el vértice opuesto al cateto $b$ (extremo del cateto $a$).
Se encuentran los puntos en los que la circunferencia intercepta tangencialmente cada uno de los lados del triángulo.

Desde el punto $O$ hasta el punto de intercepto del cateto $a$ existe una longitud $r$, por lo que el resto del cateto tendrá una longitud de $a-r$. De igual forma, desde el punto $O$ hasta el punto de intercepto del cateto $b$ existe una longitud $r$ haciendo que el resto del cateto tenga una longitud $b-r$.

Desde el punto $P$ hasta el punto de intercepto de la hipotenusa tiene la misma longitud que la del lado formado por el punto $P$ y el punto de intercepto del cateto $b$ por lo que la longitud también es de $b-r$.

Desde el punto $Q$ hasta el punto de intercepto de la hipotenusa tiene la misma longitud que la del lado formado por el punto $Q$ y el punto de intercepto del cateto $a$ por lo que la longitud también es de $a-r$.

Por lo que la suma de las longitudes de $b-r$ y $a-r$ será de igual longitud que la hipotenusa, por lo que se puede afirmar que:
$$
(b-r)+(a-r)=\sqrt{ a^{2}+b^{2} }
$$

![[Triangle|center|500]]

Resolviendo:

%% col-start %%
%% col-break:41 %%
$$
\begin{gather*}
(b-r)+(a-r)=\sqrt{ a^{2}+b^{2} }\\
b+a-2r=\sqrt{ a^{2}+b^{2} }\\
c=\sqrt{ a^{2}+b^{2} }\\
b+a-2r=c\\
\frac{b+a-c}{2}=r
\end{gather*}
$$
%% col-break:59 %%
$$
\begin{gather*}
\frac{ab}{2}-\pi\left( \frac{b+a-c}{2} \right)^{2}\\
u=a+b\\
\frac{ab}{2}-\frac{\pi}{4}(u-c)^{2}\\
\frac{ab}{2}-\frac{\pi}{4}(u^{2}-2uc+c^{2})\\
\frac{ab}{2}-\frac{\pi}{4}((a+b)^{2}-2(a+b)c+c^{2})\\
\frac{ab}{2}-\frac{\pi}{4}(\cancelto{ c^{2} }{ a^{2}+b^{2} }+2ab-2ac-2bc+c^{2})\\
\frac{ab}{2}-\frac{\pi}{4}(c^{2}+2ab-2ac-2bc+c^{2})\\
\frac{ab}{2}-\frac{\pi}{4}(2c^{2}+2ab-2ac-2bc)\\
\frac{ab}{2}-\frac{\pi}{2}(c^{2}+ab-ac-bc)\\
\frac{ab-\pi(c^{2}+ab-ac-bc)}{2}
\end{gather*}
$$
%% col-end %%
Entonces el área de la zona sombreada es igual a:
$$
\boxed{\frac{ab-\pi(c^{2}+ab-ac-bc)}{2}}
$$
