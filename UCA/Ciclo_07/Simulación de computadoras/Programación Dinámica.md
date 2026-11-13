# Independent Set Problem

Recordando grafos:
Un grafo es un conjunto de vértices ($V$) y aristas $(E)$
$$
G=(V,E)
$$
$$
S \subseteq V \,|\, \forall v, w\in S,v\neq w \implies (v,w) \not\in E
$$
Un **conjunto independiente** ($S$) es un subconjunto de los vértices del grafo, conteniendo los elementos $v$ y $w$. Pero la dupla de estos vértices no posee una arista que los conecte (no se encuentra en el conjunto de las aristas del grafo).

# MWIS Problem

$$
\begin{gather*}
G=(V,E)\\
S \subseteq V \,|\, \forall v, w\in S,v\neq w \implies(v,w) \not\in E\\
w_{v} \forall v\in V, \sum_{v\in S}w_{v} \text{ es máxima}
\end{gather*}
$$
$$
\begin{gather*}
v_{n} \not\in S\\
V-\{ v_{n} \}=V^{*}\\
E-\{ (v_{n}, v_{n-1}) \}=E^{*}\\
G_{n-1}=(V^{*},E^{*})\\

\end{gather*}
$$
---

# Taller

Eventos posibles:
$$
[5,3,4,11,2]
$$
**Restricción:** No se puede asistir a 2 eventos consecutivos
**Objetivo:** Obtener máxima ganancia obtenible.

Sea $G(i)$ la máxima ganancia posible llegando a los primeros $i$ eventos con las restricciones dadas.

$$
G(i):=\begin{cases}
G(i-1) \\
g_{i}+G(i-2)
\end{cases}
$$

$$
f(i):=max(f(i+1), f(i+2))
$$