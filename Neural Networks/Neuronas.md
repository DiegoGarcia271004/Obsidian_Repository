---
date: 2026-03-01
---
# Neuronas
Las [[Introducción a las redes neuronales|redes neuronales]] se llaman así porque, sorpresa, son redes de neuronas, que se encuentran conectadas entre sí, activándose en respuesta a las señales que recibe de entrada, y contribuyendo a la activación de otras por medio de su salida.

Es más o menos de esta forma cómo funcionan las neuronas del cerebro. Reciben un estímulo, se activan, y mandan señales a otras neuronas con las que se encuentran conectadas

## Neuronas artificiales
Al imitar neuronas, podemos tomarnos muchos tipos de libertades; pero la idea central es que son vistas como una función con varios parámetros:
- Señales de entrada.
- Umbral de activación, o también llamado sesgo.

Una neurona artificial recibe $n$ señales de entradas, cada una de las cuales vamos a representar como $a_{i}$. La neurona suma estas señales, y compara el resultado de la suma con el umbral de activación:
- Si la suma es mayor que el umbral, la neurona se activa.
- Si la suma es menor o igual que el umbral, la neurona no se activa.

Además, una cosa a replicar es que hay ciertas neuronas a las que se le quiere dar mayor importancia si resulta que estas son activadas; y también se da el caso que hay ciertas señales que no son relevantes para la activación de cierta neurona. Para retratar esto, se utilizan pesos $w_{i}$ en las conexiones de las neuronas, multiplicando el valor de la salida con el peso, y sumando.
Es decir, el umbral se compara con una suma ponderada de las señales de entrada con sus respectivos pesos.

> [!NOTE] Perceptrón
> La neurona artificial más sencilla es la de un perceptrón, una forma de red neuronal antigua diseñado para replicar el comportamiento de las neuronas biológicas, y por tanto, tienen una salida binaria: Activada o desactivada.
> 
> La neurona de un perceptrón se representa por la siguiente función:
> $$\begin{cases}
> 1 \quad  \text{si} \quad  \Sigma_{i}\, a_{i}w_{i} > \text{umbral} \\
> 0 \quad  \text{si} \quad  \Sigma_{i}\, a_{i}w_{i} \leq \text{umbral} 
> \end{cases}$$

Las señales de entradas pueden pasar por varios procesos, dependiendo de lo que se quiere hacer con la red. Por ejemplo, para imágenes complejas, se utilizan convoluciones dado que la convolución de pixeles es una excelente forma de reconocer formas, como curvas o bordes.

También, las neuronas no necesariamente tienen que tener una salida binaria como la del perceptrón para funcionar. De hecho, es mucho mejor que las neuronas tengan un rango de activación continuo, y no discreto; pero depende del uso que se le quiera dar el rango que las neuronas son limitadas.

La activación de las neuronas se hacen por medio de **funciones de activación**, las cuales varían dependiendo del uso o comportamiento que se les quiere dar. Entre los ejemplos de estas funciones, se encuentran:
- Función escalón (usada en la neurona de un perceptrón).
- Función logística o sigmoide.
- Función rectificadora o ReLU.

Por ejemplo, si queremos que una neurona tenga un rango de activación entre 0 y 1, entonces el valor resultante se pasa por la función logística, también llamada sigmoide, ya que es una función útil para marcar valores altos como cercanos a 1, y valores negativos o bajos como cercanos a 0.
Por otro lado, si queremos recompensar valores positivos y desprestigiar valores negativos, se usa la función ReLU, definida como $\max(0,x)$. Todos los valores negativos son igualados a cero, y los valores positivos se dejan como son.

## Estándar matemático
Las redes neuronales se suelen trabajar en capas. Cada neurona de una capa manda su señal de salida a las neuronas de la siguiente capa; y cada neurona de la siguiente capa recibe las salidas de todas las neuronas de la capa anterior. Recordar, cada salida tiene un peso que determina la importancia que se le tiene que dar a esta neurona para la activación.

