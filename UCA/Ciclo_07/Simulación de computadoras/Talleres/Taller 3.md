[1,3,2,4,6,1]

Aplicando empezar desde el final:
1. Empezamos en el 1 (al "final"), pero para este caso resulta que el valor $n-1$, siempre deberá de tomarse, no es cuestión si entra o no en la respuesta sino que en todos los casos posibles, siempre terminaremos tomando el resultado final.
2. Debido a lo explicado en el punto 1, nosotros empezaremos en el valor ubicado en $n-2$. Aquí es donde planteamos la tautología:
	1. Caso 1: Se toma el peso actual
	2. Caso 2: No se toma el peso actual
	Con respecto al caso 2 podemos plantear dos casos aparte:
		2.1 el mínimo se obtiene en el paso anterior al nodo actual
		2.2 el mínimo se obtiene en la posición dos pasos antes del actual
	Por ende, podemos sintetizarlos en:
		**No se toma el peso actual, sino que se toma el peso mínimo entre **


---

5. Los subproblemas que aparecen recurrentemente es el del cálculo del costo para llegar desde 0 hasta la posición $i$.
---

6.1 La recurrencia, tomando en cuenta los discutido en la tautología sería:
$$
MWP(n):=\begin{cases}
w_{i}+min(MWP(i-1),MWP(i-2)) \\
MWP(i-1)
\end{cases}
$$
$$
MWP(n)=min(w_{i}+min(MWP(i-1),MWP(i-2))), MWP(i-1))
$$
6.2 
La IA planteó la siguiente recurrencia:
$$
MWP(n)=w_{i}+min(MWP(i-1), MWP(i-2))
$$



1, 3, 2, 4, 6, 1

