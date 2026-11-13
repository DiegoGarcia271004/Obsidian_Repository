---
tags:
  - Algoritmos
  - Programacion
---
El objetivo de esta guía es permitir a los estudiantes de la materia de Análisis de algoritmos recordar conceptos y sintaxis de código en el lenguaje c++ que serán útiles para aplicar los algoritmos vistos en clase en código.

# Índice

1. Sintaxis básica de c++ (Repaso)
2. Condicionales (Repaso)
3. Funciones (Repaso)
4. Loops
5. Arrays / Vectores
6. Punteros
7. Recursión
8. Clases y structs
9. Actividad evaluada
---

# Teoría
## Sintaxis básica de c++ (Repaso)

### Tipos de datos

Existen distintos tipos de datos en c++, entre estos podemos encontrar:
- `int`: Es el tipo de dato utilizado para representar números enteros, permite expresar números en el rango $[-2^{31}, 2^{31}]$.
- `double` y `float`: Son los tipos de datos utilizados para representar número decimales, la principal diferencia entre ellos es la precisión, mientras que `float` usa 4 bytes de memoria permitiendo poseer una precisión de 7 dígitos; `double` ocupa 8 bytes de memoria, proporcionando una precisión de hasta 15 dígitos.
- `string` y `char`: Son tipos de datos que permiten almacenar caracteres, `char` solo permite almacenar un solo carácter por ejemplo: `'a'`. c++ internamente trabaja los `string` como un arreglo de caracteres. Cabe aclarar que `string` no es un dato nativo de c++ sino un objeto de la clase `std::string` por lo que si se quiere usar sin el `std::` al inicio se debe declarar al inicio del archivo un `using namespace std;`.  
- `bool`: Es el tipo de dato que representa valores booleanos (`true` y `false`).

*Ejemplo:*
```cpp
using namespace std;

int a = 42;
double b = 3.1415926535;
float c = 6.022;
char d = '.';
string e = "bruh";
bool f = true;
```

---
## Condicionales (Repaso)

Los condicionales permiten evaluar una proposición y en el caso que sea verdadera ejecutará lo que está en el cuerpo del condicional.

*Ejemplo:*
```cpp
if (a>b) {
	cout<<"a es mayor que b" << endl;
} else if(a == b) {
	cout<<"a es igual a b" << endl;
} else {
	cout<<"a es menor que b" << endl;
}
```

---
## Funciones (Repaso)

Las funciones son bloques de código reutilizables que realizan una tarea específica, permitiendo ordenar el código evitando repetición de código y permitiendo dividir problemas grandes en partes pequeñas.

*Ejemplo:*
```cpp
#include <iostream>
using namespace std;

int suma(int a, int b) {
	return a + b;
}

int main() {
	cout << suma(2, 3) << endl; // La salida será 5
}
```

---
## Loops

Los loops o bucles en c++ son estructuras de control que permiten repetir un bloque de código varias veces de forma automática, ayudando a ahorrar tiempo y evitar repetir líneas idénticas.
Existen distintos tipos de bucles:
### Bucle `for`
Este tipo de bucle se utiliza cuando sabemos exactamente la cantidad de veces que queremos repetir el bloque de código.
En el argumento del bucle se puede definir 3 cosas:
- Desde donde vamos a empezar
- La condición de paro
- El incremento de la variable

*Ejemplo:*
```cpp
#include <iostream>
using namespace std;

int main() {
    
    for (int i = 0; i < 5; i++) {
	    cout << string(i, '*') << endl;
    }
    
    /*
    La salida será:
    
    *
    **
    ***
    ****
    
    */
}
```

Como dijimos anteriormente, nosotros podemos decidir como se comportará el bucle, en el ejemplo anterior hicimos que fuera un bucle con valores ascendentes, pero también es posible hacer que vaya de forma descendente:

*Ejemplo:*
```cpp
#include <iostream>
using namespace std;

int main() {
    
    for (int i = 5; i > 0; i--) {
	    cout << i << endl;
    }
    
    /*
    Salida:
    5
    4
    3
    2
    1
    */
}
```

También es posible hacer que vaya en distintos saltos, no solo de uno en uno:

*Ejemplo:*
```cpp
#include <iostream>
using namespace std;

int main() {
    
    for (int i = 0; i<=10; i += 2) {
	    cout << i << endl;
    }
    
    /*
    Salida:
    0
    2
    4
    6
    8
    10
    */
}
```