Entonces, refiriéndonos a una neurona como ${a_{i}}^{(l)}$, esta realiza una suma ponderada de las señales de entrada, que puede ser representado como:
$$w_{0}\,  {a_{0}}^{(l-1)}+w_{1}\, {a_{1}}^{(l-1)}+w_{2}\, {a_{2}}^{(l-1)}+\dots+w_{n}\, {a_{n}}^{(l-1)}$$

Pero, una forma de abreviarlo es observando a los pesos como componentes de un vector $\mathbf{w}$ de pesos; y a los valores de entrada (o salida de la capa $k-1$) como componentes de un vector $\mathbf{a}$ de salidas. Entonces, la suma ponderada es simplemente el [[producto punto]] entre estos dos vectores. Con esto, por ejemplo, la función de una neurona de un perceptrón sería:

$${a_{i}}^{(l+1)}=\begin{cases}
1 \quad  \text{si} \quad  \mathbf{w}_{l} \cdot \mathbf{a}_{l}  > \text{umbral} \\
0 \quad  \text{si} \quad  \mathbf{w}_{l} \cdot \mathbf{a}_{l} \leq \text{umbral} 
\end{cases}$$
Otro estándar es pasar el umbral de activación al otro lado de la desigualdad, en donde cambia de nombre y pasa a ser llamado **sesgo de activación**. Si bien son conceptos con diferentes nombres, es simple recordar que $\text{sesgo} \equiv -\text{umbral}$. 

Como sesgo en inglés es *bias*, generalmente vemos al sesgo representado por una $b$. Si el umbral significaba qué tan difícil es activar una neurona, el sesgo indica qué tan fácil es activarla:
$${a_{i}}^{(l+1)}\begin{cases}
1 \quad  \text{si} \quad  \mathbf{w}_{l}\cdot \mathbf{a}_{l} + b_{i} > 0 \\
0 \quad  \text{si} \quad  \mathbf{w}_{l}\cdot \mathbf{a}_{l} + b_{i} \leq 0
\end{cases}$$
En el ejemplo del perceptrón, podemos ver cómo la función escalón se hace obvia; pero se puede usar realmente cualquier función de activación que se desee. Por ejemplo, para una neurona sigmoide, la función sería la siguiente:
$${a_{i}}^{(l)}=\sigma(\mathbf{w}_{l}\cdot \mathbf{a}_{l}+b_{i})$$
En general, el producto punto y luego la suma del sesgo son evaluados en la función de activación $f$ que se desee:
$${a_{i}}^{(l)}=f(\mathbf{w}_{l}\cdot \mathbf{a}_{l}+b_{i})$$

> [!warning] No linealidad
> La función de activación no puede ser cualquiera... Tiene que cumplir una condición: Que no sea una función lineal. Si una función $f$ es lineal, entonces se cumple que $f(x+y)=f(x)+f(y)$ y también que $f(ax)=a\, f(x)$.
> 
> Esto es particularmente importante para las capas de neuronas, pues si una función de activación fuera lineal, entonces las capas colapsan en una sola.

### Capas enteras
Ahora, para hacer las cosas más sencillas de representar (o mejor dicho, compactas), ya que cada neurona tiene sus propios pesos y sesgos, lo que se hace es meter todos los pesos de las conexiones en una matriz, donde cada fila $i$ representa los pesos de la neurona $a_{i}$, y los sesgos de las neuronas dentro de un vector:
$$\begin{bmatrix}
w_{0,0} & w_{0,1} & \dots & w_{0,n}  \\
w_{1,0} & w_{1,1} & \dots & w_{1,n}  \\
\vdots & \vdots & \ddots & \vdots    \\
w_{k,0} & w_{k,1} & \dots & w_{k,n}
\end{bmatrix}
\begin{bmatrix}
{a_{0}}^{(l)} \\
{a_{1}}^{(l)} \\
\vdots \\
{a_{n}}^{(l)}
\end{bmatrix}+
\begin{bmatrix}
{b_{0}}^{(l)} \\
{b_{1}}^{(l)} \\
\vdots \\
{b_{k}}^{(l)}
\end{bmatrix}$$
El resultado, comprimido como $\mathbf{W}_{l}\, \mathbf{a}_{l}+b_{l}$, da como resultado un vector de $k$ componentes, cada uno de los cuales es evaluado por la función de activación. En esta notación:
$$f(\mathbf{a})=\begin{bmatrix}
f(a_{1}) \\
f(a_{2}) \\
\vdots \\
f(a_{n})
\end{bmatrix}$$
Por lo tanto, la forma compacta de una red neuronal es la siguiente:
$$a_{l+1}=f(\mathbf{W}_{l}\, \mathbf{a}_{l}+b_{l})$$
## Por qué funcionan las redes neuronales
Consideremos una neurona sencilla:
- Una neurona de un perceptrón, señal binaria.
- Dos señales de entrada, ambas con un peso de $-2$.
- Un sesgo de activación, de $3$.

