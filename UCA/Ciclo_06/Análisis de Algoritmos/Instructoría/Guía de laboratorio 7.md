Comprender por qué los árboles rojo-negro mantienen una altura acotada, identificar las reglas que deben cumplir y relacionarlas con las operaciones de inserción, rotación y eliminación implementadas en el código proporcionado.

# Índice

1. Repaso teórico
2. Implementación en C++
3. Ejercicios evaluados

---

# Teoría
## 1. Repaso teórico

### ¿Para qué sirve un árbol rojo-negro?

Un árbol rojo-negro (_Red-Black Tree_ o RBT) es un árbol binario de búsqueda (BST) que almacena claves ordenadas y utiliza colores y reestructuraciones para evitar que el árbol se vuelva demasiado alto.

Un BST ordinario puede degenerar en una cadena si se insertan valores ordenados. En ese caso, buscar, insertar o eliminar puede costar **\(O(n)\)**. Un RBT mantiene la altura en **\(O(\log n)\)**, por lo que estas operaciones tienen costo **\(O(\log n)\)**.

### Propiedades de un RBT

1. Cada nodo es **rojo** o **negro**.
2. La raíz es negra.
3. Los nodos nulos (NIL) se consideran negros.
4. Un nodo rojo no puede tener un padre rojo ni un hijo rojo. Equivalentemente, no puede haber dos nodos rojos consecutivos en un camino.
5. Todo camino desde un nodo hasta una hoja NIL descendiente contiene la misma cantidad de nodos negros.

Las propiedades, junto con el orden de BST, permiten acotar la altura. En el código del laboratorio, los hijos ausentes se representan con `nullptr` en lugar de nodos NIL explícitos; para razonar sobre las reglas, se consideran negros.

### ¿Qué aportan los colores?

Los colores permiten detectar qué regla se rompió después de una inserción o eliminación. El algoritmo corrige el árbol cambiando colores y, cuando hace falta, mediante rotaciones.

No se debe memorizar una secuencia aislada de cambios de punteros: primero identifica la relación entre el nodo afectado, su padre, su abuelo y su tío (o su hermano durante el borrado).

### Rotaciones

Una rotación modifica la estructura local de un árbol sin romper el orden de búsqueda.

En una **rotación izquierda**, el hijo derecho sube y el nodo original pasa a ser su hijo izquierdo. En una **rotación derecha** ocurre lo simétrico. También se actualizan el padre, el enlace del abuelo y el subárbol intermedio.

Rotación izquierda en `A`, donde `B` es su hijo derecho:

```
Antes:                 Después:

      A                      B
     / \                    / \
    X   B                  A   Z
       / \                / \
      Y   Z              X   Y
```

Las funciones `leftRotation(A, B)` y `rightRotation(A, B)` del código realizan estas reconexiones. Se asume que `B` es el hijo derecho de `A` para la rotación izquierda, y el hijo izquierdo para la derecha.

### Complejidad

La altura de un RBT es **\(O(\log n)\)**. Por ello, buscar, insertar y eliminar requieren **\(O(\log n)\)** tiempo. Las rotaciones y los cambios de color de cada paso cuestan **\(O(1)\)**; una reparación puede subir por la altura del árbol, de modo que el costo total sigue siendo **\(O(\log n)\)**.

---

## 2. Implementación en C++

### Código a utilizar

