---
tags:
  - Algoritmos
  - Programacion
---
Analizar por qué combinar dos algoritmos de ordenamiento con complejidades distintas puede ser una decisión razonable en la práctica, y practicar análisis asintótico sobre un algoritmo modificado.

# Índice

1. Repaso teórico
2. Planteamiento del problema
3. Desarrollo guiado
4. Ejercicios evaluados

---
# Teoría

## Repaso teórico

Recordemos un poco los conceptos necesario sobre algoritmos que hemos visto recientemente y es importante tener claros.

### Insertion Sort
- El peor caso de este algoritmo es de $\mathcal{O}(n^{2})$, esto ocurre cuando un arreglo está ordenado de manera invertida.
- Aunque tenga una complejidad cuadrática esta tiene una constante multiplicativa pequeña debido a la poca cantidad de operaciones por comparación, una buena localidad en el caché y no tiene un overhead (costo) de llamadas recursivas.
- Para valores pequeños de $n$, la constante de insertion sort puede pesar más que el exponente cuadrático en su complejidad. Por lo que en ciertas ocasiones puede ser ganarle a algunos algoritmos con complejidades asintóticas menores.

### Merge Sort
- El peor caso de este algoritmo es de $\mathcal{O}(n\log n)$, gracias a su recurrencia.
- El costo $\mathcal{O}(n)$ por nivel, viene del proceso de hacer el *merge* al combinar las dos sub-listas ordenadas de tamaño total $m$ en una sola lista ordenada toma $\mathcal{O}(m)$.
- La recursión llega hasta subproblemas de tamaño $1$ el cual es el caso base trivial.
El pseudocódigo de merge sort es el siguiente:
![[Pasted image 20260906194233.png|center]]
![[Pasted image 20260906194300.png|center]]

---

## Planteamiento del problema

El libro: *Introduction to algorithms* plantea en el problema 2-1 lo siguiente:
El algoritmo de merge sort original se ve alterado de la siguiente manera: En vez de hacer la recursión hasta el caso trivial (con solo un dato), se divide el arreglo de tamaño $n$ en $n/k$ sub-listas de tamaño $k$, cada una de estas sub-listas se ordena con insertion sort y luego se mezclan todas usando el mecanismo estándar de merge sort.

El ejercicio pide analizar:
1. Mostrar que insertion sort puede ordenar las $n/k$ sub-listas, cada una de tamaño $k$, en tiempo $\mathcal{O}(nk)$ en el peor caso.
2. Mostrar cómo mezclar las sublistas en tiempo $\mathcal{O}\left( n\log \frac{n}{k} \right)$ en el peor caso.
3. Dado que el algoritmo modificado corre en $\mathcal{O}\left( nk+n\log \frac{n}{k} \right)$ en el peor caso, ¿Cuál es el mayor valor de $k$ en función de $n$ para el cual el algoritmo modificado tiene la misma complejidad que el merge sort estándar?
4. ¿Cómo se debería elegir $k$ en la práctica?

---

## Desarrollo guiado

### Tiempo de insertion sort
Insertion sort sobre una sola lista de tamaño $k$ toma $\mathcal{O}(k^{2})$ en el peor caso. Para el algoritmo modificado existen $n/k$ sub-listas, por lo que el tiempo total es:
$$
\left( \frac{n}{k} \right) \cdot \mathcal{O}(k^{2}) =\mathcal{O}(nk)
$$
### Tiempo de mezcla
Una vez ordenadas las $n/k$ sub-listas de tamaño $k$, debemos mezclarlas de la misma manera que con merge sort de toda la vida: Combinándolas de dos en dos, luego estos resultados de dos en dos y así de manera sucesiva hasta terminar todo la lista.

- Al empezar con $n/k$ sub-listas en vez de los $n$ elementos individuales significa que ahora tenemos $\log \frac{n}{k}$ niveles de mezcla (en vez de $\log n$).
- Cada nivel de mezcla, sin importar cuántas sub-listas se estén combinando, procesa un total de $n$ elementos por nivel, haciendo que cueste $\mathcal{O}(n)$,
- En total, tenemos $\mathcal{O}(n)$ por nivel multiplicado por $\log \frac{n}{k}$ niveles $=\mathcal{O}\left( n\log \frac{n}{k} \right)$.

