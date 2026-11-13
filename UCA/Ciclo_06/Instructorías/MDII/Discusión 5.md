---
date: 2025-09-25
---
# Axiomas de Kolmogorov

> [!NOTE] Axiomas generales de probabilidad
> Si se tiene un espacio muestral $S$, una **función de probabilidad** $P$ cuyo dominio son todos los eventos contenidos en $S$ y su rango es el conjunto de los números reales $\mathbb{R}$ TIENE que cumplir con los siguientes axiomas:
> 
> Para todos los eventos $A$ y $B$ contenidos en $S$:
> 1. $$0 \leq P(A) \leq 1$$
> 2. $$P(\varnothing)=0 \quad \text{\&}\quad  P(S)=1$$
> 3. Si $A \cap B=\varnothing$, entonces la probabilidad de la unión de $A$ y $B$ es is $$P(A\cup B)=P(A)+P(B)$$

## Demostración de la unión de dos eventos
Conocemos que si dos eventos $A$ y $B$ son mutuamente disjuntos, entonces $P(A\cup B)=P(A)+P(B)$. Esto es por axioma. Pero si sabemos que $A$ y $B$ tienen elementos en común, es decir, que la intersección de $A$ y $B$ no es el conjunto vacío, entonces no podemos usar el tercer axioma directamente.

Sin embargo, lo que se puede hacer es tomar los conjuntos que tenemos y separarlos en conjuntos que sí son mutuamente disjuntos.

![[Pasted image 20250926134510.png]]

De esta forma tenemos tres conjuntos que son mutuamente disjuntos: $A-B$, $A\cap B$ y $B-A$. Y, una cosa que podemos notar observando el diagrama de Venn, es lo siguiente:
- $A-B=A-(A\cap B)$
- $B-A=B-(A\cap B)$

De aquí, entonces obtenemos que $A\cup B =A-(A\cap B)+B-(A\cap B)+(A\cap B)$. Entonces, sacando $P(A\cup B)$:
$$\begin{align}
P(A\cup B) &=P(A)-P(A\cap B)+P(B)\cancel{ -(A \cap B)+(A \cap B) } \\
&= P(A) -P(A\cap B)+P(B) \\
&= P(A)+P(B)-P(A\cap B)
\end{align}$$
Es de esta forma que obtenemos la fórmula que conocemos por medio del principio de inclusión-exclusión.

---
## Ejercicios de práctica

> [!example] Ejercicio 1

Suponga que tenemos tres eventos, $A$, $B$ y $C$, que son mutuamente disjuntos en el espacio muestral $S$. En este espacio muestral se cumple lo siguiente:
- $S=A\cup B\cup C$
- $P(A)=0.3$
- $P(B)=0.5$

¿Cuánto es $P(A\cup B)$? ¿Es posible que $P(C)=0.1$? ¿Cuánto es $P(C)$?

> [!check] Solución
> - Ya que sabemos que $A$ y $B$ son eventos mutuamente disjuntos, por el tercer axioma sabemos que $P(A\cup B)=P(A)+P(B)=0.3+0.5=0.8$.
> - No es posible que $P(C)=0.1$ dado que $P(S)=1$ y que $S=A\cup B\cup C$. Asumiendo que $P(C)=0.1$, observamos que $P(A\cup B\cup C)=0.3+0.5+0.1=0.9 \neq 1$.
> - Entonces, para este caso, $P(C)$ tiene que ser igual a $0.2$.

---

> [!example] Ejercicio 2

Suponga que tenemos dos eventos, $A$ y $B$, en un espacio muestral $S$. Se sabe que $P(A)=0.8$ y que $P(B)=0.7$, y también que $P(A\cap B)=0.6$. ¿Cuál es el valor de $P(A\cup B)$?

> [!check] Solución
> - Aquí no se estableció que $A$ y $B$ son mutuamente disjuntos. Incluso aún, conocemos que $P(A\cap B)=0.6$, que es diferente de cero. Entonces, tenemos que usar la fórmula del principio de inclusión exclusión: $$\begin{align} P(A\cup B)&=P(A)+P(B)+P(A\cap B) \\ &=0.8+0.7-0.6 \\ &=0.9 \end{align}$$

---

> [!example] Ejercicio 3

Suponga que tenemos dos evento, $A$ y $B$, en un espacio muestral $S$. También, suponemos que $P(A)=0.6$, $P(B^{c})=0.4$ y que $P(A\cap B)=0.2$. ¿Cuál es el valor de $P(A\cup B)$?

> [!check] Solución
> Recordando, $B^{c}$ significa el complemento de $B$, que escrito en otra forma es $S-B$. Entonces, $P(B^{c})=P(S)-P(B)$. Pero, el complemento del complemento es el mismo resultado que $B$, por doble negación. 
> Entonces, para obtener $P(B)$ se realiza $P(S)-P(B^{c})=1-0.4=0.6$. Ahora que se sabe que $P(B)=0.6$, se utiliza la fórmula de principio de inclusión-exclusión para calcular la respuesta: $$P(A\cup B)=0.6+0.6-0.2=1$$