### Bucle `while`
A diferencia del bucle `for` el bucle `while` se usa cuando no se sabe cuantas veces se repetirá el proceso y dependiendo de si una condición es verdadera, si la condición es falsa antes de empezar el bucle, el bucle directamente no se ejecutará.

*Ejemplo:*
```cpp
#include <iostream>
using namespace std;

int main() {
    
    int n;
    cin >> n;
    
    while(n > 0) {
	    cout << n << endl;
	    n--;
    }
	 
// La salida será una cuenta regresiva desde el número ingresado hasta 1 si es que el número ingresado es mayor a 0   
}
```

### Bucle `do-while`
Es parecido al bucle `while` con la diferencia que la condición se evalúa hasta después de haber sido ejecutado una vez, es decir, que con seguridad el bloque de código se ejecutará al menos una vez.

*Ejemplo:*
```cpp
#include <iostream>
using namespace std;

int main() {
    
    int n;
    cin >> n;
    
    do {
	    cout << n << endl;
	    n--;
    } while(n > 0)
    
//Mismo comportamiento que el anterior, pero con la diferencia que sin importar el número ingresado, este se imprimirá una vez.
}
```

---
## Arrays / Vectores

### Arrays
Los arrays o arreglos son una estructura de datos dentro de c++ que permite almacenar una cantidad fija de un tipo de datos, su índice empieza en 0.
Los arreglos se pueden definir sin datos pero con un espacio definido, o directamente especificar los datos que contiene.

*Ejemplo:*
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5]; //No tiene ningún dato en su interior pero tiene espacio para 5 enteros
    int arr2[] = {1, 2, 3, 4, 5, 6}; //Ya se define que datos contiene
    
    int arr3[5] = {1, 2, 3} //Se definen los primeros 3 datos del arreglo, el resto contiene datos basura
}
```

### Vectores
Los vectores no son una estructura nativa de c++, sino que viene de la clase de la librería estandar de c++ `std::vector`, parecido al arreglo también es una estructura de datos, con la diferencia que los vectores son dinámicos, es decir que se les puede agregar más datos durante la ejecución del programa, por esto mismo son bastante usados.

Los vectores tienen distintas funciones que permiten manejarlo.

*Ejemplo:*

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
	vector<int> v; //Se define el la variable v como un vector de enteros
	
	vector<int> v1(5, 0); //Se define v1 como un vector de enteros con 5 espacios inicializados en 0: [0,0,0,0,0]
	
	vector<string> s = {"hola", "como", "estas"}; //Se inicializa un vector de strings.
	
	s.push_back("?"); // Al vector s se le agrega un nuevo elemento al final del vector: ["hola", "como", "estas", "?"]
	
	cout << s[2]; //Se imprime el contenido del vector s en el índice 2: "como"
	
	cout << s.front(); //Obtiene el primer elemento del vector: "hola"
	cout << s.back(); //Obtiene el último elemento del vector: "?"
	
	s[0] = ":)"; //Cambia el elemento ubicado en el índice 0.
	
	
}
```

---
## Punteros

### Definición
Los punteros son variables que almacenan el valor de una dirección de memoria de otra variable. Por lo que en vez de almacenar un valor, guardan la dirección de memoria donde se encuentra dicho valor.

Al trabajar con punteros, existen 2 operadores clave que se utilizarán siempre que se trabaje con ellos:
- **Operador `&`:** Es el operador de dirección, al colocarlo junto a una variable, este devolverá la dirección de memoria de la variable.
- **Operador `*`:** Es el operador de desreferenciación, Al colocarlo junto a un puntero, permite acceder al valor al que apunta el puntero.

Sintaxis básica de punteros:
```cpp
int x = 10;
int* p = &x; //Se guarda la dirección de memoria de la variable x.

cout << x; //10 de toda la vida.
cout << &x; //0x7ffee... la dirección de memoria donde está x.
cout << p; //0x7ffee... mismo valor que &x.
cout << *p; //10 valor al que apunta p.
```

Si se observa en el ejemplo, el operador `*` aparece también en la declaración  del tipo `int* p`, esto indica un puntero a `int`, no una desreferenciación. Misma sintaxis, distinto contexto.

