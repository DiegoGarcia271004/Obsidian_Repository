¡Es terrible! Sir Colocado II y Hermione no lograron darle pelea al PFL Pleités…

Lastimosamente, no lograron detenerlo, y ahora ambos están al borde de ser expulsados de las canchas, por lo que ambos tuvieron que retirarse.

Tras retirarle el casco, Robert Polanski volvió en sí, para confirmar lo peor: el objetivo del PFL Pleités es desactivar el sistema de defensa interplanetaria de los Autovengadores, permitiendo así la llegada de los temibles Reapers. Desafortunadamente, Polanski quedó lesionado, Chriseme cansado y Odlanor sigue evacuando, así que no hay nadie que pueda detener al PFL Pleités.

El sistema se diseñó conectando una serie de N módulos mediante M cables de altísima tensión, asegurándose que hay un único módulo de control general (el 1, donde tienes acceso a todos los demás) y, al menos un módulo de defensa (todos están ubicados al límite de la red). Para desactivar el sistema, el PFL Pleités necesita enviar un pulso de energía por la red, que sea capaz de destruir todos los módulos de defensa que existan.

Cabe destacar que cada módulo resiste un pulso de, a lo sumo, E de energía, y cualquier cantidad menor no pasará al siguiente. Para esta tarea, el PFL Pleités recibirá…

**TU AYUDA?????**

## Entrada

La primera línea contiene un valor N, la cantidad de módulos, y M, la cantidad de cables.

La segunda línea contiene N enteros E, la cantidad de energía que resiste cada módulo

Las siguientes M líneas presentan cada una dos enteros U y V, que indican una conexión entre dichos módulos (esto significa que un pulso de energía puede ir del nodo U al V, y viceversa).

## Salida

Debes imprimir un entero por cada módulo de defensa, que represente la cantidad mínima de energía que requiere destruirlo. Por simplicidad, imprime todos los valores en una misma línea, ordenados de menor a mayor.

## Restricciones

- Actualmente, el PFL Pleités y tú están en el módulo 1
- $1\leq N \leq 10^{5}$
- $N-1\leq M \leq \frac{N*(N-1)}{2}$
- $1\leq U,V\leq N$
- $1\leq E\leq 10^{9}$

| Entrada                                             | Salida |
| --------------------------------------------------- | ------ |
| 5 5<br>3 8 2 4 1<br>1 2<br>1 3<br>3 2<br>2 4<br>3 5 | 6 15   |

| Entrada                                                      | Salida |
| ------------------------------------------------------------ | ------ |
| 6 6<br>2 5 1 4 3 2<br>1 2<br>1 3<br>2 4<br>2 5<br>3 5<br>3 6 | 5 11   |
|                                                              |        |

```cpp
#include <bits/stdc++.h>
using namespace std;

class Module
{
private:
    size_t id;
    vector<pair<Module *, size_t>> wires;

public:
    Module(size_t i) : id(i) {}

    void setId(size_t i)
    {
        id = i;
    }

    size_t getId()
    {
        return id;
    }

    void addEdge(Module *v, size_t w)
    {
        wires.push_back(make_pair(v, w));
    }

    vector<pair<Module *, size_t>> &getWires()
    {
        return wires;
    }
};

class Graph
{
private:
    vector<Module *> modules;

public:
    Graph() = default;

    size_t getN()
    {
        return modules.size();
    }

    vector<Module *> &getModules()
    {
        return modules;
    }

    void addVertex(Module *m)
    {
        modules.push_back(m);
    }
};

vector<size_t> Dijkstra(Graph &g, Module *s, vector<size_t> &v)
{
    vector<size_t> len(g.getN(), INT_MAX);
    len[s->getId() - 1] = 0;

    auto f = [](pair<size_t, Module *> a, pair<size_t, Module *> b)
    {
        return a.first > b.first;
    };
    priority_queue<pair<size_t, Module *>, vector<pair<size_t, Module *>>, decltype(f)> H(f);
    H.push(make_pair(0, s));

    while (!H.empty())
    {
        pair<size_t, Module *> v = H.top();
        H.pop();

        if (v.first <= len[v.second->getId() - 1])
        {
            for (pair<Module *, size_t> w : v.second->getWires())
            {
                size_t new_len = len[v.second->getId() - 1] + w.second;

                if (new_len < len[w.first->getId() - 1])
                {
                    len[w.first->getId() - 1] = new_len;
                    H.push(make_pair(new_len, w.first));
                }
            }
        }
    }

    vector<size_t> ret;
    for (size_t i : v)
    {
        ret.push_back(len[i - 1]);
    }

    sort(ret.begin(), ret.end());

    return ret;
}

int main()
{

    size_t n, m;
    vector<size_t> e;
    vector<size_t> p;
    Graph g;

    cin >> n >> m;

    for (size_t i = 0; i < n; ++i)
    {
        size_t t;
        cin >> t;
        Module *mod = new Module(i + 1);
        g.addVertex(mod);
        p.push_back(mod->getId());
        e.push_back(t);
    }

    for (size_t i = 0; i < m; ++i)
    {
        size_t u, v;
        cin >> u >> v;

        g.getModules()[u - 1]->addEdge(g.getModules()[v - 1], e[v - 1]);
        if (g.getModules()[u - 1]->getWires().size() > 1)
            p[u - 1] = 0;

        g.getModules()[v - 1]->addEdge(g.getModules()[u - 1], e[u - 1]);
        if (g.getModules()[v - 1]->getWires().size() > 1)
            p[v - 1] = 0;

        p[0] = 0;
    }

    if (g.getModules().size() == 1) p[0] = 1;

    vector<size_t> tot, res;
    for (size_t i : p)
    {
        if (i != 0)
            tot.push_back(i);
    }

    res = Dijkstra(g, g.getModules()[0], tot);
    for (size_t i = 0; i < res.size(); ++i)
    {
        if (i)
            cout << ' ';
        cout << res[i] + e[0];
    }
    cout << '\n';

    return 0;
}
```

