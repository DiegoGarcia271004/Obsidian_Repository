---
tags:
  - Calculo3
  - Matematica
---
## Sucesiones

Una sucesión es una serie de datos dados por una sucesión general donde cumple la siguiente regla:
$$
\begin{align*}
\forall n\geq m&&&\forall n\in \mathbb{Z}
\end{align*}
$$
donde $m$ el primer término de la sucesión.
En otras palabras es una función que posee un dominio **discreto**.

Las sucesiones se expresan con la siguiente notación:
$$
\left\{ a_{n} \right\}_{n=1}^{\infty}=\{a_{1},\,a_{2},\,a_{3},\dots\}
$$

**Ejemplo**:
Encuentre la forma general de las siguientes sucesiones:

$$
\begin{align*}
1)\\
&\left\{ \frac{1}{2},\, \frac{2}{3},\, \frac{3}{4}, \, \frac{4}{5},\, \dots \right\} && \Rightarrow&& \left\{ \frac{n}{n+1} \right\}_{n=1}^{\infty}\\
\\
2)\\
&\left\{ \frac{3}{5},\, -\frac{4}{25},\, \frac{5}{125},\, -\frac{6}{625},\, .. \right\}&&\Rightarrow&&\left\{ \frac{(-1)^{n+1}\cdot n}{5^{n-2}} \right\}_{n=3}^{\infty}
\end{align*}
$$

## Sucesiones convergentes

Una sucesión se le considera convergente si y solo si el límite con tendencia infinita del termino general de la sucesión retorna un valor $L$:
$$
\left\{ a_{n} \right\}_{n=1}^{\infty} \, \text{es convergente} \iff \lim_{ n \to \infty } a_{n}=L
$$
**Ejemplo:**
Compruebe si la sucesión $\left\{ \frac{n}{n+1} \right\}_{n=1}^{\infty}$ converge:
$$
\lim_{ n \to \infty } \frac{n}{n+1}=1\,\, \therefore \text{converge.}
$$

## Criterios de evaluación de convergencia de sucesiones

#### Criterio del valor absoluto
En el caso de que se encuentre una sucesión alternante, es decir, que sus términos posean una (redundantemente) alternancia de signos entre términos, estas se pueden expresar de varias formas:
$$
\begin{align*}
&(-1)^{n}&&\cos(\pi\cdot n)&&\sec(\pi\cdot n) &&\sin\left( \left( \frac{2n+1}{2} \right) \pi \right) &&\csc\left(\left( \frac{2n+1}{2} \right)\pi\right)
\end{align*}
$$
En el dado caso que estas formas se encuentran en la forma general de la función, se le aplica un valor absoluto, al realizar esto, la forma de alternancia (vistas anteriormente) se remueve del término general y se aplica el criterio del límite, en el caso de que el límite de $0$, la sucesión converge. Sin embargo, si el límite da cualquier otro número, la serie diverge:
$$
\begin{align*}
&\lim_{ n \to \infty } |a_{n}|=0&&\text{converge a }0\\
&\lim_{ n \to \infty } |a_{n}|\neq 0&&\text{diverge}  
\end{align*}
$$
**Ejemplo**
Determine si la siguiente sucesión converge:
$$
\begin{align*}
\left\{ \frac{\cos(n\pi)}{n^{2}} \right\}_{n= 1}^{\infty} &&\Rightarrow &&\left\{\left| \frac{(-1)^{n}}{n^{2}} \right| \right\}_{n=1}^{\infty} && \Rightarrow && \lim_{ n \to \infty } \frac{1}{n^{2}}=0&&\therefore\text{Converge a } 0
\end{align*}
$$

#### Criterio de la razón o cociente
En el dado caso que se encuentre un término general que sea más complicada de resolver por los métodos usuales de resolución de límites (como pueden ser factoriales, potencias n-ésimas, etc.) en estos casos es que se aplica este método.
Para aplicarse, es necesario tomar el término general $a_{n}$ y se debe realizar un cociente de la siguiente manera: $\frac{a_{n+1}}{a_{n}}$, es decir, la forma general evaluada en $n+1$ dividido por el término general.
Como siguiente paso se debe evaluar el límite del cociente, y este regresara un valor $\rho$, es decir: $\lim_{ n \to \infty } \frac{a_{n+1}}{a_{n}}=\rho$, y dependiendo de el valor de $\rho$ se evaluaran las siguientes condiciones.
1. $\rho <1$ la sucesión converge a 0.
2. $\rho >1$ la sucesión diverge.
3. $\rho=1$ No se concluye. 

**Ejemplo:**
Determine la convergencia de la siguiente sucesión:
$$
\begin{align*}
&\left\{ \frac{2\cdot n!}{(2n)!} \right\}_{n=1}^{\infty}\\\\

& a_{n}=\frac{2\cdot n!}{(2n)!}&&\Rightarrow &&a_{n+1}=\frac{2\cdot(n+1)!}{(2n+2)!}\\\\
&\frac{a_{n+1}}{a_{n}} =\frac{2^{n+1}(n+1)!(2n!)}{(2n+2)!\cdot 2^{n}\cdot n!} && \Rightarrow && \frac{\cancel{2}\cdot \cancel{2^{n}}\cdot\cancel{(n+1)}\cdot\cancel{n!}\cdot \cancel{2n!}}{\cancel{2}\cancel{(n+1)}\cdot(2n+1)  \cancel{ (2n)! } \cancel{ 2^{n} }\cdot \cancel{ n! }} && \Rightarrow && \frac{1}{2n+1}\\
&\lim_{ n \to \infty }  \frac{1}{2n+1}=0\\
\\
&\therefore \text{Convege a 0}

