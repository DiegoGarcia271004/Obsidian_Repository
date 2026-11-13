## 11. Nota para quien imparte la guía

### 11.1 Sobre el código base

El código original (construcción, `show_with_levels` y `RSQ`) funciona correctamente para `n ≤ 10`, pero `RSQ` extraía los límites del intervalo desde el `label` con `substr`, lo que da respuestas incorrectas cuando algún índice tiene dos o más dígitos. En esta guía se corrige guardando `lo` y `hi` como enteros. Con la corrección, la estructura se verificó contra una suma, un mínimo y un máximo calculados por fuerza bruta (casi 200 000 comprobaciones sobre arreglos de hasta 60 elementos, con actualizaciones intercaladas, y consultas con n = 1000), sin errores. Aun así, conviene mencionarlo en clase, porque es el tipo de error que no aparece con el arreglo de ejemplo.

### 11.2 Respuestas de referencia de la Parte A

- **A1.** Árbol de `{4,1,7,3,9,2}`: `0-5: 26`; hijos `0-2: 12` (con `0-1: 5` → hojas `0-0: 4`, `1-1: 1`; y `2-2: 7`) y `3-5: 14` (con `3-4: 12` → hojas `3-3: 3`, `4-4: 9`; y `5-5: 2`). El árbol tiene 11 nodos (2n − 1). `RSQ(1,4) = 20` y visita **9 nodos**: `0-5` (parcial), `0-2` (parcial), `0-1` (parcial), `0-0` (disjunto), `1-1` (contenido, 1), `2-2` (contenido, 7), `3-5` (parcial), `3-4` (contenido, 12) y `5-5` (disjunto). Con `RSQ(0,5)` la raíz está contenida y se visita **1 solo nodo**.
- **A2.**
    
    ```cpp
    Tree* find_leaf(Tree* T, int idx) {    while (T->lo != T->hi) {        int q = (T->lo + T->hi) / 2;        T = (idx <= q) ? T->left : T->right;    }    return T;}void update_up(Tree* root, int idx, int value) {    Tree* x = find_leaf(root, idx);    x->data = value;    for (x = x->parent; x != NULL; x = x->parent)        x->data = x->left->data + x->right->data;}
    ```
    
    Se recalculan tantos nodos como ancestros tiene la hoja: la altura del árbol (⌈lg n⌉).
- **A3.** `op_gcd` con elemento neutro `0`, porque `gcd(0, x) = x`; verificado con pruebas aleatorias contra fuerza bruta sin errores.
- **A4.** (1) 1999 nodos para n = 1000 (11 niveles contando la raíz), y 2047 para n = 1024 (11 niveles). (2) Sumas prefijas: consulta O(1) y no hay actualizaciones que las invaliden. (3) Fuerza bruta: hasta 10⁵ · 10⁵ = 10¹⁰ operaciones en las consultas; sumas prefijas: hasta 10¹⁰ en las actualizaciones; Segment Tree: unas 10⁵ · 17 ≈ 1.7 · 10⁶. (4) La resta **no es asociativa** (`(a−b)−c ≠ a−(b−c)`) y no tiene un neutro por ambos lados, así que no cumple las condiciones: el árbol daría resultados que dependen de cómo se parte el intervalo.

### 11.3 Sobre la selección de los problemas de LeetCode

Según las páginas de resumen que consulté (no directamente LeetCode), 3477, 3479, 406 y 729 llevan la etiqueta _Segment Tree_ y su dificultad (Fácil, Media, Media y Media) coincide con la de la tabla; 53 no lleva esa etiqueta (ver B3). Conviene confirmar las etiquetas y enunciados directamente en LeetCode antes de publicar la guía. Se evitaron adrede los problemas más típicos de esa sección (_Range Sum Query - Mutable_, _Count of Smaller Numbers After Self_, _The Skyline Problem_, etc.) por si alguno forma parte de lo que se evalúa; si tienes la lista de problemas evaluados, puedo revisarla para confirmar que no haya coincidencias.

### 11.4 Soluciones de referencia de la Parte B

Todas se compilaron y se probaron: contra fuerza bruta con entradas aleatorias (B1: 20 000 casos; B2: 5 000 casos con alturas repetidas; B3: 20 000 casos, incluyendo arreglos con todos los valores negativos; B4: 3 000 secuencias de reservas) y con los ejemplos del enunciado, sin ningún error. Rendimiento medido en una ejecución con _sanitizers_ activos (más lento que una compilación normal): B1 con n = 10⁵ en 40 ms, y B2 con n = 2·10⁵ en 322 ms.

**B1 (3477 y 3479).** Con la clase `SegMax` de la sección 8:

```cpp
int numOfUnplacedFruits(vector<int>& fruits, vector<int>& baskets) {
    int n = baskets.size();
    SegMax st(baskets);
    int unplaced = 0;
    for (int f : fruits) {
        int i = st.first_at_least(1, 0, n - 1, f);       // canasta libre más a la izquierda con capacidad >= f
        if (i == -1) unplaced++;
        else st.set_value(1, 0, n - 1, i, 0);            // 0 la inutiliza (las capacidades son >= 1)
    }
    return unplaced;
}
```

