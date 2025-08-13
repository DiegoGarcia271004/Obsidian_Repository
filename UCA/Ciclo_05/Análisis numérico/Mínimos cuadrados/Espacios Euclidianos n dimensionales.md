---
tags:
  - ANumérico
---
# Norma euclidiana de un vector en $\mathbb{R}^{n}$

La norma de un vector, desde el punto de vista que hemos estudiado durante todo este tiempo sería considerado la longitud de dicho vector, y se calcula de la siguiente manera:

Sea $\bar{X}$ un vector en $\mathbb{R}^{2}$. Y $x$ y $y$ sus componentes rectangulares, la norma del vector $\bar{X}$ se define como:
$$
\|\bar{X}\|=\sqrt{ x^{2}+y^{2} }
$$

Pero si buscamos expandirnos a más dimensiones, podemos generalizar el cálculo de su norma:

Sea $\underline{X}$ un vector que pertenece a $\mathbb{R}^{n}$, su norma euclidiana se define como.
$$
\|\underline{X}\|=\sqrt{ x_{1}^{2}+x_{2}^{2}+x_{3}^{2}+\dots+x_{n}^{2} }
$$
O también como:
$$
\|\underline{X}\|=\sqrt{ \sum_{k=1}^{n}x_{i}^{2} }
$$
---

# Propiedades de la norma euclidiana en $\mathbb{R}^{n}$

La norma de los vectores tienen distintas propiedades en los espacios euclidianos n-dimensionales, entre las cuales podemos encontrar:

1.  La norma del vector siempre será mayor o igual a 0 en cualquier dimensión
$$
\|\underline{X}\|\geq 0\quad \forall \underline{X}\in \mathbb{R}^{n}
$$
2. La única forma en que la norma de un vector sea 0, es cuando todas sus componentes sean 0.
$$
\|\underline{X}\|=0\quad \iff \quad \underline{X}=\left[ \begin{matrix}
0 \\
0 \\
0 \\
\vdots\\
0
\end{matrix} \right]
$$
3. Si una constante multiplica a un vector, su norma es igual a la norma propia del vector multiplicada por el valor absoluto de la constante.
$$
\|c \underline{X}\|=|c|\|\underline{X}\|,\,\forall \underline{X}\in\mathbb{R}^{n}\,\forall c\in\mathbb{R}
$$
4. Si tenemos dos vectores, la norma del vector resultante de su adición será menor que la suma de la norma de cada vector individual.
$$
\|\underline{X}+\underline{Y}\|\leq\|\underline{X}\|+\|\underline{Y}\|,\,\forall \underline{X}\,\forall\underline{Y}\in\mathbb{R}^{n}
$$

---

# Producto interno de vectores en $\mathbb{R}^{n}$

## Caso discreto

El producto interno de dos vectores $\underline{X}$ y $\underline{Y}$ ambos pertenecientes a $\mathbb{R}^{n}$, es denotado por $(\underline{X},\underline{Y})$ y es definida como la suma de los productos respectivos de sus miembros:
$$
(\underline{X},\underline{Y})=\sum_{k=1}^{n}(x_{i}y_{i})=x_{1}y_{1}+x_{2}y_{2}+x_{3}y_{3}+\dots+x_{n}y_{n}
$$
Tenemos que el producto interno discreto cumple las siguientes propiedades:

1. El producto interno cumple la conmutatividad
$$
(\underline{X},\underline{Y})=(\underline{Y},\underline{X})\quad\forall \underline{X}\,\forall\underline{Y}\in\mathbb{R}^{n}
$$
2. El producto interno entre dos vectores iguales siempre será mayor o igual a 0.
$$
(\underline{X},\underline{X})\geq 0
$$
3. El producto interno cumple la linealidad.
$$
(c_{1}\underline{X}+c_{2}\underline{Y},\underline{Z})=(c_{1}\underline{X},\underline{Z})+(c_{2}\underline{Y},\underline{Z})
$$
4. Dos vectores son ortogonales si y solo si su producto interno es 0.
$$
\underline{X}\text{ y }\underline{Y}\text{ son ortogonales }\iff (\underline{X},\underline{Y})=0
$$
- Un conjunto de vectores n-dimensionales $\left\{ v_{1},v_{2},v_{3},\dots,v_{n} \right\}$ son ortogonales si el producto interno de dos vectores cualesquiera dentro del conjunto es 0.	$$
(v_{i},v_{j})=0
$$

> [!important] Vectores ortogonales
> Esto significa que no importa que par de vectores distintos tome, siempre deberán de dar 0, no es que al menos un producto interno sea 0


- Un conjunto de vectores n-dimensionales son **ortonormales** si, además de ser ortogonales, el conjunto está formado por vectores unitarios.
$$
(v_{i},v_{j})=0\wedge\|v_{i}\|\,\forall i\in[1,n]
$$
- El teorema de Pitágoras se cumple si el producto interno de dos vectores es 0.
$$
\|\underline{X}+\underline{Y}\|^{2}=\|\underline{X}\|^{2}+\|\underline{Y}\|^{2}\quad \iff\quad (\underline{X},\underline{Y})=0
$$

