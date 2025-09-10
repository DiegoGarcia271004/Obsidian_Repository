# Introducción al conteo y probabilidad
---
Autores:
- Diego Benjamín García Alfaro
- Mauricio Alejandro Montes Varela

## Probabilidad
La probabilidad es una rama de la matemática muy importante, que a nivel básico estudia la proporción que hay entre la ocurrencia de un evento aleatorio y el resto de posibilidades que se encuentran en el experimento. Muchas de las cosas que se hacen con probabilidad están relacionadas con los métodos de conteo, por lo que es algo que hay que tener bien fundamentado.

Una de las aplicaciones más comunes para la probabilidad es en la estadística inferencial, una rama muy usada de las matemáticas dada su capacidad de realizar predicciones.
### Conceptos básicos
Cómo es normal en la matemática, hay que tener claro varios conceptos. Estos han sido definidos rigurosamente, y es en estos que se apoyan los teoremas. Primeramente, conjuntos.

- **Proceso aleatorio.**
  Se dice que un proceso es *aleatorio* cuando, realizar dicho proceso garantiza que un resultado dentro de un conjunto de todos los posibles resultados va a ocurrir; sin embargo, no se sabe con certeza cuál será el resultado. 
  Por ejemplo, tirar una moneda. Sabemos que la moneda tiene dos posibles resultados: **Cara o Cruz**. Tirar la moneda es un resultado aleatorio porque, si bien sabemos que la moneda será o **cara** o **cruz**, *no sabemos exactamente si será cara o cruz*.
  
- **Experimento.**
  Un experimento es un conjunto de procesos aleatorios realizados. Dado que estos procesos ya fueron realizados, el resultado de los procesos aleatorios es conocido. También puede ser la acción de realizar varios procesos aleatorios, usualmente una cantidad finita.
  
- **Espacio muestral.** 
  En inglés llamado "sample space", razón por la cual se suele representar con $S$, es un conjunto. Este conjunto engloba todos los resultados que un **evento aleatorio** pueda generar. 
  En el caso de tirar la moneda, el *espacio muestral solo es cara o cruz*. Lanzar un dado genera un *espacio muestral con los valores 1, 2, 3, 4, 5 y 6.* Formalmente, el espacio muestral es $S=\{ 1,2,3,4,5,6 \}$.
  
- **Evento.**
  Un evento es otro conjunto. Un subconjunto del espacio muestral representado por $E$. Este conjunto contiene los resultados que deseamos obtener. Si tiro un dado y espero obtener un número par, *el espacio muestral sigue siendo 1, 2, 3, 4, 5 y 6* pero *el evento solo contiene 2, 4 y 6.*
  En sus formas de conjunto, $S=\{ 1,2,3,4,5,6 \}$ y $E=\{ 2,4,6 \}$.
  
- **Probabilidad.**
  Es una proporción, razón, ratio. Se dice que la *probabilidad* de un **evento**, representado como $P(E)$, es la razón que hay entre **la cardinalidad del evento** y **la cardinalidad del espacio muestral**.
  
- **Cardinalidad.**
  Es la cantidad de elementos que tiene un conjunto. El espacio muestral de tirar un dado es de 1, 2, 3, 4, 5, 6. Es decir: $S=\{ 1,2,3,4,5,6 \}$. Entonces, la cardinalidad del espacio muestral es $N(S)=6$.


> [!important] Fórmula de Probabilidad
> $$P(E)=\frac{N(E)}{N(S)}$$


---
## Ejercicios

> [!example] Ejercicio 9.1.11
> Suponga que una moneda es tirada tres veces, y la cara que se observa es anotada por cada lanzamiento. Asumimos que en cada lanzamiento, cara o cruz son igualmente probables. Cara (Head) es representado por $H$, y Cruz (Tail) es representado por $T$. Siguiendo esta notación, la secuencia $HTT$ indica que el primer lanzamiento fue cara, y los otros dos lanzamientos fueron cruz.
> 
> - Lista los ocho elementos que conforman el espacio muestral del experimento planteado.
> - Escribe los siguientes eventos en su forma de conjunto y encuentra su probabilidad.
>   1. El evento de que cara salga **solo una vez**.
>   2. El evento de que cara salga **al menos dos veces**.
>   3. El evento de que cara **no haya salido**.


> [!example] Ejercicio 9.1.16
> Dos caras de un dado de seis caras están pintadas de rojo, otras dos de verde, y las restantes de azul. El dado es lanzado tres veces, y en cada lanzamiento se anota el color de la cara que mira hacia arriba. Puesto que todos los colores tienen el mismo número de caras, se asume que todos los resultados son igualmente probables.
> 
> - Lista los 27 posibles resultados.
> - Considere el evento en que los tres lanzamientos resultan en tres colores diferentes. Lista todos los resultados contenidos en este evento. ¿Cuál es su probabilidad?
> - Considere el evento en que se obtiene dos veces un mismo color. Liste todos los posibles resultados contenidos por el evento, y calcule su probabilidad.


> [!example] Ejercicio 
> Una urna contiene dos bolas azules ($B_{1}$ y $B_{2}$ respectivamente), y una bola blanca ($W$). Se saca una bola de la urna, se anota su color, y se devuelve. Luego, se saca otra bola de la urna y se anota su color. Dado que las bolas se retornan a la urna, todos los resultados son igualmente probables.
> - Liste los nueve posibles resultados.
> - Considere el evento de que las dos bolas sacadas hayan sido azules. Liste todos los posibles resultados y calcule su probabilidad.
> - Considere el evento de que una bola haya sido azul, y la otra blanca. Liste todos los posibles resultados y calcule su probabilidad.
