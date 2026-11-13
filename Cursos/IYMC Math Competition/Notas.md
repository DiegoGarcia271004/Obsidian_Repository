
# Datos importantes

Primeramente, definamos que es un número triangular. 
Un número triangular es un número positivo que cumple la forma:
$$
T_{k}=\frac{k(k+1)}{2} \qquad k=1,2,3,\dots
$$
Por lo que $T_{2}$ es definido como un conjunto de todas las sumas entre dos números triangulares positivos.
Es decir:
$$
T_{2}=\{T_{i}+T_{j}\,| \,i,j \geq 1\}
$$
$$
\begin{gather*}
T_{2}=\left\{ \frac{i(i+1)}{2}+\frac{j(j+1)}{2} |\,i,j\geq 1 \right\}\\
T_{2}=\left\{ \frac{1}{2}[i(i+1)+j(j+1)]\,|\,i,j_{6}\geq 1 \right\}
\end{gather*}
$$
(Solo para expandir, no es nada importante).

Se define que una función $f$ que tiene las siguientes propiedades:
1. $f$ es una función multiplicativa, es decir que $f(ab)=f(a)f(b)$
2. $f$ es una función aditiva dentro de $T_{2}$, es decir que para todo $a, b \in T_{2}$ se cumple que $f(a+b)=f(a)+f(b)$

Lo que se intenta demostrar, es que si existe algún valor $n\neq 1,3,5$ que cumpla $f(n)\neq 0$, entonces $f$ será la función identidad para todo $n$.

## Introducción

Se le llama multiplicativa a una función $f:\mathbb{N}\to \mathbb{C}$ **si** $f(1)=1$ y $f(mn)=f(m)f(n)$ para todos los números primos relativos $m$ y $n$.

En 1992 se mostró que si una función multiplicativa $f$ satisface la condición:
$$
f(p+q)=f(p)+f(q)
$$
para todos los primos $p,q$ y $f(p_{0})\neq 0$ entonces $f$ será si o si la función identidad. A esto se le llamo como **unicidades aditivas**.

Desde dicho descubrimiento, muchos matemáticos estudiaron las unicidades aditivas de distintos conjuntos. Por ejemplo se obtuvo el mismo resultado con la condición extendida de:
$$
f(p_{1}+p_{2}\pm\dots+p_{k})=f(p_{1})+f(p_{2})+\dots+f(p_{k})
$$
con $k\geq 3$.

También se descubrió que todas las funciones multiplicativas satisfacen:
$$
f(m^{2}+n^{2})=f(m^{2})+f(n^{2})
$$
Para todos $m,n\in\mathbb{N}$. Para este caso, la función $f$ no está determinada como unicidad. Luego se mostró que si la condición se cambia a:
$$
f(a_{1}^{2}+a_{2}^{2}+\dots+a_{k}^{2})=f(a_{1}^{2})+f(a_{2}^{2})+\dots+f(a_{k}^{2})
$$
con $k\geq 3$, entonces $f$ es la función identidad.

Sea $T$ el conjunto de los números triangulares positivos, que es:
$$
T=\left\{ \frac{n(n+1)}{2}\,|\,n=1,2,\dots \right\}=\left\{  1,3,6,10,15,21,28,36,45,\dots\right\}
$$
Unos matemáticos mostraron que $T$ es una **unicidad aditiva (UA)** para funciones multiplicativas.
Mostraron que el conjunto:
$$
P=\left\{ \frac{n(3n-1)}{2}\,|\,n\in\mathbb{Z},n\neq 0 \right\}=\left\{ 1,2,5,7,12,15,22,26,35,40,\dots \right\}
$$
de números pentagonales generalizados son una UA de conjuntos de funciones multiplicativas. A su vez, la condición para la UA de los conjuntos $T$ y $P$ pueden ser extendidas como fue hecho para el conjunto de primos y el conjunto de cuadrados.

El autor mostro que todas las funciones multiplicativas $f$ satisfacen la condición
$$
f(a^{2}+b^{2}+c^{2}+d^{2})= f(a^{2}+b^{2})+f(c^{2}+d^{2})
$$
para todos los enteros positivos $a,b,c$ y $d$.

Ahora, consideremos el problema de reemplazar los cuadrados con números triangulares en la condición inicial. Sea $T_{2}$ el conjunto de las sumas de dos elementos de $T$. Eso es:
$$
T_{2}=\left\{ 2,4,6,7,9,11,12,13,16,18,20,21,22,24,25,27,29,30,\dots \right\}
$$
Entonces se establece.


> [!NOTE] Teorema 1
> Si una función multiplicativa $f$ satisface la condición
> $$
> f(a+b)=f(a)+f(b)
> $$
> para todos los $a,b\in T_{2}$, entonces $f$ es uno de los siguientes:
> 1. $f(n)=n$, la función identidad,
> 2. $f(n)=0$ para todos los $n\neq 1,3,5$ y $f(3)f(5)=0$.


---

## ¿Qué es un número triangular?

Un número triangular es aquel que posee la forma:
$$
T_{n}=\frac{n(n+1)}{2}\qquad n\in\mathbb{N}
$$

