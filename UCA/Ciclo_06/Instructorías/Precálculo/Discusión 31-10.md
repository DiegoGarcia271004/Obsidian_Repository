Encuentre la solución a los siguientes problemas. Puede utilizar el método de solución que usted prefiera (igualación, sustitución, reducción)

1. Alberto y su padre se llevan 25 años. Calcular la edad de Alberto sabiendo que dentro de 15 años la edad de su padre será el doble de la edad que tiene Alberto actualmente.

Primeramente plantearemos las variables principales:
$$
\begin{gather*}
\text{Sea }x \text{ la edad de Alberto }\\
\text{Sea }y \text{ la edad del padre de Alberto}
\end{gather*}
$$
Entonces conocemos que la diferencia que se llevan Alberto y su padre es de 25 años (ya que por lógica el padre es mayor, entonces a él se le debe de restar la edad de Alberto, de lo contrario la diferencia sería negativa).
$$
y-x=25\tag{1}
$$
Para nuestra segunda ecuación, tomaremos que la edad del padre dentro de 15 años será la misma que el doble que la de Alberto actualmente, por lo que la definimos:
$$
y+15=2x\tag{2}
$$
Ya con las dos ecuaciones, podemos formar nuestro sistema de ecuaciones lineales:
$$
\begin{cases}
y-x=25 \\
y+15=2x
\end{cases}
$$
A continuación, para resolver este sistema usaremos sustitución, así que procederemos a despejar $y$ de $(1)$:
$$
y=25+x\tag{3}
$$
Ya con $y$ despejada, sustituimos $(3)$ en $(2)$:
$$
\begin{gather*}
25+x+15=2x\\
\boxed{35=x}
\end{gather*}
$$
Con esto podemos concluir que la edad de Alberto es de 35 años.
Ahora para la edad del padre, solo debemos sustituir la edad de Alberto en $(3)$:
$$
\begin{gather*}
y=25+35\\
\boxed{y=60}
\end{gather*}
$$
Con todo esto podemos concluir que la edad de Alberto es de 35 años, y la edad del padre es de 60 años.

--- 

2. Se desea construir un envase cilíndrico para jugos, con $15\, \text{cm}$ de altura y con capacidad de $2500\,\text{cm}^{3}$. Encuentre el radio de la base del envase.

Para este caso, estamos buscando el radio del cilindro, para esto podríamos utilizar la fórmula para obtener el volumen de un cilindro, por lo que nuestra primera ecuación sería:
$$
V=\pi r^{2}h
$$
Y ya que sabemos el valor del volumen, entonces nuestra primera ecuación quedaría como:
$$
\pi r^{2}h=2500 \,\text{cm}^{3} \tag{4}
$$
Para nuestra segunda ecuación, solamente debemos de establecer el valor de la altura que ya nos dan:
$$
h=15\,\text{cm}\tag{5}
$$
Ahora planteamos nuestro sistema de ecuaciones:
$$
\begin{cases}
\pi r^{2}h=2500 \\
h=15
\end{cases}
$$
Este sistema es posible de resolver utilizando una sustitución simple:
$$
\begin{gather*}
\pi r^{2}(15)=2500\\r^{2}=\frac{2500}{15\pi}\\
r=\sqrt{ \frac{2500}{15\pi} }\\
\boxed{r=7.284}
\end{gather*}
$$
---

3. En una empresa trabajan 70 personas. Trabajan horas extras el 20% de los hombres y el 10% de las mujeres. Si el número total de personas que hacen horas extras es de 11. ¿Cuántos hombres y mujeres hay en la empresa?

Empezamos definiendo las variables:
$$
\begin{gather*}
\text{Sea } x \text{ la cantidad de hombres en la empresa}\\
\text{Sea }y \text{ la cantidad de mujeres en la empresa}
\end{gather*}
$$
Primeramente se nos es dado que la cantidad total de personas en la empresa es de 70, es decir que la cantidad de hombres y la de mujeres en conjunto da en total 70, es por esto que podemos obtener:
$$
x+y=70\tag{6}
$$
Luego, se nos revela que cierto porcentaje de hombres, más cierto porcentaje de mujeres suman 11 personas, por lo que cambiando estos porcentajes por valores numéricos ($20\%=0.2\quad 10\%=0.1$):
$$
0.2x+0.1y=11\tag{7}
$$
Ya con las ecuaciones definidas, planteamos nuestro sistema:
$$
\begin{cases}
x+y=70 \\
0.2x+0.1y=11
\end{cases}
$$
Despejando $y$ de $(1)$:
$$
y=70-x\tag{8}
$$
Sustituyendo $(8)$ en $(7)$:
$$
\begin{gather*}
0.2x+0.1(70-x)=11\\
0.2x+7-0.1x=11\\
0.1x=11-7\\
x=\frac{4}{0.1}\\
\boxed{x=40}
\end{gather*}
$$
Habiendo obtenido el valor de $x$, podemos sustituirlo en $(8)$ y encontrar el valor de $y$:
$$
\begin{gather*}
y=70-40\\
\boxed{y=30}
\end{gather*}
$$
Por lo que podemos concluir que en la empresa hay 40 hombres y 30 mujeres.