### Máximo valor de $k$
El algoritmo modificado corre en $\mathcal{O}\left( nk+n\log \frac{n}{k} \right)$. Nos conviene expandir el segundo término:
$$
n\log \frac{n}{k} = n\log n - n\log k
$$
Por lo que el tiempo total es de:
$$
\mathcal{O}(nk+n\log n-n\log k)
$$
Ya que queremos llegar a $\mathcal{O}(n\log n)$ de la misma manera que con merge sort y teniendo en cuenta que el término $n\log n$ ya está presente y que el término $-n\log k$ es de orden menor o igual y no afecta el análisis asintótico hacia arriba. Entonces el término que sí podría dominar y arruinar la complejidad es $nk$.
Por lo que si no queremos que $nk$ nos arruine lo que tenemos, debemos de:
$$
nk=\mathcal{O}(n\log n)\iff k=\mathcal{O}(\log n)
$$
Por lo tanto, el mayor valor de $k$ (en función de $n$) para el cual el algoritmo modificado mantiene la misma complejidad $\mathcal{O}(n\log n)$ que el merge sort normal es:
$$
k=\mathcal{O}(\log n)
$$


### Elección de $k$ en la práctica
El análisis asintótico dice que $k$ puede llegar a crecer hasta $\mathcal{O}(\log n)$ sin que cambie la complejidad, pero no explica cuál es el valor concreto que debe de tomar $k$. Esto dependerá de las constantes reales de la implementación que varían de una máquina y de un compilador a otro.

En la práctica $k$ se determina de forma empírica, se suele probar el algoritmo híbrido con distintos valores de $k$ sobre entradas representativas, se mide el tiempo real de la ejecución y se elige el valor de $k$ que dio mejores resultados. No tomamos $k=\log n$ ya que esto crece muy lentamente y en la práctica el valor óptimo suele ser una constante fija razonablemente pequeña.


---

# Ejercicios evaluados

**Ejercicio 1 - Generalizando el umbral**
Suponga que en vez de usar un número fijo $k$ como una constante o como $\mathcal{O}(\log n)$, sino que definimos $k=\sqrt{ n }$. Determine la complejidad del algoritmo híbrido en este caso y explique si es que insertion sort sigue siendo viable de utilizar con este tamaño de sublista.

**Pistas**
- Sustituye $k=\sqrt{ n }$ directamente en $\mathcal{O}\left( nk+n\log \frac{n}{k} \right)$ y simplifique cada término por separado.
- Compare el resultado contra $\mathcal{O}(n\log n)$. ¿El término $nk$ sigue siendo de orden menor, igual o mayor?
- La conclusión debe conectarse con el apartado **Máximo valor de $k$**. ¿Qué tan cerca o lejos está $\sqrt{ n }$ del límite $\mathcal{O}(\log n)$ que se encontró?

**Ejercicio 2 - Implementación y medición empírica**
Implemente el algoritmo híbrido descrito en el problema en c++. Luego, mida el tiempo de ejecución para un arreglo grande (podría ser $n=1,000,000$ elementos generados aleatoriamente) probando distintos valores de $k$ ($1,2,4,8,16,32,64,128$), y determine empíricamente cuál $k$ da el mejor rendimiento en su computadora.

**Pistas:**
- $k=1$ debería comportarse igual que un merge sort estándar. Úselo como un punto de referencia.
- Use `<chrono>` para medir el tiempo de ejecución de forma precisa (observe el ejemplo más abajo)
- Grafique (de la forma qué prefiera) tiempo vs $k$. Se debería poder apreciar una curva que mejora hasta cierto punto y luego empieza a empeorar.

*Ejemplo de uso de `crhono`*
```cpp
#include <iostream>
#include <chrono>
using namespace std;
using namespace std::chrono;

int main() {
	auto inicio = high_resolution_clock::now();
	
	algoritmo(); //Lo que se quiera medir
	
	auto fin = high_resolution_clock::now(); 
	auto duracion = duration_cast<microseconds>(fin - inicio);
	
	cout << "Tiempo: " << duracion.count() << " us" << endl;
	
	return 0;
}
```
