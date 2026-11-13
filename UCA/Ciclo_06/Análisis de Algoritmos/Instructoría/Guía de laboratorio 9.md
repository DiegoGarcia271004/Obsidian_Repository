## Objetivo

Resolver de forma eficiente consultas sobre rangos de un arreglo (por ejemplo, "¿cuál es la suma de los elementos entre las posiciones `p` y `r`?") cuando el arreglo además **cambia** con el tiempo. Se estudia la construcción del Segment Tree por divide y vencerás, la consulta de rangos, la actualización puntual y cómo generalizar la estructura a otras operaciones (mínimo, máximo, mcd...). Al final se aplica en problemas de LeetCode.

La guía se apoya en lo visto antes: structs con punteros (nodos con `left`, `right` y `parent`), recursión, la recurrencia de divide y vencerás del laboratorio de sorting híbrido, y los árboles de los laboratorios de BST y RBT.

---

## 1. Motivación: consultas de rango con actualizaciones

Dado un arreglo `A` de `n` enteros, se quiere atender dos tipos de operaciones:

- **Consulta**: `RSQ(p, r) = A[p] + A[p+1] + ... + A[r]` (_Range Sum Query_).
- **Actualización**: `A[i] = v`.

|Estrategia|Consulta|Actualización|
|---|---|---|
|Recorrer el rango cada vez|O(n)|O(1)|
|Sumas prefijas (`pref[i]` = suma de `A[0..i]`)|O(1)|O(n) (hay que recalcular lo que sigue de `i`)|
|**Segment Tree**|**O(lg n)**|**O(lg n)**|

Las sumas prefijas son excelentes si el arreglo **nunca cambia**. En cuanto hay actualizaciones mezcladas con consultas, ambas estrategias simples tienen una operación lenta, y el Segment Tree equilibra las dos: ninguna cuesta más que O(lg n).

---

## 2. La idea

Un Segment Tree es un árbol binario donde **cada nodo guarda el resultado de la operación sobre un intervalo del arreglo**:

- La raíz representa el intervalo completo `[0, n-1]`.
- Un nodo que representa `[p, r]` (con `p < r`) tiene dos hijos: `[p, q]` y `[q+1, r]`, donde `q = (p + r) / 2`.
- Las hojas representan un solo elemento `[i, i]` y guardan `A[i]`.
- El dato de un nodo interno es la **combinación** (aquí, la suma) de los datos de sus dos hijos.

Para el arreglo `A = {21, 23, 61, 46, 97, 26, 48, 77, 71, 84}` el árbol resultante es:

```
0-9: 554
├── 0-4: 248
│   ├── 0-2: 105
│   │   ├── 0-1: 44
│   │   │   ├── 0-0: 21
│   │   │   └── 1-1: 23
│   │   └── 2-2: 61
│   └── 3-4: 143
│       ├── 3-3: 46
│       └── 4-4: 97
└── 5-9: 306
    ├── 5-7: 151
    │   ├── 5-6: 74
    │   │   ├── 5-5: 26
    │   │   └── 6-6: 48
    │   └── 7-7: 77
    └── 8-9: 155
        ├── 8-8: 71
        └── 9-9: 84
```

Propiedades útiles (se pueden comprobar con el árbol de arriba):

- Tiene `n` hojas y `n - 1` nodos internos: **2n − 1 nodos en total** (19 para n = 10; 1999 para n = 1000).
- Su altura es ⌈lg n⌉ (4 niveles por debajo de la raíz para n = 10). Esto es lo que hace que las operaciones cuesten O(lg n).
- Es un árbol **estático**: su forma depende solo de `n`, no de los valores. A diferencia de un BST, no hay inserciones ni rotaciones; solo cambian los datos de los nodos.

---

## 3. Estructuras del código base

```cpp
typedef struct Node {
    struct Node* parent;    // Puntero al padre
    string label;           // Texto "p-r" del intervalo (solo para mostrar el árbol)
    int lo, hi;             // Intervalo [lo, hi] que cubre el nodo, como enteros
    int data;               // Dato del nodo (aquí, la suma del intervalo)
    struct Node* left;      // Hijo izquierdo
    struct Node* right;     // Hijo derecho
} Tree;
```

