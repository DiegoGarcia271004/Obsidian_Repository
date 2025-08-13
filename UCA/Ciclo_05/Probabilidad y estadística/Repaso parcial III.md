---
tags:
  - ProbabilidadYEstadística
---
1. Una planta de energía impulsada por carbón mineral está considerando un nuevo sistema para reducir los contaminantes. El actual sistema reporta que de 200 muestras de aire, 136 presentan niveles aceptables. El sistema que se está considerando instalar, y que opera a un costo mayor, reportó niveles aceptables de contaminación en 182 de 240 muestras de aire. ¿Recomendaría usted la instalación del nuevo sistema?

$$
\begin{gather*}
p_{1}=\frac{136}{200}=0.68\qquad p_{2}=\frac{182}{240}=0.7583\\
H_{0}:p_{1}\geq p_{2}\\
H_{a}:p_{1}<p_{2}\\
\text{se calcula la proporción combinada:}\\
\hat{p}= \frac{136+182}{200+240}=0.7227\\
\sigma=\sqrt{ \hat{p}(1-\hat{p})\left( \frac{1}{200}+\frac{1}{240} \right) }=0.0429\\
\text{obteniendo el estadístico z}:\\
Z_{c}=\frac{p_{2}-p_{1}}{\sigma}=1.825\\
\text{valor comparado con }\alpha=0.05
\\
Z_{0.05}=1.64\\
Z_{c}>Z_{0.05}\\
\therefore \text{Se rechaza la hipótesis nula}
\end{gather*}
$$

2. Una fábrica de sorbete utiliza una máquina que llena cartones con 64 onzas de producto. Se considera que la máquina está desajustada si llena los cartones con más producto o menos producto. El encargado de producción toma cada día una muestra de 16 cartones para controlar la operación de la máquina. Una muestra de un día cualquiera produjo los siguientes datos:

62.7, 64.7, 64.0, 64.5, 64.6, 65.0, 64.4, 64.2,  
64.6, 65.5, 64.7, 64.0, 64.2, 63.6, 63.0, 63.6

¿Existen evidencias en los datos que indiquen que la máquina está desajustada? Considere que el llenado de producto se distribuye normalmente.  
Utilice α = 0.05.

$$
\begin{gather*}
\hat{\mu}=64.206\quad n=16 \quad s=0.7197 \quad \alpha=0.05\\
H_{0}:\hat{\mu}=\mu\\
H_{a}:\hat{\mu}\neq \mu\\
\text{calculando }t_{c}:\\
t_{c}=\frac{64.206-64}{0.7197/\sqrt{ 16 }}=1.145\\
t(0.05/2,15)=2.131\\
t_{c}\in[-2.131,2.131]\quad \therefore\text{Se acepta }H_{0}
\end{gather*}
$$

3. Se realizó un experimento para estudiar la eventual influencia de la luz en el crecimiento de una especie de pez. Dos lotes de peces fueron puestos bajo condiciones de luminosidad diferentes. El lote 1 (180 individuos) con luminosidad de 400 lux y el lote 2 (90 individuos) con 2000 lux.

El día 95 se midió la longitud en mm de los peces con los siguientes resultados:  
Lote 1: media = 21 y varianza = 30.75  
Lote 2: media = 22.7 y varianza = 20.36

Organice una prueba estadística y exprese con claridad su conclusión.  
Utilice α = 0.10 y suponga las varianzas poblacionales iguales.

$$
\begin{gather*}
H_{0}:\mu_{1}=\mu_{2}\\
H_{a}:\mu_{1}\neq\mu_{2}\\
\text{calculando }S^{2}_{p}:\\
S^{2}_{p}=\frac{(180-1)30.75+(90-1)20.36}{180+90-2}=27.3\\
\text{calculando }t_{c}:\\
t_{c}=\frac{21-22.7}{\sqrt{ 27.3\left( \frac{1}{180}+\frac{1}{90} \right) }}=-2.52\\
t_{c}\not\in[-1.645, 1.645]\\
\therefore\text{Hay suficiente evidencia para rechazar } H_{0}
\end{gather*}
$$


