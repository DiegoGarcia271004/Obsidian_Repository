**Mejorar entrada y salida**

```cpp
ios::sync_with_stdio(false);
cin.tie(nullptr);
```

**Grafo dirigido con peso**
```cpp
class Vertex {
private:
    long long id;
    vector<pair<Vertex *, long long>> edges;
    //vector<Vertice *> edges;
public:
    Vertex(long long i) : id(i) {}
    void setId(long long i) { id = i; }
    long long getId() { return id; }
    void addEdge(Vertex *v, long long e) { edges.push_back(make_pair(v, e)); }
    vector<pair<Vertex *, long long>> &getEdges() { return edges; }
    //vector<Vertice *>
    bool removeEdge(Vertex *dest, long long w) {
        for (auto it = edges.begin(); it != edges.end(); ++it) {
            if (it->first == dest && it->second == w){
                edges.erase(it);
                return true;}
            }
        return false;
    }
};
class Graph {
private:
    vector<Vertex *> vertices;
public:
    Graph() = default;
    long long getN() { return vertices.size(); }
    vector<Vertex *> &getVertices() { return vertices; }
    void addVertex(Vertex *m) { vertices.push_back(m); }
    bool removeEdge(long long from, long long to, long long w) {
        Vertex *src = nullptr, *dst = nullptr;
        for (Vertex *v : vertices) {
            if (v->getId() == from) src = v;
            if (v->getId() == to) dst = v;
        }
        if (!src || !dst)return false;
        return src->removeEdge(dst, w);
    }
};
```

**Dijkstra**
```cpp
vector<long long> Dijkstra(Graph &g, Vertex *s) {
    vector<long long> len(g.getN(), LLONG_MAX);
    len[s->getId() - 1] = 0;
    auto f = [](pair<long long, Vertex *> a, pair<long long, Vertex *> b){
        return a.first > b.first;
    };
    priority_queue<pair<long long, Vertex *>, vector<pair<long long, Vertex *>>, decltype(f)> H(f);
    H.push(make_pair(0, s));
    while (!H.empty()){
        pair<long long, Vertex *> v = H.top(); H.pop();
        if (v.first != len[v.second->getId() - 1]) { continue; }
        for (pair<Vertex *, long long> w : v.second->getEdges()){
                long long new_len = len[v.second->getId() - 1] + w.second;
                if (new_len < len[w.first->getId() - 1]) {
                    len[w.first->getId() - 1] = new_len;
                    H.push(make_pair(new_len, w.first));
                }
            }
    }
    return len;
}
```

**Criba y factorización**
```cpp
typedef long long ll; typedef vector<ll> vll;
ll _sieve_size; bitset<10000010> bs; vll p;
//Para factorizar hasta 10^7 primos
vll primeFactors(ll N){ 
    vll factors;
    for (int i = 0; (i < (int)p.size()) && (p[i] * p[i] <= N); ++i)
        while (N % p[i] == 0) {              
            N /= p[i]; factors.push_back(p[i]);
        }
    if (N != 1) factors.push_back(N); 
    return factors;
}
void sieve(ll upperbound){                                 
    _sieve_size = upperbound + 1; bs.set(); bs[0] = bs[1] = 0;            
    for (ll i = 2; i < _sieve_size; ++i)
        if (bs[i]) {
            for (ll j = i * i; j < _sieve_size; j += i) bs[j] = 0;
            p.push_back(i);
        }
    }
}
```

```cpp
//Factorizar hasta 10^18 primos acotados
vector<int> spf(N + 1);

for (int i = 0; i <= N; i++) spf[i] = i;

for (int i = 2; i * i <= N; i++) {
    if (spf[i] == i) {
        for (int j = i * i; j <= N; j += i) {
            if (spf[j] == j) spf[j] = i;
        }
    }
}
vector<int> factorize(int n) {
    vector<int> factors;
    while (n != 1) {
        factors.push_back(spf[n]);
        n /= spf[n];
    }
    return factors;
}
```