Notaremos que la activación de esta neurona tiene un comportamiento idéntico al de una compuerta NAND:
- Si ambas señales están apagadas, es decir, su señal es cero, entonces la suma ponderada + sesgo es mayor que cero.
- Si una de las señales está encendida, la suma ponderada sumado al sesgo dan como resultado $1$, que sigue siendo mayor que cero.
- Pero si ambas están activadas, la suma ponderada es $-4$; sumarle el sesgo lo deja en $-1$ y por lo tanto, está por debajo de cero.

El caso de la compuerta NAND es especial porque se sabe que estas son **universalmente completas**. Con compuertas NAND se pueden replicar las compuertas lógicas básicas: AND, OR y NOT... Y, por inferencia, cualquier circuito puede hacerse exclusivamente con compuertas NAND.

Entonces, ya que las neuronas son capaces de replicar compuertas lógicas, entonces es posible diseñar circuitos; y una red neuronal es capaz de formar circuitos más complejos. Se puede decir incluso que, con una red neuronal lo suficientemente grande, es posible representar cualquier función computable. Sin embargo, hasta ahora no hay nada revolucionario.
Sí, las neuronas pueden formar circuitos lógicos; pero eso ya podíamos hacerlo antes, ¿no? Entonces, ¿no acabamos de reinventar la rueda?

La ventaja que sobrepasa a los paradigmas de programación clásicos es que, las redes neuronales pueden ajustarse por su cuenta, sin necesidad de nosotros pensar en los circuitos lógicos y diseñarlos. Estos circuitos se forman naturalmente por medio de un proceso sofisticado de [[entrenamiento]], el cual realmente es más matemática que entrenamiento.
### Por qué se usan capas
La intuición es simple. La capa inicial de neuronas recibe la señal de entrada, y en base a esta señal toma una decisión, la cual es pasada a la siguiente capa. Esta segunda capa ahora tomará una decisión a partir de la decisión tomada por la capa anterior, lo cual indica un mayor nivel de abstracción en la toma de decisiones.

Hay muchas formas de interpretar esto, desde un punto de vista de optimización hasta geométricos:
- La recursión de las capas de neuronas es equivalente a una composición de funciones, ya que el resultado de una capa es evaluado dentro de una función. Es por eso que, usando más capas se pueden hacer sub-cálculos intermedios, permitiendo representar funciones complejas con menos neuronas que una red poco profunda.
- Cada profundidad de capas abstrae elementos en una jerarquía de representaciones. Al analizar una imagen, la capa inicial puede que solo distinga líneas o bordes; pero las capas más profundas son capaces de reconocer formas, estructuras, patrones; llegando a la capa final que reconoce al objeto.
- La señal de entrada y las salidas de una capa de neuronas puede ser visto como un vector hiperdimensional. Cada capa transforma linealmente este vector (multiplicación matricial con los pesos) y luego cada componente es evaluado en una función de activación *no lineal*. Esta deformación del hiperespacio es más efectiva entre más veces se realice, permitiendo representaciones más complejas entre mayor sea la profundidad.

Hay más argumentos, pero en resumen, la profundidad permite crear representaciones complejas a partir de transformaciones simples aplicadas sucesivamente.