4. Para determinar la efectividad de un programa de seguridad industrial se recogieron datos sobre la pérdida semanal de horas-trabajador, debidos a accidentes en 7 plantas, respectivamente antes y después de que se pusiera en operación el programa:

- Antes: 50, 87, 37, 141, 59, 65, 24    
- Después: 41, 75, 35, 129, 60, 53, 26

¿Es efectivo el programa de seguridad?  
(_Use_ α=0.05)

```latex
list1:={50,87,37,141,59,65,24}
list2:={41,75,35,129,60,53,26}
list3:=list1 - list2

tTest 0,list3,1,0: stat.results
```



5. Se realizó una encuesta para conocer la opinión de una comunidad sobre un proyecto de explotación minera en la zona. De 400 encuestados, solo 140 se manifestaron a favor del proyecto.

**a)** Determinar un intervalo de confianza del 95% para la proporción poblacional de los que están de acuerdo.  
**b)** Si se desea bajar el error de la estimación al 2.5%, ¿de qué tamaño debería ser la muestra?


## **Planteamiento del problema**

Se desea probar si los siguientes datos se ajustan a una distribución **geométrica** con:

$$
f(x)=p(1−p)x−1f(x) = p(1 - p)^{x - 1}f(x)=p(1−p)x−1
$$


Usamos la propiedad:

$$
E(X)=1pE(X) = \frac{1}{p}E(X)=p1​
$$

Nivel de significancia: **α = 0.05**

|x|Frecuencia observada O(x)|
|---|---|
|1|136|
|2|60|
|3|34|
|4|12|
|5|9|
|6|3|
|**Total**|**254**|

---

## **Paso 1: Estimación del parámetro**

Se estima el parámetro p usando la media muestral:

$$
\begin{gather*}
\bar{x}=1(136)+2(60)+3(34)+4(12)+5(9)+6(3)254=\frac{469}{254}≈1.847
\end{gather*}
$$

Entonces,

$$
\hat{p}=\frac{1}{\bar{x}}=11.847≈0.5415
$$

---

## **Paso 2: Cálculo de probabilidades teóricas**

Usamos:

$$
P(x)=p(1−p)x−1P(x) = p(1 - p)^{x - 1}P(x)=p(1−p)x−1

$$
Con p=0.5415:

|x|P(x) aproximado|
|---|---|
|1|0.5415|
|2|0.2484|
|3|0.1139|
|4|0.0523|
|5|0.0240|
|≥ 6|0.020 (acumulado)|

Nota: Se agrupa la categoría “6 o más” para asegurar frecuencias esperadas mayores a 5.

---

## **Paso 3: Frecuencias esperadas**

Multiplicamos las probabilidades por el total n=254n = 254n=254:

|x|E(x) = n·P(x)|
|---|---|
|1|137.5|
|2|63.1|
|3|28.9|
|4|13.3|
|5|6.1|
|≥ 6|5.1|

---

## **Paso 4: Estadístico chi-cuadrado**

$$
\chi^2 = \sum \frac{(O_i - E_i)^2}{E_i}​
$$

|x|O(x)|E(x)|(O−E)²/E|
|---|---|---|---|
|1|136|137.5|0.0164|
|2|60|63.1|0.1524|
|3|34|28.9|0.9003|
|4|12|13.3|0.1271|
|5|9|6.1|1.3820|
|≥ 6|3|5.1|0.8658|
|**Total**|||**3.44**|

---

## **Paso 5: Grados de libertad**


$$
df = \text{número de clases} - 1 - \text{parámetros estimados}
$$
$$
df=6−1−1=4
$$
Valor crítico:

$$\chi^2_{0.05, 4} = 9.49$$

---

## ✅ **Conclusión**

Como $\chi^2_{\text{calc}} = 3.44 < \chi^2_{\text{crítico}} = 9.49$, **no se rechaza la hipótesis nula**.

> Por lo tanto, los datos **sí se ajustan a una distribución geométrica** con $\approx 0.5415p≈0.5415$.