`create_node` recibe el dato y los límites del intervalo:

```cpp
Tree* create_node(int n, int p, int r) {
    Tree* nodo = new Tree();
    nodo->data = n;
    nodo->lo = p;
    nodo->hi = r;
    nodo->label = to_string(p)+"-"+to_string(r);
    nodo->parent = nodo->left = nodo->right = nullptr;
    return nodo;
}
```

---

## 4. Construcción

```cpp
Tree* build_segment(int A[], int p, int r) {
    if (p < r) {
        int q = (p + r) / 2;
        Tree* L = build_segment(A, p, q);        // mitad izquierda [p, q]
        Tree* R = build_segment(A, q + 1, r);    // mitad derecha  [q+1, r]

        Tree* N = create_node(L->data + R->data, p, r);   // combinación de los hijos
        N->left = L;
        N->right = R;
        L->parent = R->parent = N;
        return N;
    }
    return create_node(A[p], p, r);   // caso base: un solo elemento
}
```

Es un divide y vencerás: se parte el problema en dos mitades, se resuelve cada una recursivamente y se combinan los resultados en O(1). La recurrencia es:

T(n) = 2T(n/2) + Θ(1)

Después de usarlo, el árbol debe liberarse (se vio en la guía de punteros):

```cpp
void destroy(Tree* T) {
    if (T == NULL) return;
    destroy(T->left);
    destroy(T->right);
    delete T;
}
```

---

## 5. Consulta de rango (RSQ)

```cpp
int RSQ(Tree* T, int p, int r) {
    // Caso 1: el intervalo del nodo y el pedido no se tocan -> elemento neutro de la suma
    if (r < T->lo || T->hi < p) return 0;

    // Caso 2: el intervalo del nodo está completamente dentro del pedido -> se usa su dato
    if (p <= T->lo && T->hi <= r) return T->data;

    // Caso 3: traslape parcial -> se pregunta a los dos hijos y se combinan las respuestas
    return RSQ(T->left, p, r) + RSQ(T->right, p, r);
}
```

> El comentario del código original decía que en el caso 2 el nodo está "total o parcialmente" dentro del intervalo pedido. La condición realmente exige que esté **totalmente contenido**; el traslape parcial es el caso 3.

### 5.1 Traza de ejemplo

`RSQ(2, 4)` sobre el árbol de la sección 2 (`61 + 46 + 97 = 204`):

```
0-9  -> traslape parcial, baja a ambos hijos
   0-4  -> traslape parcial, baja a ambos hijos
      0-2  -> traslape parcial, baja a ambos hijos
         0-1  -> disjunto, devuelve 0
         2-2  -> contenido, devuelve 61
      3-4  -> contenido, devuelve 143          (46 + 97)
   5-9  -> disjunto, devuelve 0
```

Total: 61 + 143 = **204**, visitando solo **7 de los 19 nodos**. Observa que el intervalo `[2, 4]` se "armó" con dos piezas del árbol (`2-2` y `3-4`) en vez de sumar tres elementos uno por uno. Con `RSQ(1, 8)` (resultado 449) se visitan 13 nodos, y las piezas usadas son `1-1`, `2-2`, `3-4`, `5-7` y `8-8`.

### 5.2 ¿Por qué es O(lg n)?

En cada nivel del árbol, **a lo sumo dos nodos tienen traslape parcial** (los que contienen a los extremos `p` y `r`). Todos los demás nodos de ese nivel son disjuntos o totalmente contenidos, y esos terminan al instante. Como cada nodo parcial genera dos llamadas hijas, se visitan a lo sumo unos 4 nodos por nivel, y hay ⌈lg n⌉ niveles: **O(lg n)**, aunque el rango pedido abarque casi todo el arreglo.

---

## 6. Actualización puntual

