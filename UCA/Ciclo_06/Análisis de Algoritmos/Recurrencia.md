---
tags:
---
## Definiendo valores

Primeramente, partimos que tenemos una ecuación de recurrencia con una forma general de la siguiente forma:
$$
T(n)=aT\left( \frac{n}{b} \right)+f(n)\tag 1
$$
Donde:
- $T(n)$ es la complejidad de tiempo del algoritmo
- $a$ es la cantidad de llamadas recursivas del algoritmo
- $n/b$ es la cantidad de datos que se envía en la llamada recursiva
- $f(n)$ es la eficiencia del resto de código
Con estos valores es con los cuales vamos a construir el árbol para poder encontrar la complejidad temporal del algoritmo.

## Creando árboles

Con los valores de las variables de la ecuación $(1)$, estos nos guiarán y darán las instrucciones con las que podremos construir nuestro árbol, de la siguiente manera:
- $a$ es la cantidad de hijos que tendrán cada nodo
- $n/b$ (sin muchos cambios cono su definición) representa la cantidad de datos que pasa por el nodo actual
- $f(n)$ es lo que le ocurrirá a los datos en el nodo 

## Ejemplo

Busquemos encontrar la complejidad temporal del algoritmo **Merge Sort**, que sabemos que tiene una complejidad dada por la expresión:
$$
T(n)=2T\left( \frac{n}{2} \right) +O(n)
$$
De esta expresión sabemos:
- $a=2$, cada nodo del árbol tendrá 2 nodos, es decir que será un árbol binario.
- $\frac{n}{2}$ será la cantidad de información que se transmitirá en cada nodo
- $O(n)$ es lo que le ocurre a los datos dentro de cada nodo.

Ya conociendo lo anterior, formemos el árbol:

![[Pasted image 20250912175220.png|center|600]]


Principalmente, tenemos el nodo base, que contiene la totalidad de la información, luego se divide en dos ramas el primer nodo, que da a cada uno de los hijos la mitad de su información 