Para esta (debido a la gran cantidad de código que tiene no se colocará) el archivo con el código se encuentra en este enlace:
[Código RBT](https://github.com/UCASV/AAI/blob/main/03-Searching/05_rbt.cpp)

### Estructura del nodo

El código compartido utiliza la siguiente estructura:

```
enum color { RED, BLACK, DOUBLE_BLACK };

typedef struct Node {
    int data;
    enum color color;
    struct Node* left;
    struct Node* right;
    struct Node* parent;
} TreeNode;
```

Además de los enlaces izquierdo y derecho de un BST, cada nodo conserva un puntero a su padre y un color.

En este código, `DOUBLE_BLACK` se utiliza temporalmente durante la reparación de algunas eliminaciones; no es un color permitido en un RBT una vez que la operación termina correctamente.

### Funciones auxiliares que debes reconocer

- `create_node(value)`: crea un nodo nuevo rojo, con hijos y padre nulos.
- `BST_search(T, value)` y `BST_get(T, value)`: comprueban si existe un valor y, en el segundo caso, devuelven el puntero al nodo.
- `check_child_side(node)`: indica si el nodo es hijo izquierdo o derecho de su padre.
- `BST_insert(value)` y `BST_delete(value)`: realizan la parte estructural de insertar o borrar como en un BST.
- `leftRotation(A, B)` y `rightRotation(A, B)`: reestructuran el árbol y actualizan los enlaces de padres e hijos.

#### Visualización

Usa `BST_show(T, IN)` para imprimir el recorrido _in-order_ y verificar que los valores siguen ordenados.

La función `RBT_show_with_levels(T, 0)` muestra la estructura por niveles y los colores. No es necesario estudiar su implementación; basta con utilizarla para observar los cambios después de cada operación.

### Inserción en un RBT

La inserción se divide en dos fases:

1. Insertar el valor como en un BST, creando el nodo rojo.
2. Reparar posibles violaciones de las reglas rojo-negro con `RBT_fixInsertion(n)`.

#### Casos de reparación

- **El nodo insertado es la raíz:** se colorea de negro.
- **El padre es negro:** no hay violación y el proceso termina.
- **El padre es rojo y el tío es rojo:** el padre y el tío se vuelven negros, el abuelo rojo y se continúa revisando desde el abuelo.
- **El padre es rojo y el tío es negro o nulo:** si nodo-padre-abuelo forman un triángulo, se rota primero el padre; luego se rota el abuelo para resolver la línea y se ajustan los colores.

![[Pasted image 20261018220940.png]]

### Eliminación en un RBT

La eliminación tiene una fase estructural y otra de reparación. Primero se obtiene el nodo que se eliminará y se guarda su color original. Después, `BST_delete(value)` lo elimina como en un BST y devuelve el hijo que ocupa su lugar, si existe.

El color original es importante: borrar un nodo rojo no produce el mismo problema que borrar uno negro.

En la implementación entregada, los casos principales son:

- **El nodo eliminado era rojo, o el hijo que lo reemplaza es rojo:** el reemplazo se deja negro y la reparación termina.
- **Se elimina un nodo negro y lo reemplaza un nodo negro o nulo:** aparece el estado temporal de doble negro y se debe reparar.
- **El hermano es negro:** según los colores de sus hijos y del padre, puede recolorearse, propagarse el doble negro hacia arriba o resolverse mediante una o dos rotaciones.
- **El hermano es rojo:** se intercambian colores y se rota el padre para convertir la situación en un caso con hermano negro.

Para seguir el código, identifica:

- `d`: nodo eliminado.
- `h`: hijo que lo reemplaza o nodo con doble negro.
- `p`: padre.
- `s`: hermano.
- `n`: hijo rojo del hermano cuando aplica.

Los hijos `nullptr` se consideran negros.

![[Pasted image 20261018221100.png]]

---

# 3. Ejercicios evaluados

Resuelve los siguientes problemas utilizando las operaciones del árbol rojo-negro que ya se proporcionaron. **No modifiquen la implementación de las funciones del RBT ni del BST**; puedes escribir funciones auxiliares propias y adaptar el `main()` para leer datos, procesar consultas y mostrar los resultados solicitados.

En todos los ejercicios, asume que los valores insertados son enteros y que no hay duplicados, salvo que el enunciado indique lo contrario.

### Ejercicio 1 - ¿Está en el inventario?

**Tema:** inserción y búsqueda.

Una tienda registra los códigos numéricos de sus productos en un árbol rojo-negro. Después de cargar los códigos, debe responder varias consultas para determinar si un producto está registrado.

**Entrada**

- Una línea con dos enteros `N` y `Q`: cantidad de códigos registrados y cantidad de consultas.
- Una línea con `N` enteros distintos que representan los códigos.
- Luego, `Q` líneas, cada una con un entero `X` que se debe consultar.

**Salida**

Para cada consulta, imprime `SI` si el código existe en el árbol o `NO` en caso contrario.

**Ejemplo**

```
Entrada
5 4
18 7 25 3 12
7
10
25
30

Salida
SI
NO
SI
NO
```

**Pistas:**
1. Inserta los `N` códigos utilizando `RBT_insert`.
2. Responde cada consulta utilizando la función de búsqueda disponible.
3. Evita recorrer todo el árbol para cada consulta: aprovecha el orden de búsqueda del BST.

### Ejercicio 2 - Productos dentro de un rango

**Tema:** recorridos y procesamiento de datos almacenados en el árbol.

Una tienda quiere conocer cuántos productos tienen un código dentro de ciertos intervalos. Después de insertar los códigos, se reciben consultas con dos límites `L` y `R`. Para cada consulta, debes contar cuántos códigos cumplen `L <= código <= R`.

### Entrada

- Una línea con dos enteros `N` y `Q`.
- Una línea con `N` códigos distintos.
- Luego, `Q` líneas con dos enteros `L` y `R`, donde `L <= R`.

### Salida

Para cada consulta, imprime la cantidad de códigos que pertenecen al intervalo cerrado `[L, R]`.

### Ejemplo

```
Entrada
6 3
20 8 30 5 12 25
5 12
10 26
21 40

Salida
3
3
2
```

### Indicaciones

1. Construye el árbol usando `RBT_insert`.
2. Implementa una función auxiliar que recorra el árbol y cuente los nodos cuyo valor está entre `L` y `R`, inclusive.
3. Aprovecha el orden del BST para evitar visitar ramas que no pueden contener valores dentro del intervalo.
4. No es necesario modificar `BST_show` ni las funciones del árbol proporcionadas.

### Ejercicio 3 - Registro dinámico de códigos

**Tema:** inserción, eliminación y consultas después de actualizaciones.

Un sistema mantiene un conjunto de códigos activos. Inicialmente se registra una lista de códigos y después se ejecutan operaciones de tres tipos:

- `A X`: agregar el código `X`.
- `E X`: eliminar el código `X`, si existe.
- `C X`: consultar si el código `X` está activo.

Se garantiza que los códigos agregados con `A` no están activos en ese momento. Una operación `E` puede solicitar la eliminación de un código que no exista; en ese caso, no debe cambiar el árbol.

**Entrada**

- Una línea con dos enteros `N` y `Q`.
- Una línea con `N` códigos distintos que forman el conjunto inicial.
- Luego, `Q` líneas, cada una con una operación y un entero `X`.

**Salida**

Por cada operación `C X`, imprime `SI` si el código está activo y `NO` si no lo está. Las operaciones `A` y `E` no producen salida.

**Ejemplo**

```
Entrada
4 7
10 20 30 40
C 20
E 20
C 20
A 15
C 15
E 99
C 30

Salida
SI
NO
SI
SI
```

**Pistas:**

1. Inserta los códigos iniciales con `RBT_insert`.
2. Para `A X`, inserta el código con la operación de inserción del RBT.
3. Antes de ejecutar `E X`, verifica que el código exista, porque la implementación de `RBT_delete` compartida asume que el valor está presente.
4. Para `C X`, utiliza la función de búsqueda.
5. Prueba las operaciones en distintos órdenes y verifica que el árbol siga funcionando después de inserciones y eliminaciones.