El código base no incluye cómo modificar un elemento. Para cambiar `A[idx]` hay que cambiar la hoja correspondiente y **recalcular los datos de todos sus ancestros**, que son exactamente los nodos del camino desde la raíz hasta esa hoja (a lo sumo ⌈lg n⌉ + 1 nodos):

```cpp
void update(Tree* T, int idx, int value) {
    if (T->lo == T->hi) { T->data = value; return; }     // llegamos a la hoja
    int q = (T->lo + T->hi) / 2;
    if (idx <= q) update(T->left, idx, value);
    else          update(T->right, idx, value);
    T->data = T->left->data + T->right->data;             // recalcular al regresar
}
```

Lo importante es la línea final: el recálculo ocurre **al regresar** de la recursión, de manera que cada nodo del camino se recalcula después de que su hijo ya está actualizado. Costo: **Θ(lg n)**.

Ejemplo: tras `update(S, 3, 100)` sobre el árbol de la sección 2, cambian `3-3` (46 → 100), `3-4` (143 → 197), `0-4` (248 → 302) y `0-9` (554 → 608). Los demás nodos no se tocan.

---

## 7. Generalización: no solo sumas

El Segment Tree funciona con cualquier operación `op` que sea **asociativa** y tenga un **elemento neutro** `e` (tal que `op(e, x) = x`). Solo hay que cambiar dos cosas: cómo se **combinan** los hijos y qué se devuelve cuando un nodo es **disjunto** de la consulta.

|Operación|`op(a, b)`|Elemento neutro|
|---|---|---|
|Suma|`a + b`|`0`|
|Mínimo (RMQ)|`min(a, b)`|`INT_MAX`|
|Máximo|`max(a, b)`|`INT_MIN`|
|MCD|`gcd(a, b)`|`0` (porque `gcd(0, x) = x`)|
|XOR|`a ^ b`|`0`|
|Producto|`a * b`|`1`|

Una forma limpia de implementarlo es pasar la operación como parámetro (un puntero a función):

```cpp
int op_sum(int a, int b) { return a + b; }
int op_min(int a, int b) { return min(a, b); }
int op_max(int a, int b) { return max(a, b); }

Tree* build_op(int A[], int p, int r, int (*op)(int,int)) {
    if (p == r) return create_node(A[p], p, r);
    int q = (p + r) / 2;
    Tree* L = build_op(A, p, q, op);
    Tree* R = build_op(A, q + 1, r, op);
    Tree* N = create_node(op(L->data, R->data), p, r);
    N->left = L; N->right = R;
    L->parent = R->parent = N;
    return N;
}

int query_op(Tree* T, int p, int r, int (*op)(int,int), int neutral) {
    if (r < T->lo || T->hi < p) return neutral;
    if (p <= T->lo && T->hi <= r) return T->data;
    return op(query_op(T->left, p, r, op, neutral), query_op(T->right, p, r, op, neutral));
}

void update_op(Tree* T, int idx, int value, int (*op)(int,int)) {
    if (T->lo == T->hi) { T->data = value; return; }
    int q = (T->lo + T->hi) / 2;
    if (idx <= q) update_op(T->left, idx, value, op);
    else          update_op(T->right, idx, value, op);
    T->data = op(T->left->data, T->right->data);
}
```

Uso: `Tree* M = build_op(A, 0, n-1, op_min);` y `query_op(M, 2, 7, op_min, INT_MAX)` devuelve el mínimo de `A[2..7]`.

### 7.1 Descenso por el árbol

Además de consultar rangos, el árbol permite **buscar** directamente. Por ejemplo, en un árbol de **máximos**, el primer índice cuyo valor es ≥ `x`:

```cpp
int first_at_least(Tree* T, int x) {
    if (T->data < x) return -1;                       // ni siquiera el máximo del intervalo alcanza
    if (T->lo == T->hi) return T->lo;                 // llegamos a la hoja
    if (T->left->data >= x) return first_at_least(T->left, x);    // si hay en la izquierda, es el primero
    return first_at_least(T->right, x);
}
```

