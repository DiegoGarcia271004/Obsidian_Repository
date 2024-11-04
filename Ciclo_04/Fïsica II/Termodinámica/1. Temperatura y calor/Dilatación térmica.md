---
tags:
  - Física_II
---
## Expansión lineal

Si se tiene una varilla de un material con una longitud inicial $L_{0}$ a una temperatura $T_{0}$. Si la temperatura cambia en $\Delta T$, entonces la longitud de la varilla cambiara en $\Delta T$.
Si el cambio de temperatura no es muy grande (menos de 100°C) entonces la variación de longitud es directamente proporcional al cambio de temperatura por lo que si se agrega una constante de proporcionalidad $\alpha$ entonces se puede expresar de la siguiente manera:
$$
\Delta L=\alpha L_{0}\Delta T
$$
La constante de proporcionalidad se denomina *coeficiente de expansión lineal* cuyas unidades son $K^{-1}$ 

---
## Expansión volumétrica

Al igual que en la expansión térmica, un aumento de temperatura representa un aumento en el volumen de materiales, tanto líquidos como sólidos. Igualmente, la variación de volumen es directamente proporcional a la variación de temperatura del material por lo que:
$$
\Delta V=\beta V_{0}\Delta T
$$
En este caso, $\beta$ es el *coeficiente de expansión volumétrica* el cual posee las mismas unidades que la constante de expansión lineal.
En la cuál tras unos cálculos se puede concluir que para un material con un coeficiente de expansión lineal $\alpha$ se cumple:
$$
\beta=3\alpha
$$

---
## Esfuerzo térmico

Si una varilla se sujeta rígidamente con el fin de evitar la expansión o contracción y se varía la temperatura, aparecerán esfuerzos de tensión o compresión llamados *esfuerzos térmicos*. 
Estos esfuerzos en construcción pueden llevar a deformaciones permanentes o incluso a romper el material, por esto mismo se suelen tener espacios entre secciones para permitir la deformación por temperatura.

Para poder calcular los esfuerzos térmicos en una varilla sujeta, primeramente se debe calcular cuánto se expandiría en el caso de no estar sujeta, luego se calcula el esfuerzo necesario para comprimirla (o estirarla) a su longitud original.

Si se tiene una varilla de longitud $L_{0}$ y área transversal $A$ se mantiene con longitud constante, mientras se reduce la temperatura, causando un esfuerzo de tensión. El cambio fraccionario de longitud si la varilla no tuviera retenciones sería: 
$$
\left( \frac{\Delta L}{L_{0}} \right)_{\text{térmico}} =\alpha\Delta T
$$

Por la propia definición del módulo de Young ($Y=\frac{F/A}{\Delta L/L}$) donde el cociente entre la variación de la longitud y la longitud inicial es el cambio fraccionario de la tensión, por lo que:
$$
\left( \frac{\Delta L}{L_{0}} \right)_{\text{tensión}}=\frac{F}{AY}
$$
Por lo que si se suman tanto el cambio fraccionario térmico como el de la tensión, debería ser 0. Por lo que se obtiene:
$$
\left( \frac{\Delta L}{L_{0}} \right)_{\text{térmico}}+\left( \frac{\Delta L}{L_{0}} \right)_{\text{tensión}}=\alpha\Delta T+\frac{F}{AY}=0
$$
$$
\frac{F}{A}=-\alpha Y\Delta T
$$