**B2 (406).** Ordenar por altura ascendente y, a igual altura, por `k` **descendente**; cada persona se coloca en el hueco libre número `k + 1`:

```cpp
struct SegSum {
    int n; vector<int> t;
    SegSum(int n_) : n(n_), t(4 * n_) { build(1, 0, n - 1); }
    void build(int x, int lo, int hi) {
        if (lo == hi) { t[x] = 1; return; }                  // 1 = hueco libre
        int m = (lo + hi) / 2;
        build(2 * x, lo, m); build(2 * x + 1, m + 1, hi);
        t[x] = t[2 * x] + t[2 * x + 1];
    }
    int take_kth(int x, int lo, int hi, int k) {             // ocupa el k-ésimo hueco libre y devuelve su índice
        t[x]--;
        if (lo == hi) return lo;
        int m = (lo + hi) / 2;
        if (t[2 * x] >= k) return take_kth(2 * x, lo, m, k);
        return take_kth(2 * x + 1, m + 1, hi, k - t[2 * x]);
    }
};
vector<vector<int>> reconstructQueue(vector<vector<int>>& people) {
    int n = people.size();
    sort(people.begin(), people.end(), [](const vector<int>& a, const vector<int>& b) {
        if (a[0] != b[0]) return a[0] < b[0];
        return a[1] > b[1];
    });
    SegSum st(n);
    vector<vector<int>> q(n);
    for (auto& p : people) q[st.take_kth(1, 0, n - 1, p[1] + 1)] = p;
    return q;
}
```

Por qué funciona: al procesar `[h, k]`, los huecos todavía vacíos serán ocupados por personas de altura mayor o igual (las más bajas ya se colocaron); por eso los `k` huecos vacíos a su izquierda son las `k` personas ≥ `h` que quedarán delante. Con alturas iguales, la de mayor `k` se procesa primero y va más a la derecha, de modo que las de la misma altura con menor `k` (que irán a su izquierda) todavía cuentan como huecos vacíos.

**B3 (53).**

```cpp
struct Info { long long sum, pref, suf, best; };

Info combine(const Info& a, const Info& b) {
    Info r;
    r.sum  = a.sum + b.sum;
    r.pref = max(a.pref, a.sum + b.pref);
    r.suf  = max(b.suf,  b.sum + a.suf);
    r.best = max({a.best, b.best, a.suf + b.pref});    // izquierda, derecha o cruzando la mitad
    return r;
}
Info build_info(vector<int>& a, int lo, int hi) {
    if (lo == hi) return {a[lo], a[lo], a[lo], a[lo]};
    int m = (lo + hi) / 2;
    return combine(build_info(a, lo, m), build_info(a, m + 1, hi));
}
int maxSubArray(vector<int>& nums) { return (int)build_info(nums, 0, nums.size() - 1).best; }
```

**B4 (729).**

```cpp
struct CNode { bool full = false; CNode *l = nullptr, *r = nullptr; };

class MyCalendar {
    CNode* root = new CNode();
    static const int MAXV = 1000000000;       // posiciones 0 .. MAXV-1

    // true si NO hay ninguna posición ocupada en [s, e] dentro del nodo que cubre [lo, hi]
    bool libre(CNode* x, int lo, int hi, int s, int e) {
        if (x == nullptr || e < lo || hi < s) return true;
        if (x->full || (s <= lo && hi <= e)) return false;   // un nodo existente => hay algo reservado dentro
        int m = lo + (hi - lo) / 2;
        return libre(x->l, lo, m, s, e) && libre(x->r, m + 1, hi, s, e);
    }
    void marcar(CNode* x, int lo, int hi, int s, int e) {
        if (s <= lo && hi <= e) { x->full = true; return; }
        int m = lo + (hi - lo) / 2;
        if (s <= m) { if (!x->l) x->l = new CNode(); marcar(x->l, lo, m, s, e); }
        if (e > m)  { if (!x->r) x->r = new CNode(); marcar(x->r, m + 1, hi, s, e); }
    }
    void destroy(CNode* x) { if (!x) return; destroy(x->l); destroy(x->r); delete x; }
public:
    ~MyCalendar() { destroy(root); }
    bool book(int start, int end) {
        if (!libre(root, 0, MAXV - 1, start, end - 1)) return false;
        marcar(root, 0, MAXV - 1, start, end - 1);
        return true;
    }
};
```

Este último punto es sutil: un nodo que existe en el árbol siempre contiene al menos una posición reservada en su intervalo (los nodos solo se crean al recorrer el camino hacia una reserva), así que, si el intervalo de ese nodo queda completamente dentro del rango consultado, hay conflicto sin necesidad de bajar más.