Cada paso baja un nivel eligiendo un solo hijo: **O(lg n)**, sin recorrer el arreglo. Esta idea ("decidir con el dato del hijo izquierdo hacia dónde bajar") es la clave de dos de los ejercicios de LeetCode del final.

### 7.2 Nodos con más de un dato

Cuando un solo valor por nodo no alcanza, el nodo puede guardar una **pequeña estructura** y la combinación se vuelve una función `combine(a, b)` que resume dos intervalos adyacentes en uno. Por ejemplo, para el subarreglo de suma máxima cada nodo guarda cuatro números: la suma total del intervalo, el mejor prefijo, el mejor sufijo y la mejor suma de un subarreglo dentro del intervalo. Se desarrolla en el ejercicio 3 de LeetCode.

---

## 8. Representación en arreglo

El código del repositorio usa nodos con punteros, que es el estilo coherente con el resto del curso. En programación competitiva (y en LeetCode) es más común guardar el árbol **en un arreglo**, sin punteros: el nodo `x` tiene a sus hijos en las posiciones `2x` y `2x+1` (la raíz es la posición 1), y se reserva espacio para `4n` nodos.

```cpp
struct SegMax {
    int n; vector<int> t;
    SegMax(const vector<int>& a) : n(a.size()), t(4 * a.size()) { build(1, 0, n - 1, a); }

    void build(int x, int lo, int hi, const vector<int>& a) {
        if (lo == hi) { t[x] = a[lo]; return; }
        int m = (lo + hi) / 2;
        build(2 * x, lo, m, a);
        build(2 * x + 1, m + 1, hi, a);
        t[x] = max(t[2 * x], t[2 * x + 1]);
    }

    void set_value(int x, int lo, int hi, int i, int v) {     // actualización puntual
        if (lo == hi) { t[x] = v; return; }
        int m = (lo + hi) / 2;
        if (i <= m) set_value(2 * x, lo, m, i, v);
        else        set_value(2 * x + 1, m + 1, hi, i, v);
        t[x] = max(t[2 * x], t[2 * x + 1]);
    }

    int first_at_least(int x, int lo, int hi, int v) {        // descenso (sección 7.1)
        if (t[x] < v) return -1;
        if (lo == hi) return lo;
        int m = (lo + hi) / 2;
        if (t[2 * x] >= v) return first_at_least(2 * x, lo, m, v);
        return first_at_least(2 * x + 1, m + 1, hi, v);
    }
};
```

|Con punteros (código base)|En arreglo|
|---|---|---|
|Memoria|2n − 1 nodos, cada uno con 3 punteros + `label`|arreglo de 4n enteros (algunas posiciones sin usar)|
|Navegación|`T->left`, `T->right`, `T->parent`|`2x`, `2x+1`, `x/2`|
|Uso típico|enseñanza, árboles dinámicos|concursos, problemas con n grande|

Las operaciones y las complejidades son exactamente las mismas.


---

## 9. Ejercicios

Los siguientes problemas se pueden resolver con lo visto en la guía. Están ordenados por dificultad y se evitaron los problemas más típicos de la sección de Segment Tree de LeetCode (como _Range Sum Query - Mutable_), para que sirvan como práctica adicional.