---

> [!example] Ejercicio 4

Suponga que tenemos dos eventos, $U$ y $V$, en un espacio muestral $S$. También, suponemos que $P(U^{c})=0.3$, $P(V)=0.6$ y que $P(U^{c}\cup V^{c})=0.4$. ¿Cuál es el valor de $P(U\cup V)$?

> [!check] Solución
> - Por ley de D'Morgan, se sabe que $U^{c}\cup V^{c}$ es equivalente a $(U\cap V)^{c}$.
> - Entonces, $P((U\cap V)^{c})=0.4$, por lo que $P(U\cap V)=1-0.4=0.6$.
> - Además, $P(U)=1-0.3=0.7$.
> - Por lo tanto: $$P(U\cup V)=0.7+\cancel{ 0.6-0.6 }=0.7$$

---

> [!example] Ejercicio 5

Sean $A$ y $B$ eventos de un espacio muestral $S$, y sea $C=S-(A\cup B)$. Suponga que $P(A)=0.4$, $P(B)=0.5$ y que $P(A\cap B)=0.2$. Encontrar:

| - $P(A\cup B)$<br>- $P(C)$<br>- $P(A^{c})$ | - $P(A^{c}\cap B^{c})$<br>- $P(A^{c}\cup B^{c})$<br>- $P(B^{c}\cap C)$<br> |
| ------------------------------------------ | -------------------------------------------------------------------------- |

> [!check] Solución
> - $P(A\cup B)=0.4+0.5-0.2=0.7$
> - $P(C)=P(S)-P(A\cup B)=1-0.7=0.3$
> - $P(A^{c})=P(S)-P(A)=1-0.4=0.6$
> - $P(A^{c}\cap B^{c})=P((A\cup B)^{c})=1-P(A\cup B)=1-0.7=0.3$
> - $P(A^{c}\cup B^{c})=P((A\cap B)^{c})=1-0.2=0.8$
> 
> Estos son relativamente sencillos, pero el sexto puede ser un poco confuso, así que podemos guiarnos con un diagrama de Venn.
> 
> ![[Pasted image 20250926142845.png]]
> 
> A manera de fórmula, despejamos la fórmula original para obtener el valor de la intersección: $$\begin{align*} P(B^{c}\cup C) &= P(B^{c})+P(C)-P(B^{c}\cap C) \\ P(B^{c}\cup C)+ P(B^{c}\cap C) &= P(B^{c})+P(C)\\ P(B^{c}\cap C) &= P(B^{c})+P(C)-P(B^{c}\cup C) \end{align*}$$
> Entonces, conocemos $P(B^{c})=P(A)-P(A\cap B)+P(C)$, $P(C)$ y observando el diagrama podemos verificar que $B^{c}\cup C=B^{c}$ , así que $P(B^{c}\cup C)=P(B^{c})$. Usando la fórmula que obtuvimos:
> - $P(B^{c}\cap C)=(1-0.5)+(0.3)-(1-0.5)=0.3$

---
# Probabilidad condicional
La probabilidad condicional es una forma de obtener la probabilidad de una situación ocurrido que este evento sea el resultado de otro evento. 

Si tenemos dos eventos $A$ y $B$ en un espacio muestral $S$, un experimento puede ser parte de los resultados contenidos en $A$, o de los contenidos en $B$, o que pertenezca a ambos, $A\cap B$.
La probabilidad condicional calcula la probabilidad de uno de los eventos, dado que también pertenece al otro evento. Entonces, por probabilidad condicional, se tiene que: $$P(B | A)=\frac{P(A\cap B)}{P(A)}$$
$P(B|A)$ se lee como la probabilidad de $B$ dado $A$, y vemos que en la fórmula tiene sentido. Estamos calculando la probabilidad de que un evento pertenezca a $B$ entendiendo que este también corresponde a $A$; y la única forma en que esto ocurra es que el evento corresponda a $A\cap B$.

La dificultad de los ejercicios de probabilidad condicional está en la comprensión lectora, en interpretar cuáles son los eventos de los que se quiere obtener la probabilidad condicional.

---
## Ejercicios de práctica

> [!example] Ejercicio 6

El instructor de una clase de matemática discreta II calificó dos evaluaciones que se realizaron y observó lo siguiente:
- El 25% de los estudiantes obtuvo más de 9 en la primera evaluación,
- El 15% de los estudiantes obtuvo más de 9 en ambas evaluaciones.

¿Cuál es el porcentaje de los estudiantes que recibieron más de 9 en la primera evaluación obtuvo más de 9 en la segunda evaluación?