\end{align*}
$$

## Acotamiento y monotonía en sucesiones infinitas

### Acotamiento

$\left\{ a_{n} \right\}_{n=1}^{\infty}$ es acotada si existe alguna constante "$M$" talque:
$$
a_{n} \leq M \,\, \forall n \in \mathbb{Z},\, n\geq m
$$
### Monotonía 

$\left\{ a_{n} \right\}_{n=m}^{\infty}$ se considera:

1. Creciente si $a_{n}<a_{n+1},\,\forall n\geq m$.
2. No decrece si $a_{n} \leq a_{n+1} ,\,\forall n\geq m$.
3. Decreciente si $a_{n}>a_{n+1},\,\forall n\geq m$.
4. No creciente si $a_{n}\geq a_{n+1},\,\forall n\geq m$.
5. Monótona si no crece o no decrece.
6. Estrictamente monótona si crece o decrece.

**Extras**
Si se tiene una sucesión $\left\{ a_{n} \right\}_{n=1}^{\infty}$ se tiene que el término general $a_{n}=f(n)\equiv f(x)$ si es continua y derivable $\forall x\geq m$, entonces:
1. $f'(x)\geq 0,\,\forall x\geq m \rightarrow f(x) \text{ crece en } [1, +\infty [$
2. $f'(x)\leq 0,\,\forall x\geq m \rightarrow f(x) \text{ decrece en } [1, +\infty]$


> [!important] Teorema
> Toda sucesión monótona y acotada es convergente

### Prueba de acotamiento y monotonía

#### Prueba de monotonía
Para poder encontrar si una sucesión es monótona, siendo que el término general no se pueda expresar como una función de $x$ diferenciable, es necesario utilizar el método de inducción matemática, lo que se busca demostrar es la desigualdad: $a_{n}\leq a_{n+1}$.

#### Prueba de acotamiento
Para encontrar si una sucesión posee un acotamiento, de igual forma que para la prueba de monotonía, se debe realizar una prueba por inducción matemática, sin embargo, en este caso lo que se busca demostrar es la desigualdad $a_{n}\leq M$ sea $M$ un valor aproximado al valor que converge la sucesión.

**Ejemplo:**
Demuestre que la sucesión $a_{n+1}=3-\frac{1}{a_{n}};\,a_{1}=1$ converge.

**Prueba de monotonía:**
$$
\begin{align*}
a_{n}&\leq a_{n+1}\\
&\text{Paso base n=1}\\
a_{1}=1;\,a_{2}&=3-\frac{1}{1}=2\\
a_{1}&\leq a_{2}\\
1&\leq 2\\
\\
\text{Hipótesis Inductiva: }& a_{k}\leq a_{k+1}\\
&\text{Paso inductivo:}\\
a_{k}\leq a_{k+1}&\Rightarrow \frac{1}{a_{k}}\geq \frac{1}{a_{k+1}}\\
-\frac{1}{a_{k}}\leq-\frac{1}{a_{k+1}}&\Rightarrow 3-\frac{1}{a_{k}}\leq 3-\frac{1}{a_{k+1}}\\
a_{k+1}&=3-\frac{1}{a_{k}}\\
a_{k+2}&=3-\frac{1}{a_{k+1}}\\
a_{k+1}&\leq a_{k+2}\\\\

&Q.E.D
\end{align*}
$$
**Prueba de acotamiento:**
$$
\begin{align*}
a_{n}&\leq M\\
M=3;&\text{ Paso base n=1}\\
a_{1}&\leq 3\\
1&\leq 3\\
\\
&\text{Hipótesis Inductiva: } a_{k}\leq 3\\
&\text{Paso Inductivo:}\\
a_{k}&\leq 3\\
\frac{1}{a_{k}}\geq \frac{1}{3}&\Rightarrow-\frac{1}{a_{k}}\leq-\frac{1}{3}\\
3-\frac{1}{a_{k}}&\leq 3-\frac{1}{3}\\
a_{k+1}&=3-\frac{1}{a_{k}}\\
a_{k+1}&\leq 3-\frac{1}{3}\Rightarrow a_{k+1}\leq \frac{8}{3}\\
\frac{8}{3}&\leq3\\
\\
&Q.E.D
\end{align*}
$$
Ya que encontramos que en la sucesión posee monotonía y acotamiento, por el teorema, se sabe que la serie converge, es decir que es necesario encontrar el valor de convergencia, ya que anteriormente confirmamos la convergencia se afirma que: $\lim_{ n \to \infty }a_{n}=L$ siendo $L$ el valor de convergencia.

**Aplicando límite infinito:**
Debido a que el límite de convergencia de $a_{n}$ es $L$, el límite de convergencia del termino siguiente ($a_{n+1}$) debe converger al mismo valor, es decir: $\lim_{ n \to \infty }a_{n+1}=L$.
$$
\begin{align*}
\lim_{ n \to \infty } a_{n+1}&=3-\frac{1}{a_{n}}\\
L&=3-\frac{1}{L}\\
L^{2}&=3L-1\\
L^{2}-3L+1&=0\\
L&=\frac{3+\sqrt{ 5 }}{2}\\
\\

\end{align*}
\therefore \text{El valor de convergencia de } a_{n} \text{ es } \frac{3+\sqrt{ 5 }}{2}
$$