**Segment tree**
```cpp
struct Monoide {
	int valor = 0; //elemento neutro de la operación
	Monoide() = default;
	Monoide(int valor) : valor(valor) {}
};
//Cambiar que hace la función para cambiar el operador
Monoide operator+(Monoide left, Monoide right) {
	return max(left.valor, right.valor);
}
struct SegmentTree {
	int n; //cantidad inicial de datos a ingresar
	vector<Monoide> data; //estructura de datos principal
	SegmentTree(auto const& a) : n(bit_ceil(a.size())), data(bit_ceil(a.size())*2) {
		for (int i = 0; i < a.size(); ++i) data[i + n] = a[i];
		for (int i = n; i--;) data[i] = data[i*2] + data[i*2 + 1];
	}
	void set(int i, Monoide x) {
		i += n;
		data[i] = x;
		while (i /= 2) data[i] = data[i*2] + data[i*2 + 1];
	}
	Monoide get(int l, int r, int idx, int cl, int cr) {	// [l, r)
		if (l >= cr || cl >= r) return {};
		if (l <= cl && cr <= r) return data[idx];
		int m = (cl + cr)/2;
		return get(l, r, idx*2, cl, m) + get(l, r, idx*2 + 1, m, cr);
	}
	Monoide get(int l, int r) {
		return get(l, r, 1, 0, n);
	}
};
```

**Union find**
```cpp
class UnionFind {
private:
    vector<int> parent;
    vector<int> rank;
public:
    UnionFind(int n) {
        parent.resize(n);
        rank.assign(n, 0);
        for (int i = 0; i < n; i++) {
            parent[i] = i;
        }
    }
    int find(int x) {
        if (parent[x] != x)
            parent[x] = find(parent[x]);
        return parent[x];
    }
    void unite(int a, int b) {
        a = find(a);
        b = find(b);
        if (a == b)
            return;
        if (rank[a] < rank[b])
            swap(a, b);
        parent[b] = a;
        if (rank[a] == rank[b])
            rank[a]++;
    }
    bool same(int a, int b) {
        return find(a) == find(b);
    }
};
```

**CC**
```cpp
vector<int> CC(Graph &g) {
    vector<bool> visited(g.getN(), false);
    vector<int> component(g.getN(), -1);
    int cc = 0;
    for (int i = 0; i < g.getN(); i++) {
        if (visited[i])
            continue;
        queue<Vertice*> q;
        Vertice* s = g.getVertex(i + 1);
        visited[i] = true; component[i] = cc; q.push(s);
        while (!q.empty()) {
            Vertice* v = q.front(); q.pop();
            for (Vertice* w : v->getEdges()) {
                int id = w->getId() - 1;
                if (!visited[id]) {
                    visited[id] = true; component[id] = cc; q.push(w);
                }
            }
        }
        cc++;
    }
    return component;
}
```

**BFS para distancias**
```cpp
vector<ull> ShortestPath(Graph &g, Vertice *s)
{
    vull len(g.getN(), -1);
    len[s->getId() - 1] = 0;
    vector<bool> exp(g.getN() + 1, false);
    exp[s->getId() - 1] = true;
    queue<Vertice *> q;
    q.push(s);
    while (!q.empty())
    {
        Vertice *v = q.front();
        q.pop();
        for (Vertice *w : v->getEdges())
        {
            if (!exp[w->getId() - 1])
            {
                exp[w->getId() - 1] = true;
                len[w->getId() - 1] = len[v->getId() - 1] + 1;
                q.push(w);
            }
        }
    }
    return len;
}
```

**DFS**
```cpp
void DFS(Vertex* v, vector<bool>& visited) {
    visited[v->getId() - 1] = true;
    for (Vertex* w : v->getEdges()) {
        if (!visited[w->getId() - 1]) {
            DFS(w, visited);
        }
    }
	if (r == 0 && b != 0 || r != 0 && b == 0 || r>=2 && b >= 2) return true
}
```

**Knapsack**
```cpp
int Knapsack(vec& V, vec& W, int n, int C) {
    mat dp(n+1, vec(C+1, -1));
    for(int j = 0; j <= C; j++) dp[0][j] = 0;
    for(int i = 0; i <= n; i++) dp[i][0] = 0;
    for(int i = 1; i <= n; i++)
        for(int j = 1; j <= C; j++)
            if( W[i-1] <= j )
                dp[i][j] = max( dp[i-1][j], V[i-1] + dp[i-1][j-W[i-1]]);
            else
                dp[i][j] = dp[i-1][j]; return dp[n][C];}
```

