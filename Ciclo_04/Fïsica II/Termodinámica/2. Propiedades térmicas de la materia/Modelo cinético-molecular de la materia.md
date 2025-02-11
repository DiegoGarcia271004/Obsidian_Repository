---
tags:
  - Física_II
---
A continuación se presentará un modelo sencillo de los [[Ecuaciones de estado#Gases ideales|gases ideales]]. Este modelo representa el gas como un gran número de partículas que rebotan en un ambiente cerrado. En esta sección se utilizará el modelo cinético-molecular para poder predecir la capacidad calorífica molar de un gas ideal.

Para este modelo se toman las siguientes suposiciones:
1. Un recipiente con un volumen $V$ posee una gran cantidad $N$ de moléculas idénticas, cada una posee una masa $m$.
2. Las partículas se comportan como [[1.1 Partícula, sistemas de referencia y desplazamiento|partículas puntuales]]; su tamaño será inferior en comparación con la distancia media entre las partículas y las dimensiones del recipiente.
3. Las moléculas se encuentran en constante movimiento. Ocasionalmente las partículas chocan con las paredes del recipiente. Estos choques son [[Conservación del momento lineal y choques#Choques elásticos e inelásticos|perfectamente elásticos]].
4. Las paredes del recipiente son rígidas y de masa infinita, es decir que no se mueven.

## Colisiones y presión de gas 

Cuando las partículas chocan contra las paredes, estas ejercen fuerza contra ellas; este es el origen de la presión del gas. 
Se supondrá que las moléculas del gas poseen la misma magnitud en su componente $x$ de velocidad de su movimiento.
Cuando una partícula choca contra una de las paredes, su componente $x$ de velocidad cambia de $-|v_{x}|$ a $+|v_{x}|$, por lo que su [[Momento lineal e impulso|momento lineal]] $-m|v_{x}|$ también cambia de dirección, es decir a $+m|v_{x}|$. Por consecuente el cambio del momento lineal es de: $m|v_{x}|-(-m|v_{x}|)=2m|v_{x}|$.

Si la molécula va a chocar contra una de las paredes con área $A$ en un instante de tiempo $dt$, entonces se debe encontrar al menos a una distancia $|v_{x}|dt$ y dirigida hacia la pared. Por lo que el número de moléculas que chocan con $A$ durante $dt$ es igual al número de moléculas que se encuentran en un cilindro con área de la base $A$ y altura $|v_{x}|dt$ y cuya velocidad $x$ esté en dirección a la pared.
El volumen del cilindro anterior está dada por $A|v_{x}|\,dt$. Si se supone que la cantidad de moléculas por unidad de volumen ($N/V$) es uniforme, entonces el número de moléculas en el cilindro es de $(N/V)(A|v_{x}|\,dt)$. Obteniendo el promedio, la mitad de las partículas se encuentran chocando y la otra mitad se encuentran alejándose de la pared (porque ya chocaron), entonces la cantidad de choques con $A$ en el instante $dt$ es de: 
$$
\frac{1}{2}\left( \frac{N}{V} \right)(A|v_{x}|\,dt)
$$
Para todo el sistema de choques de las partículas de gas, el cambio de momento lineal $dP_{x}$ durante $dt$ es el número de choques multiplicado por $2m|v_{x}|$:
$$
dP_{x}=\frac{1}{2}\left( \frac{N}{V} \right)(A|v_{x}|\,dt)(2m|v_{x}|)=\frac{NAv_{x}^{2}dt}{V}
$$
Por lo que la tasa de cambio de la componente de momento lineal $P_{x}$ es de:
$$
\frac{dP_{x}}{dt} =\frac{NAv_{x}^{2}}{V} 
$$
Si retomamos la segunda ley de Newton, la variación de momento lineal es igual a la fuerza ejercida por las moléculas sobre el área ($p=\frac{F}{A}$), por lo que:
$$
p=\frac{F}{A}=\frac{NAv^{2}_{x}}{V}
$$
## Presión y energías cinéticas moleculares

Antes se dijo que la velocidad $|v_{x}|$ era igual para todas las partículas, pero esto no es del todo acertado, pero podemos concluir que realmente, después de todo no es tan importante, esto debido a los siguiente:

Se puede empezar organizando las velocidades, sabiendo que la magnitud total de la velocidad de la partícula está dada por:
$$
v^{2}=v_{x}^{2}+v_{y}^{2}+v_{z}^{2}
$$
Podemos, además, promediar las velocidades:
$$
(v^{2})_{\text{med}}=(v_{x}^{2})_{\text{med}}+(v_{y}^{2})_{\text{med}}+(v_{z}^{2})_{\text{med}}
$$
Pero en nuestro modelo (planteado al inicio del documento) no existe una diferencia real entre las direcciones $v_{x}\,v_{y}\,\text{y } v_{z}$ por lo que las velocidades medias de las tres componentes deben ser las mismas. Por lo tanto:
$$
(v_{x}^{2})_{\text{med}}=\frac{1}{3}(v^{2})_{\text{med}}
$$
Por lo que nuestra ecuación de la sección anterior se convierte en:
$$
pV=\frac{1}{3}Nm(v^{2})_{\text{med}}=\frac{2}{3}N\left[ \frac{1}{2}m(v^{2})_{\text{med}} \right]
$$
Observamos que $\frac{1}{2}m(v^{2})_{\text{med}}$ es la [[Trabajo y energía cinética|energía cinética]] de traslación media de una sola molécula. El producto de esto por el número de moléculas $N$ es igual a la energía cinética aleatoria (?) total $K_{tr}$del movimiento de traslación. Por lo que tras esto, podemos concluir:
$$
pV=\frac{2}{3}K_{\text{tr}}
$$
Por lo que si igualamos con la ecuación de los gases ideales:
$$
K_{\text{tr}}=\frac{3}{2}nRT
$$
Siendo está la energía cinética de traslación media de $n$ moles de gas ideal.

Gracias a este resultado, podemos decir que la energía cinética de transición media es directamente proporcional a la temperatura absoluta $T$.

A partir de esta ecuación, podemos obtener la energía cinética de traslación media de una sola molécula al dividirla entre la cantidad de moléculas $N$:
$$
\frac{K_{\text{tr}}}{N}=\frac{1}{2}m(v^{2})_{\text{med}}=\frac{3nRT}{2N}
$$

A su vez, sabemos que la cantidad de moléculas en el gas es igual a la cantidad de moles por el número de Avogadro $N_{A}$ ($6.022\times10^{23} \,\mathrm{moléculas/mol}$).
$$
N=nN_{A}\qquad \frac{n}{N}=\frac{1}{N_{A}}
$$
y
$$
\frac{K_{\text{tr}}}{N}=\frac{1}{2}m(v^{2})_{\text{med}}=\frac{3}{2}\left( \frac{R}{N_{a}} \right)T
$$
La proporción dada por $R/N_{A}$ aparece frecuentemente en la teoría molecular y se denomina constante de Boltzmann, el valor más aceptado para esta constante es de $1.3806\times10^{-23}\mathrm{J/molécula\cdot K}$.

Por lo que podemos definir la energía cinética de traslación media de una molécula de gas como:
$$
\frac{1}{2}m(v^{2})_{\text{med}}=\frac{3}{2}kT
$$
### Rapidez eficaz de una molécula de gas

A partir de la ecuación encontrada, es posible despejar la velocidad de ella:
$$
v_{\text{rms}}=\sqrt{ (v^{2})_{\text{med}} }=\sqrt{ \frac{3kT}{m} }=\sqrt{ \frac{3RT}{M} }
$$
Otra forma de poder expresar la $v_{\text{rms}}$ es la siguiente:
$$
v_{\text{rms}}=\sqrt{ \frac{3p}{\rho} }
$$