### Punteros con arreglos
Anteriormente explicamos los arreglos como estructuras de datos, pero el comportamiento de estos es el mismo que el de un puntero. El nombre de un arreglo se comporta como un puntero al primer elemento del arreglo.

*Ejemplo:*
```cpp
int arr[5] = {10, 20, 30, 40, 50};
int* p = arr;

cout << *p; //10
cout << *(p + 1); //20 (aritmética de punteros)
cout << p[2] //30 (misma notación de arreglos)
```

### Punteros nulos
Si se crea un puntero que no apunta a nada específico, este debe inicializarse como `nullptr`:
```cpp
int* p = nullptr;

if (p != nullptr) {
	cout << *p; //solo se desreferencia si no es nulo
}
```

Si se intenta desreferenciar un puntero nulo, generará un error (el famoso *segmentation fault*).

### Memoria dinámica
Por el momento las variables que hemos usado viven en la memoria stack, cuando los datos salen del alcance se destruyen automáticamente. Sin embargo, la memoria dinámica vive en el heap y el programador se debe de encargar de liberarla.

```cpp
int* p = new int(5); // reserva un int en el heap con valor 5 
cout << *p; // 5 
delete p; // libera la memoria 
p = nullptr; // buena práctica: evitar puntero colgante 

int* arr = new int[10]; // arreglo dinámico de 10 enteros 
delete[] arr; // liberar arreglos con delete[]
```

### Punteros con funciones
Este apartado es muy importante para lo que haremos el resto del curso ya que afecta directamente el rendimiento de los algoritmos.

```cpp
// Paso por valor: Se copia la totalidad del vector -> costoso en memoria con vectores grandes
void f1(vector<int> v) { v[0] = 100; }

// Paso por referencia: Se pasa la dirección de memoria del vector original, no se crea una copia del vector, se trabaja directamente sobre el vector original.
void f2(vector<int>& v) { v[0] = 100; }

// Paso por referencia constante: No genera una copia, y no permite modificar el vector, útil para solo lectura
void f3(const vector<int>& v) { cout << v[0]; }
```

---
## Recursión

### Definición
Una función recursiva es una función que se llama a si misma. Las funciones recursivas necesitan dos partes:
1. **Caso base:** La condición que detiene la recursión (sin esto, la función nunca termina).
2. **Caso recursivo:** La función se llama a si misma con una entrada "más pequeña" o "más cercana" al resultado esperado.

*Ejemplo:*
```cpp
int factorial(int n) {
	if(n == 0) return 1;            //Caso base
	return n * factorial(n - 1);    //Caso recursivo
}
```

### Pila de llamadas
Cada una de las llamadas recursivas se apila en memoria hasta llegar al caso base y luego se resuelve en orden inverso:

```
factorial(3)
= 3 * factorial(2)
= 3 * (2 * factorial(1))
= 3 * (2 * (1 * factorial(0))
= 3 * (2 * (1 * 1))
= 6
```

Por cada llamada, se genera un "marco" que se agrega a la pila, si no hay caso base (o el caso base esta bien, pero que bien lejos) la pila ya no puede almacenar más marcos y salta un *stack overflow*.


> [!info] Dato para curiosos
> El siguiente es una fork-bomb muy conocida en Linux, y en su esencia es una función recursiva. ¿Puedes identificar sus partes y porque es peligroso?
> ```bash
> :(){:|:&};:
> ```
> DISCLAIMER: El autor de la guía no se hace responsable por el uso incorrecto del código y computadoras dañadas.
>

---
## Clases y Structs

### Structs
Un `struct` permite agrupar varias variables de distintos tipos bajo un solo nombre para poder representar una entidad como una unidad.
```cpp
struct Punto {
	int x;
	int y;
};

Punto p1;
p1.x = 3;
p1.y = 5;

Punto p2 = {7, 2}; //inicializar directamente 
```

Por defecto, los datos dentro de los structs son públicos, es decir que en el ejemplo anterior, cualquiera puede acceder a `p1.x` libremente desde afuera.

Los structs también puede contener funciones miembro:
```cpp
struct Punto {
	int x, y;
	
	double distanciaAlOrigen() {
		return sqrt(x * x + y * y);
	}
};

Punto p = {3, 4};
cout << p.distanciaAlOrigen(); //5
```

### Clases
Una `class` en c++ es prácticamente lo mismo que un `struct`, con la diferencia de que por defecto, los miembros de la clase son privador por defecto.

