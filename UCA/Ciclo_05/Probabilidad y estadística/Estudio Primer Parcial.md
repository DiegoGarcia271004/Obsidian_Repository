

Una compañía distribuye un test de aptitud entre todos sus nuevos representantes de ventas. La dirección tiene interés en conocer la capacidad del test para predecir el eventual éxito de estos representantes. La tabla adjunta recoge el valor (en cientos de dólares) de las ventas semanales medias y las respectivas puntuaciones obtenidas en el test de aptitud para una muestra aleatoria de 8 representantes.

| **Puntuación en el test** | **Ventas semanales** |
| ------------------------- | -------------------- |
| 55                        | 10                   |
| 60                        | 12                   |
| 85                        | 28                   |
| 75                        | 24                   |
| 80                        | 18                   |
| 85                        | 20                   |
| 65                        | 15                   |
| 60                        | 15                   |
<!-- TBLFM: @>$>=sum(@2$<..@>$<) -->
a) Elija las variables dependiente e independiente y elabore un diagrama de dispersión de los datos.
b) Determine la recta de regresión de Y sobre X.
c) Calcule los coeficientes de correlación y determinación, y evalúe el grado de dependencia entre
las variables.
d) Estime el valor de las ventas para alguien que obtuvo un puntaje de 62 en el test.

---

Primero que nada, vaya pedazo de basura de tabla que es.

**a)**
Para un diagrama de dispersión, simplemente hay que poner los datos de la tabla en un gráfico, obviamente para esto hay que definir la variable dependiente e independiente. Para la independiente preferiblemente tomamos la columna con menor variación, en este casos sería la  columna de la puntuación en el test, por lo que la segunda sería la variable dependiente.

**b) y c)**
La regresión lineal de la forma $a+bx$ puede realizarse ya sea manualmente o con la ayuda de la calculadora, por fines de tiempo y versatilidad, se recomienda trabajarla en la calculadora.
Los resultamos que hemos obtenido tras la regresión son los siguientes:

| Ecuación | $a+bx$ |
| -------- | ------ |
| $a$      | -12.40 |
| $b$      | 0.4269 |
| $r^{2}$  | 0.7232 |
| $r$      | 0.8504 |
Con estos valores concluimos que la recta de regresión es:
$$
y=-12.40+0.4269x
$$
**Coeficiente de correlación:**
Este valor es dado por $r$, que anteriormente obtuvimos. El valor que posee nos indica que los datos poseen una fuerte correlación entre sí como una regresión lineal.
**Coeficiente de determinación:** 
El valor de este coeficiente es dado por $r^{2}\times100\%$ es decir: $72.32\%$ este valor representa que este porcentaje de la variación en las ventas puede explicarse por este modelo.

**d)**
Para poder estimar el valor de la venta de alguien con 62 puntos, usaremos la recta de regresión que anteriormente calculamos y evaluaremos el valor de $x=62$:
$$
\begin{gather*}
y(x)=-12.40+0.4269x\\
y(62)=-12.40+0.4269(62)\\
\boxed{y(62)=14.06}
\end{gather*}
$$
---

De 10 sensores de radiación solar, tres están mal calibrados. Si se eligen cinco sensores al azar,
menciona la probabilidad de que aparezcan:
a) Exactamente dos mal calibrados.
b) A lo sumo uno mal calibrado.

---

**a)**

Para trabajar con probabilidades, tendremos que utilizar la fórmula de Laplace, que establece que la probabilidad de un evento es igual a la cantidad de casos favorables entre la cantidad de sucesos posibles:
$$
P(A)=\frac{n(A)}{n(S)}
$$
Para este caso, ya que estamos tomando 5 sensores de los 10, nuestro espacio muestral serán las posibles formas de tomar 5 de esos 10 sensores, por lo que:
$$
n(S)=\left( \begin{matrix}
10 \\
5
\end{matrix} \right)=252
$$
tenemos 252 formas de tomar 5 sensores de los 10 dados.

Ahora, para buscar de cuantas formas podemos obtener 2 sensores malos de los 3, sería:
$$
\left( \begin{matrix}
3 \\
2
\end{matrix} \right)
$$
Pero ya que ahora tendríamos que variar entre los que si están bien calibrados, entonces también tendremos que calcular cuantas formas podemos tomar esos 3 sensores calibrados de los 7 que tenemos:
$$
\left( \begin{matrix}
7\\
3
\end{matrix} \right)
$$
Finalmente, como estos dos sucesos pueden combinarse con el otro, debemos utilizar la multiplicación, por lo que:
$$
n(A)=\left( \begin{matrix}
3 \\
2
\end{matrix} \right)\cdot\left( \begin{matrix}
7 \\
3
\end{matrix} \right)=105
$$
Finalmente, calculando la probabilidad:
$$
P(A)=\frac{n(A)}{n(S)}=\frac{105}{252}\approx 0.4167
$$
Por lo que la probabilidad de obtener 2 sensores malos tras tomar 5 es del 41.67%

**b)**

Para el segundo caso, nos pide que **máximo** un sensor malo, por lo que realmente estamos trabajando 2 casos, uno en donde no sacamos ningún malo, y otro donde obtenemos al menos un sensor malo.

Ya que igual que en el caso anterior sacamos 5, la cantidad total de eventos se mantiene igual $n(S)=252$.