> [!check] Solución
> Prestar atención, no estamos hablando del 15% de todos los estudiantes. Estamos preguntando qué proporción de los que sacaron más de 9 en la primera evaluación sacó más de 9 en la segunda. Es decir, estamos sacando el porcentaje del 25% que aprobó.
> 
> Sacando los eventos:
> - $A$ es el evento de obtener más de 9 en la primera evaluación.
> - $B$ es el evento de obtener más de 9 en la segunda evaluación.
> - $B|A$ es sacar más de 9 en la segunda evaluación, dado que sacaron más de 9 en la primera.
> - $A\cap B$ es sacar más de 9 en ambas evaluaciones.
>   
>  $$P(B|A)=\frac{P(A\cap B)}{P(A)}=\frac{0.15}{0.25}=0.6$$
>  Es decir, del 25% de los estudiantes que sacaron más de 9 en la primera evaluación, el 60% de esos sacó más de 9 en ambas evaluaciones.

---

> [!example] Ejercicio 7

Suponga que $A$ y $B$ son eventos de un espacio muestral $S$ y que los valores de $P(A)$, $P(B)$ y $P(A|B)$ son conocidos. Derivar una fórmula para obtener $P(A|B^{c})$.

> [!check] Solución
> Por fórmula, podemos observar que: $$P(A|B^{c})=\frac{P(A\cap B^{c})}{P(B^{c})}$$
> Usando un diagrama de Venn:
> 
> ![[Pasted image 20250926151445.png]]
> 
> Observamos que $A\cap B^{c}=A-(A\cap B)$. Otra forma de justificarlo es que $(A\cap B)\subseteq B$, por lo tanto $A\cap B^{c}$ tendría que ser las partes de $A$ que no están relacionadas con $B$. De esta forma: $$\begin{align} P(A|B^{c}) &= \frac{P(A\cap B^{c})}{P(B^{c})} \\ &= \frac{P(A)-P(A\cap B)}{1-P(B)} \end{align}$$
> Sin embargo, no conocemos $A\cap B$; así que este se obtiene de despejar la fórmula de la probabilidad condicional: $$P(A|B)=\frac{P(A\cap B)}{P(B)} \implies P(A\cap B)=P(A|B)\cdot P(B)$$
> Por lo tanto, la fórmula final es: $$P(A|B^{c})=\frac{P(A)-P(B)\cdot P(A|B)}{1-P(B)}$$

---

> [!example] Ejercicio 8

Una urna contiene 25 bolas rojas y 15 bolas azules. Dos bolas son elegidas al azar, una después de la otra, sin regresarlas a la urna.

Usar un árbol de probabilidades para calcular las siguientes probabilidades:

- La probabilidad de que ambas bolas sean rojas.
- La probabilidad de que la primera bola sea roja, y la segunda no.
- La probabilidad de que la primera bola no sea roja, y que la segunda sí.
- La probabilidad de que ni la primera ni la segunda bola sean rojas.


> [!success] Solución
>Para poder completar el ejercicio, dibujemos el árbol de posibilidades:
![[PosibilityTree|center]]
>Este árbol se obtiene sabiendo que al inicio tenemos un total de 40 bolas (25 rojas + 15 azules), luego debemos conocer la posibilidad de que la primera pelota sea roja. Usando la fórmula de Laplace (casos favorables / casos posibles), sabemos que en el primer intento, tenemos una probabilidad de $5/8$ de obtener una bola roja. Luego en el segundo intento, ya que se saco una bola **roja**, entonces se resta una a la cantidad de bolas rojas y a su vez se resta una a la cantidad de bolas totales, por lo que para el segundo intento, la probabilidad de obtener una bola roja es de $8/13$, por lo que para obtener la probabilidad de que ambas sean rojas:
> $$
 P(A)=\frac{5}{8}\cdot \frac{8}{13}=\frac{5}{13}
> $$
> 
> Para el literal **b**, empezamos con la misma probabilidad de obtener una bola roja ($5/8$). Pero en el segundo intento, tenemos que saber la probabilidad de obtener una bola azul, ya que ya habíamos sacado una bola anteriormente, entonces la probabilidad es de $5/13$.
> Obteniendo la probabilidad total:
> $$
 P(B)=\frac{5}{8}\cdot \frac{5}{13} = \frac{25}{104}
>$$
>
> Con el literal **c** cambia un poco, y es que ahora tendremos que buscar cuál es la probabilidad de obtener en el primer intento una bola azul, que si vemos el árbol de posibilidades, sabemos que es de $3/8$, para el segundo intento, debemos encontrar la probabilidad de encontrar una bola roja, en este caso, no se le resta a las bolas rojas (ya que no sacamos ninguna roja, duh) por lo que su probabilidad es de $25/39$, obteniendo una probabilidad de :
> $$
 P(C)=\frac{3}{8} \cdot \frac{25}{39}= \frac{25}{104}
>$$
>
> Finalmente, para encontrar la probabilidad de obtener dos veces un azul; Ya que conocemos la probabilidad de obtener una azul en el primer intento ($3/8$), solo debe de multiplicarse por la probabilidad de sacar una segunda bola azul es de $14/39$, por lo que la probabilidad final es de:
> $$
> P(D)=\frac{3}{8} \cdot \frac{14}{39} = \frac{7}{52}
>$$