```cpp
class Punto {
public:
	int x, y;
	
	double distanciaAlOrigen() {
		return sqrt(x * x + y * y);
	}
};
```

En el ejemplo anterior, colocando los datos en `public` se comporta exactamente igual que con un `struct`. Pero como ya se vio en POO, las clases permiten ocultar detalles internos y exponer solo lo necesario.

```cpp
class Contador {
private: 
	int valor;

public:
	Contador() { valor = 0; } //Constructor
	
	void incrementar() { valor++; }
	int obtenerValor() { return valor; }
}

Contador c;
c.incrementar();
c.incrementar();
cout << c.obtenerValor(); //2
// cout << c.valor; tira error ya que es privado
```

Reitero, como se vio en POO a esto se le llama *encapsulamiento*, no permite modificar el valor directamente solo a través de las funciones que expone, evitando que el estado interno quede en un valor inválido.

#### Constructores
Un constructor es una función especial dentro de las clases que se ejecuta automáticamente al crear un objeto y sirve para inicializarlo.

```cpp
class Punto {
	int x, y;
	
	Punto(int x_, int y_) {
		x = x_;
		y = y_;
	}
};

Punto p(3,4);
```

Una clase puede tener más de un constructor, incluyendo uno sin parámetros.
```cpp
class Punto {
public:
	int x, y;
	
	Punto() { x = 0; y = 0; }
	Punto(int x_, int y_) { x = x_; y = y_; }
};

Punto origen; //Usa el constructor sin parámetros (0,0)
Punto p(3, 4); //Usa el constructor con parámetros (3,4)
```
 
---

# Ejercicios evaluados

**Ejercicio 1 - Invertir un vector con dos punteros**

Escribe una función `void invertir(vector<int>& v)` que invierta el contenido de un vector en el mismo vector (sin crear uno nuevo), usando dos punteros: uno que avance desde el inicio y otro desde el final, intercambiando valores hasta cruzarse.

```
Entrada:  {1, 2, 3, 4, 5}
Salida:   {5, 4, 3, 2, 1}
```

**Pistas:**

- Puedes obtener punteros al inicio y al final con `&v[0]` y `&v[v.size() - 1]`.
- El ciclo debe seguir mientras el puntero izquierdo sea menor que el derecho.
- Utiliza una variable auxiliar para guardar algún valor necesario.

**Ejercicio 2 - ¿Es palíndromo? (recursión + dos punteros)**

Escribe una función recursiva `bool esPalindromo(const string& s, int izq, int der)` que determine si una cadena es palíndromo, comparando el carácter de la posición `izq` con el de la posición `der` y avanzando hacia el centro en cada llamada.

```
Entrada:  s = "reconocer"
Salida:   true

Entrada:  s = "algoritmo"
Salida:   false
```

**Pistas:**

- Caso base: si `izq >= der`, ya se revisó toda la cadena (o queda un solo carácter en el medio) → es palíndromo.
- Si `s[izq] != s[der]`, se puede cortar la recursión de inmediato devolviendo `false`.
- Caso recursivo: si los caracteres coinciden, avanza `izq + 1` y retrocede `der - 1`.
- Este ejercicio combina condicionales, índices tipo "puntero" sobre una secuencia, y recursión con dos parámetros que se mueven en direcciones opuestas — la misma lógica de "dos punteros" del ejercicio 1, pero expresada recursivamente en vez de con un bucle.

**Ejercicio 3 - Lista enlazada: contar nodos con recursión**
Dado el siguiente struct auto-referenciado:
```cpp
struct Nodo {
	int valor;
	Nodo* siguiente;
};
```
Escribe una función recursiva `int contarNodos(Nodo* cabeza)` que devuelva cuántos nodos tiene la lista recorriéndola a través del puntero `siguiente` hasta llegar a `nullptr`

```
Entrada: 1 -> 2 -> 3 -> nullptr
Salida: 3

Entrada: nullptr
Salida: 0
```

**Pistas:**

- Caso base: si `cabeza == nullptr` la lista esta vacía -> 0 nodos.
- Caso recursivo 1: (el nodo actual) más lo que devuelva `contarNodos` sobre `cabeza->siguiente`

$$
\int e^{-x} \, dx 
$$
$$
\int  \, dx 
$$