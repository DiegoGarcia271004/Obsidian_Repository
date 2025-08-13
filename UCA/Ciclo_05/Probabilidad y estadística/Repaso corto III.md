---
tags:
  - ProbabilidadYEstadística
---
Si se nos da una población con $N$ individuos, de la cual obtenemos una muestra de $n$ individuos. Pero nosotros sabemos que existen muchas formas de obtener $n$ individuos a partir de la población original, a esta cantidad de formas de obtenerlo lo llamaremos $r$ y se definirá por los conceptos estudiados de conteo:
$$
r=\left( \begin{matrix} N \\
n \end{matrix} \right)
$$
Ahora, si obtenemos todas las muestras posibles y obtenemos la media de cada una de estas $r$ muestras, podemos encontrar un conjunto que llamaremos $X_{\bar{x}}$ definido como $\left\{ \bar{x}_{1},\bar{x}_{2},\bar{x}_{3},\dots,\bar{x}_{r} \right\}$.
El problema radica es que realmente ninguna de estas medias podría representar el verdadero valor de la media $\mu$ de la población. Sin embargo, si obtenemos la media de este nuevo conjunto $\mu_{\bar{x}}$, está tiene la propiedad que:
$$
\mu=\mu_{\bar{x}}
$$
Con la varianza sucede algo distinto, la varianza del nuevo conjunto $\sigma_{\bar{x}}$ tiene una igualdad algo distinta:
$$
\sigma_{\bar{x}}^{2}=\frac{\sigma^{2}}{n}
$$
La varianza del conjunto de medias es igual a la varianza de la población entre la cantidad de la muestra, **si y solo si la muestra es *infinita***. De ser finita se tiene que utilizar otra expresión:
$$
\sigma _{\bar{x}}^{2}=\frac{\sigma^{2}}{n} \frac{N-n}{N-1}
$$
También podemos definir la variable estándar de la media (cota z para los amigos), debido a que 
definimos que la varianza del conjunto de medias es $\sigma^{2}/n$, entonces la cota z del conjunto de medias es:
$$
Z_{\bar{x}}=\frac{\bar{x}-\mu }{\frac{\sigma}{\sqrt{ n }}}
$$
## Teorema del límite central

Si $\bar{x}$ es la media de una muestra aleatoria tomada de cualquier población con media $\mu$ y varianza $\sigma^{2}$ finitas, entonces la variable de la media $Z_{\bar{x}}$ se distribuye aproximadamente normal si el tamaño de la muestra es suficientemente grande.

**Ejemplo:**
En un curso de economía hay 250 estudiantes. Cada uno de los integrantes de una muestra aleatoria de 50 estudiantes es interrogado con el fin de estimar la cantidad de tiempo que gasta semanalmente en resolver los problemas de Estadística. Supongamos que la desviación típica de la población es de treinta minutos. 
1. ¿Cuál es la probabilidad de que la media muestral exceda   a la media poblacional en más de 2.5 minutos? 
2. ¿Cuál es la probabilidad de que la media muestral esté más de cinco minutos por debajo de la media poblacional? 
3. ¿Cuál es la probabilidad de que la media muestral difiera de la media poblacional en más de diez minutos?

---

# Distribución de muestreo de la población

El parámetro $P=X/N$ donde $X$ es el número de elementos de una población $N$ con una determinada característica es llamado proporción poblacional. De igual forma que en el apartado anterior, si tomamos todas las posibles muestras de $n$ individuos en una población $N$, obtendríamos $r=\left( \begin{matrix} n \\ N \end{matrix} \right)$ posibles muestras posibles.
De igual forma que con las medias, definimos un conjunto $\hat{p}$ con las proporciones poblacionales de todas las muestras posibles. Este conjunto al ser distribuido se llega a la **distribución de muestreo de la población**.
Esta distribución al igual que la distribución de la media de la muestra, posee ciertas propiedades similares:

- La media de la distribución de muestreo de la población es igual a la proporción poblacional $P$ de la muestra:
$$
\mu_{\hat{p}}=P
$$
- La varianza de las proporciones muestrales cumple:
$$
\begin{gather}
\hat{\sigma}^{2}_{\hat{p}}=\frac{pq}{n} \text{ en una población infinita}\\
\hat{\sigma}^{2}_{\hat{p}}=\frac{pq}{n} \frac{N-n}{N-1} \text{ en una población finita}
\end{gather}
$$
	La raíz cuadrada de la varianza es conocida como el error estándar de la proporción.

- La distribución de muestre $P$ sigue una ley normal de probabilidad $N\left( q, \frac{pq}{n} \right)$, para muestras grandes. La estandarización de la proporción se define como: 
$$
Z=\frac{\hat{p}-p}{\sqrt{ \frac{pq}{n} }}
$$
	y es normal estándar $N(0,1)$.

---

# Estimación de parámetros

Estimar un parámetro consiste en calcular un valor aproximado utilizando los datos desde una muestra extraída de la población de interés. La estimación se aborda en dos formas:

- **Estimación puntual o punto a punto**: Se calcula un único valor con los datos de una muestra. Ya habíamos señalado algunos ejemplos:
	- $\bar{x}$ de la muestra es un estimador puntual de $\mu$, la media de la población.
	- $S$, la desviación estándar de la muestra, es un estimador puntual de $\sigma$.
	- La proporción $\hat{p}$, de la muestra, es un estimador puntual de $P$, la proporción poblacional.
- **Estimación por intervalo**: Se calculan dos valores con los datos de la muestra, y se espera que entre esos valores, y con determinada probabilidad, se encuentre el verdadero valor del parámetro. Para los límites reales $a$ y $b$ se tiene el intervalo entre los límites $|a,b|$ por ejemplo:
$$
L_{1}\leq \mu\leq L_{2}: \text{ Se esperaría que la media poblacional se encuentre entre estos límites.}
$$


## Intervalos de confianza