---

4. Si un lado de un triángulo mide una cuarta parte del perímetro, el segundo lado mide 7 metros y el tercer lado mide dos terceras partes del perímetro, ¿Cuál es el perímetro?

Podemos empezar definiendo cada uno de los lados del triángulo:

Para el primer lado se nos dice que su longitud es igual a la cuarta parte del perímetro del triángulo, es decir que podríamos definir al primer lado, siendo $P$ el valor del perímetro, de la siguiente manera:
$$
a=\frac{1}{4}P\tag{9}
$$
El segundo lado ya se nos da el valor, que es 7.
$$
b=7\tag{10}
$$
Para el tercer lado, se nos dice que su longitud mide dos terceras partes del perímetro, es decir:
$$
c=\frac{2}{3}P\tag{11}
$$
ahora podemos plantear el sistema:
$$
\begin{cases}
P=a+b+c \\
a=\frac{1}{4}P \\
b=7 \\
c=\frac{2}{3}P
\end{cases}
$$

> [!info] Sistema "complejo"
> Si bien, el sistema de ecuaciones planteado se ve distinto a lo que hemos visto, en realidad no es nada que no podamos manejar. Después de todo, solo es valor numérico


Haciendo las sustituciones respectivas:
$$
\begin{gather*}
P=\frac{1}{4}P+7+\frac{2}{3}P\\
P=\frac{11}{12}P+7\\
P-\frac{11}{12}P=7\\
\frac{1}{12}P=7\\
\boxed{P=84}
\end{gather*}
$$
Por lo tanto, el valor del perímetro es de 84 m.

---

5. Si cada uno de dos lados opuestos de un cuadrado se duplica y cada uno de los otros lados opuestos se disminuye en 2 pies, el área del nuevo rectángulo resultante supera en 32 pies cuadrados al área del cuadrado original. Encuentre la longitud del lado del cuadrado.

Definimos variables:
$$
\begin{gather*}
\text{Sea }x\text{ el valor del lado original}\\
\text{Sea }y \text{ el valor del lado disminuido} 
\end{gather*}
$$
De esta manera podemos plantear igualdades, primeramente sabemos que el valor de $y$ es el mismo valor de $x$ pero disminuido en 2, es decir:
$$
y=x-2\tag{12}
$$
Para la segunda ecuación, el área resultante de la resta del rectángulo y del cuadrado original es de 32 pies, por lo que si sabemos que el área del rectángulo es: $2xy$ (uno de los lados originales es duplicado y el otro se disminuye en 2, por lo que es igual que $y$), y que el área del cuadrado original es $x^{2}$, entonces nuestra segunda ecuación será:
$$
2xy-x^{2}=32\tag{13}
$$

> [!warning] Orden en la resta
> Es importante resaltar el porque se puso $2xy$ antes del $x^{2}$ para la resta, esto es debido a que el enunciado nos dice que el área del rectángulo **supera** al área del cuadrado en 32 pies, es decir que el área del rectángulo es **mayor** a la del cuadrado, por esto se pone de esta forma, de lo contrario, tendría que definirse la diferencia como un número negativo.

Por lo que el sistema de ecuaciones queda de la siguiente manera:
$$
\begin{cases}
y=x-2 \\
2xy-x^{2}=32
\end{cases}
$$
Ahora haremos la sustitución de $(12)$ en $(13)$:
$$
\begin{gather*}
2x(x-2)-x^{2}=32\\
2x^{2}-4x-x^{2}=32\\
x^{2}-4x-32=0
\end{gather*}
$$
Esta ecuación se puede factorizar de la siguiente manera:
$$
(x+4)(x-8)=0
$$
Por lo que podemos encontrar dos respuestas:
$$
x=-4\qquad x=8
$$
Ya que estamos hablando de longitudes, entonces $x=-4$ no es, debido a que no existe una longitud negativa, por lo que podemos concluir que la longitud de cada lado del cuadrado original es de **8 pies**.