Para los casos favorables, como dijimos anteriormente, son 2 tipos:
**Donde no se obtiene un sensor malo:**
$$
\left( \begin{matrix}
3 \\
0
\end{matrix} \right)\cdot\left( \begin{matrix}
7 \\
5
\end{matrix} \right)=21
$$
**Donde se obtiene un solo sensor malo:**
$$
\left( \begin{matrix}
3 \\
1
\end{matrix} \right)\cdot\left( \begin{matrix}
7 \\
4
\end{matrix} \right)=105
$$
Y ya que son dos eventos independientes:
$$
n(B)=21+105=126
$$
Por lo que su probabilidad sería:
$$
P(B)=\frac{126}{252}=0.5
$$

---

Un profesor de matemática ha preparado un examen que contiene 12 ejercicios, de los cuales 4 son demostraciones y los demás son ejercicios normales. El estudiante deberá elegir al azar 5 ejercicios de los 12 propuestos.
Determina la probabilidad de que entre los 5 elegidos:
a) Todos sean ejercicios normales
b) Al menos 1 sea demostración

---
**a)**

Primeramente, para encontrar la cantidad de casos totales, se observa que de 12 ejercicios, se deben de escoger 4, por lo que:
$$
n(S)=\left( \begin{matrix}
12 \\
5
\end{matrix} \right)=792
$$
Para encontrar la cantidad de casos en los que solo se toman normales, se deben saber de cuantas formas se pueden escoger los normales:
$$
\left( \begin{matrix}
8 \\
5
\end{matrix} \right)=56
$$
Así que la probabilidad será de:
$$
P(A)=\frac{56}{792}=0.0707
$$
**b)**

Ya que el caso de que al menos 1 sea de demostración, el único caso que no contempla, es el de que ninguno sea de demostración, por lo que se consideraría el complemento del ejercicio anterior, de modo que:
$$
P(B)=\overline{P(A)}=1-P(A)=1-0.0707=0.9293 
$$
---
Los puntajes obtenidos en un examen estandarizado de matemáticas por 60 estudiantes de  ́ultimo
año de bachillerato se agrupan en la siguiente tabla de frecuencias:

| Puntaje (intervalo) |     $f_{i}$     |
| :-----------------: | :-------------: |
|        14-16        |        4        |
|        16-18        |        6        |
|        18-20        |       12        |
|        20-22        |       22        |
|        22-24        |       10        |
|        24-26        |        6        |

a) Calcule la media y la desviación estándar de la distribución.
b) Aproximadamente, ¿Qué porcentaje de estudiantes obtuvo entre 19 o más puntos?
c) Si cada estudiante recibe un punto por cada respuesta correcta, y el puntaje representa el total
de respuestas correctas, ¿Cuántas respuestas correctas se han obtenido en total entre todos los
estudiantes?
d) Elabore un histograma para la distribución y mencione qué tipo de asimetría observa.
e) Si se calcula el porcentaje que representa la desviación estándar respecto a su propia media,
¿Cómo se interpreta este valor?
f) Calcule la cota Z para un estudiante que obtuvo 17 puntos. ¿Qué significa ese resultado?


| Puntaje (intervalo) |     $f_{i}$     |     $x_{i}$      |      $x_{i}f_{i}$      |     $F_{i}$     |    $(x_{i}-\bar{x})^{2}\cdot f_{i}$    |
| :-----------------: | :-------------: | :--------------: | :--------------------: | :-------------: | :------------------------------------: |
|        14-16        |        4        |        15        |           60           |        4        |                122.3236                |
|        16-18        |        6        |        17        |          102           |       10        |                74.7654                 |
|        18-20        |       12        |        19        |          228           |       22        |                28.0908                 |
|        20-22        |       22        |        21        |          462           |       44        |                 4.8598                 |
|        22-24        |       10        |        23        |          230           |       54        |                 61.009                 |
|        24-26        |        6        |        25        |          150           |       60        |                119.8854                |
|     **TOTALES**     | $\sum f_{i}=60$ | $\sum x_{i}=120$ | $\sum x_{i}f_{i}=1232$ | $\bar{x}=20.53$ | $\sum (x_{i}-\bar{x})^{2}f_{i}=410.93$ |

**a)**

Antes que nada, ya que son datos agrupados, entonces lo que se tiene q hacer es obtener un valor representativo, para esto podemos hacer uso de la siguiente fórmula:
$$
x_{i}=\frac{L_{s}+L_{i}}{2}
$$
Y estos datos se agregan a la tabla.
A continuación, para encontrar la media, tendríamos que sumar todos los productos entre el valor representativo de cada clase y la respectiva frecuencia, luego dividirlo entre la cantidad de datos recopilados (o la suma de todas las frecuencias):
$$
\bar{x}=\frac{\sum x_{i}f_{i}}{n} =20.53
$$
Para la desviación estándar, debemos encontrar la raíz de la suma de todos los valores representativos menos la media al cuadrado multiplicada por la frecuencia de cada clase dividido entre la cantidad de datos disminuido en uno.
$$
s=\sqrt{ \frac{\sum(x_{i}-\bar{x})^{2}\cdot f_{i}}{n-1} }=2.64
$$
**b)**

Para obtener el porcentaje de estudiantes que obtuvieron una nota mayor a 19 puntos, tenemos que observar la tabla y verificar cuantos estudiantes están por encima de esta nota.
Ya que vemos que 19 es un valor intermedio de una de las clases, entonces asumimos que la mitad de los estudiantes que se encuentran en esta clase no cumplen nuestros requerimientos, por lo que de 12 estudiantes cuyas notas están entre 18 y 20, solamente tomaremos 6.
Luego sumaremos las frecuencias de las demás clases y dividiremos entre la cantidad total de estudiantes y multiplicaremos por 100%:
$$
\frac{6+22+10+6}{60}\cdot100\%=\boxed{73.3\%}
$$

