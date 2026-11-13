Entender como funciona internamente una tabla hash, implementar una versión propia, y reconocer patrones de problemas donde una tabla hash convierte una solución $\mathcal O (n^{2})$ en una $\mathcal O (n)$.

# Índice
1. Repaso teórico
2. Implementación en C++
3. Ejercicios evaluados


---
# Teoría

## 1. Repaso teórico

### ¿Para qué?
Los arreglos y los vectores dan un acceso $\mathcal O(1)$ pero solamente si el índice es un número pequeño conocido. En cambio, una tabla hash permite generalizar esta idea permitiendo acceso $\mathcal O(1)$ *esperado* usando como "índice" prácticamente cualquier tipo de clave. mapeándolas en un arreglo interno mediante una función hash.

### ¿Qué es una función hash?
Una función hash `h(clave)` convierte una clave en un índice dentro del rango `[0, m-1]` donde `m` es el tamaño del arreglo interno (llamado comúnmente como buckets).
Las funciones hash (porque no hay una sola) deseablemente deben poseer las siguientes propiedades:
- **Determinista:** La misma clave siempre produce el mismo índice
- **Rápida de calcular:** No debe costar más que el resto de la operación
- **Distribución uniforme:** Claves distintas deben repartirse parejo entre los buckets, para minimizar coalisiones

Una función hash simple para trabajar con enteros es la función módulo: `h(k)=k % m`. Para strings, usualmente se suele acumular un valor numérico carácter por carácter y luego aplicar `% m`.

### ¿Qué son las colisiones?
Usualmente la cantidad de claves posibles suele ser superior a `m`, (jumpscare) que por principio de palomar es inevitable que dos claves distintas mapeen al mismo índice, a esto se le considera una colisión. Existen dos estrategias estándar para poder resolverlas:
1. **Encadenamiento:** Cada uno de los buckets guarda una lista (o una lista enlazada) de todos los pares clave-valor que tienen el índice. Insertar y buscar implicar recorrer la lista.
```
bucket 0 -> (k1, v1) -> (k5, v5)
bucket 1 -> (vacío)
bucket 2 -> (k3, v3)
```
2. **Direccionamiento abierto:** Sin un bucket ya se encuentra ocupado, se prueba con otro bucket siguiendo una secuencia determinada: lineal (la siguiente casilla), cuadrático, o doble hashing (una segunda función hash para el salto). No se usan otras listas, todo vive en el mismo arreglo.

Para este laboratorio nos centraremos en lo que sería el encadenamiento, ya que es más simple de implementar correctamente y conecta con lo que hemos visto anteriormente con structs autoreferenciados.

### Factor de carga y complejidad
El factor de carga es $\alpha=\frac{n}{m}$, donde $n$ es el número de elementos almacenados y $m$ el número de buckets. Con una función hash razonable y un $\alpha$ acotado, el tiempo de inserción, búsqueda y eliminación es $\mathcal O(1)$.
Sin embargo, debido al comportamiento por encadenamiento de la hash table, es importante recalcar que:

| Caso                                                        | Tiempo          |
| ----------------------------------------------------------- | --------------- |
| Caso esperado (Una buena función hash, $\alpha$ es acotado) | $\mathcal O(1)$ |
| Peor caso (todas las claves colisionan en el mismo bucket)  | $\mathcal O(n)$ |

---

## Implementación en C++

### Estructura básica con ordenamiento

```cpp
struct Nodo {
	string clave;
	int valor;
	Nodo* siguiente;
};

class HashTable{
private:
	vector<Nodo*> buckets;
	int m;
	
	int hash(const string& clave) {
		long h = 0;
		for (char c : clave) h = (h * 31 + c) % m;
		//nuestra función hash tomará el valor actual de h, lo multiplicará
		//por 31, le sumará el valor ascii del caracter actual y obtendrá el
		//módulo de m, esto por cada uno de los caracteres en el string
		return h;
	}  
	
public:
	HashTable(int size) : m(size) {
		buckets.assign(m, nullptr);
	}
	
	void insert(const string& clave, int valor) {
		int idx = hash(clave);
		Nodo* actual = buckets[idx];
		while (actual != nullptr) {
			if (actual->clave == clave) {actual->valor = valor; return;}
			actual = actual->siguiente;
		}
		Nodo* nuevo = new Nodo{clave, valor, buckets[idx]};
		buckets[idx] = nuevo;
	}
	
	bool buscar(const string& clave, int& valorOut) {
		Nodo* actual = buckets[hash(clave)];
		while (actual != nullptr) {
			if (actual->clave == clave) {valorOut = actual->valor; return true; }
			actual = actual->siguiente;
		}
		
		return false;
	}
}
```


> [!important] Implementación de la Hash Table
> En la práctica, casi nunca se implementa una hash table desde 0, C++ ya nos ahorra eso ofreciéndonos `unordered_map<Clave, valor>` y `unordered_set<Clave>`, con inserción, búsqueda y eliminación en $\mathcal O(1)$ esperado. El propósito de implementarla a mano, es entender como funcionan y poder razonar sobre su complejidad. 

---

# Ejercicios Evaluados

### Ejercicio 1 - Elemento duplicado

Dado un vector de enteros, determina si existe algún valor repetido, en tiempo O(n) usando una tabla hash.

```
Entrada:  {4, 2, 7, 2, 9}
Salida:   true   (el 2 está repetido)

Entrada:  {1, 2, 3, 4}
Salida:   false
```

**Pistas:**

- Recorre el vector una sola vez, insertando cada valor en la tabla hash antes de seguir.
- Antes de insertar un valor, pregúntate: ¿ya está en la tabla?

### Ejercicio 2 - Two Sum

Dado un vector de enteros `v` y un objetivo `t`, encuentra los índices `i, j` (con `i != j`) tales que `v[i] + v[j] == t`, en tiempo O(n).

```
Entrada:  v = {2, 7, 11, 15}, t = 9
Salida:   {0, 1}   (v[0] + v[1] = 2 + 7 = 9)
```

**Pistas:**

- Por cada elemento `v[i]`, calcula el complemento `t - v[i]` y pregunta si ese complemento ya está en la tabla hash _antes_ de insertar `v[i]`.
- Guarda en la tabla hash no solo el valor sino también su índice (clave = valor, valor = índice).
- Esto evita el enfoque de doble bucle O(n²) que sería la primera idea intuitiva.

### Ejercicio 3 - Agrupar anagramas

Dado un vector de strings, agrupa las palabras que son anagramas entre sí (mismas letras, distinto orden), usando una tabla hash.

```
Entrada:  {"ojo", "amor", "joo", "roma", "gato"}
Salida:   [["ojo", "joo"], ["amor", "roma"], ["gato"]]
```

**Pistas:**

- Dos palabras son anagramas si, al ordenar sus letras, quedan idénticas.
- Usa la versión ordenada de cada palabra como **clave** de la tabla hash, y guarda en el valor la lista de palabras originales que comparten esa clave.
- Este ejercicio es un buen ejemplo de que la clave de una tabla hash no tiene que ser el dato "tal cual" — puede ser cualquier propiedad derivada que agrupe correctamente.