| #   | Problema                                                                                             | Dificultad    | Idea de la guía que se practica                                   |
| --- | ---------------------------------------------------------------------------------------------------- | ------------- | ----------------------------------------------------------------- |
| B1  | [3477. Fruits Into Baskets II](https://leetcode.com/problems/fruits-into-baskets-ii/)                | Fácil → Media | Árbol de máximos + descenso (sección 7.1) y actualización puntual |
| B2  | [406. Queue Reconstruction by Height](https://leetcode.com/problems/queue-reconstruction-by-height/) | Media         | Árbol de sumas para encontrar el _k_-ésimo hueco libre            |
| B3  | [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)                              | Media         | Nodos con varios datos y función `combine` (sección 7.2)          |


**Indicaciones generales:**

- En todos los problemas se pide resolver con **Segment Tree**, aunque en algunos (como B1 con n ≤ 100 o B4) la fuerza bruta también pase los casos de LeetCode. El objetivo es practicar la estructura, no solo obtener "Accepted".
- Para B1 y B2 conviene usar la representación en arreglo de la sección 8, que es la más cómoda en LeetCode.
- Antes de enviar a LeetCode, prueba tu solución localmente contra una versión de fuerza bruta con entradas aleatorias pequeñas (como en el ejercicio A3).

#### B1 — Fruits Into Baskets

Se tienen `fruits[i]` (cantidad de cada tipo de fruta) y `baskets[j]` (capacidad de cada canasta). Las frutas se procesan de izquierda a derecha, y cada una se coloca en **la canasta libre más a la izquierda cuya capacidad sea suficiente**; cada canasta guarda un solo tipo de fruta. El resultado es cuántos tipos de fruta no pudieron colocarse.

**Pistas:**

- Resuelve primero la versión II (n ≤ 100), pero hazlo con un Segment Tree: es una forma de validar tu estructura antes de la versión III (n ≤ 10⁵), donde la solución O(n²) ya no pasa.
- ¿Qué debe guardar cada nodo? ¿Cómo encuentras "la canasta más a la izquierda con capacidad ≥ x" sin recorrer todas? Revisa la sección 7.1.
- Cuando una canasta se usa, ¿cómo la "eliminas" del árbol sin cambiar su forma? (Piensa en qué valor la vuelve inservible para cualquier fruta.)

#### B2 — Queue Reconstruction by Height

Cada persona es un par `[h, k]`: su altura `h` y la cantidad `k` de personas con altura ≥ `h` que están **delante** de ella en la fila. Dado el arreglo de personas en desorden, reconstruye la fila.

**Pistas:**

- La solución conocida de ordenar por altura descendente e insertar en la posición `k` es O(n²) por los desplazamientos. Aquí se pide la solución O(n lg n) con Segment Tree.
- Procesa a las personas de **menor a mayor altura**. Imagina la fila como `n` huecos vacíos: ¿en qué hueco (contando solo los vacíos) debe quedar una persona `[h, k]`?
- El árbol guarda, en cada nodo, **cuántos huecos libres** hay en su intervalo. Encontrar "el hueco libre número `j`" es un descenso como el de la sección 7.1: si el hijo izquierdo tiene al menos `j` huecos libres, se baja a él; si no, se baja al derecho restando los huecos del izquierdo.
- ¿Qué pasa con las personas de la misma altura? Piensa en cómo ordenarlas entre sí para que la cuenta de huecos siga siendo correcta.

#### B3 — Maximum Subarray

Dado un arreglo de enteros (positivos y negativos), encuentra la mayor suma entre todos los subarreglos contiguos. El problema tiene una solución lineal conocida (algoritmo de Kadane), y el propio enunciado sugiere como seguimiento practicar la técnica de **divide y vencerás**; aquí se pide resolverlo con la idea del Segment Tree: dividir el arreglo en mitades, resolver cada una y **combinar**. (LeetCode lo etiqueta como Array, Divide and Conquer y Programación Dinámica; el Segment Tree es la generalización natural de ese enfoque.)

**Pistas:**

- Cada nodo guarda cuatro datos del intervalo: `sum`, `pref` (mejor suma de un prefijo), `suf` (mejor suma de un sufijo) y `best` (mejor subarreglo dentro del intervalo).
- Una hoja con valor `x` tiene los cuatro datos iguales a `x`.
- Para combinar dos nodos `a` (izquierdo) y `b` (derecho), el mejor subarreglo puede estar en `a`, en `b`, o **cruzar la mitad**. Con esto puedes escribir las cuatro fórmulas de `combine(a, b)`.
- La recurrencia de tu construcción debería ser T(n) = 2T(n/2) + Θ(1) = Θ(n). Compárala con la solución clásica de divide y vencerás que recorre el cruce en cada nivel y cuesta Θ(n lg n).
- Cuidado con los arreglos con **todos los valores negativos**: el resultado es el elemento menos negativo, nunca 0.

