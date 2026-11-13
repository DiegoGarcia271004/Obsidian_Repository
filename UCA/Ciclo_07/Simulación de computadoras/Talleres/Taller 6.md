1. En la historia presentada hay 3 problemas a resolver. 
	a. Identificar cada uno de los 3 problemas y nombrarlos formalmente.
En la historia de Toby es posible identificar 3 problemas:

- Primeramente, Toby comparó las rutas de su perro (la del barrio y la del parque) buscando los huesos que aparecen en ambas rutas por igual, respetando el orden de descubrimiento de los huesos en cada ruta. Este caso presenta un problema de Longest Consecutive Subsequence (LCS).
- Toby observa ahora la colección de huesos en su jardín, y busca una selección donde cada hueso es más pequeño que el anterior sin poder reordenar libremente los huesos. Este caso es un problema de Longest Decreasing Subsequence (LDS).
- Finalmente Toby vuelve a comparar las dos rutas de su perro, buscando nuevamente los huesos que aparecen en ambas rutas, pero ahora con la condición que cada hueso común a agregar deberá de tener tamaños decrecientes. Esto sería una combinación de los dos problemas anteriores, es decir: Longest Consecutive Subsecuence + Longest Decreasing Subsequence (LCS+LDS).

	b. ¿Qué tipo de algoritmo es necesario para resolver cada uno de estos problemas?

- LSC: Dadas dos secuencias se buscará la colección más larga de elementos que se encuentren en ambas secuencias por igual, respetando el orden original de cada uno de los elementos. Pero, cada elemento puede incluirse o saltarse, y la cantidad de posibles respuestas crece en gran medida con la cantidad de objetos en las secuencias. En la historia de Toby se encuentra esta problemática al momento de que se busca esto mismo con las rutas (secuencias) y los huesos (objetos).
- LDS: Dada una sola secuencia de objetos con tamaños numéricos, se busca la selección más larga donde los tamaños de los elementos sean estrictamente decreciente sin poder reordenar la secuencia original. En la historia de Toby, él busca hacer esto mismo con los huesos recolectados en el día.
- LCS+LDS: Es la combinación de los dos algoritmos anteriores, se busca encontrar la colección más larga de elementos dadas dos secuencias, pero esta colección deberá ser estrictamente decreciente. 

---

2. Para cada uno de los problemas identificados:
a. Definir “el final” del problema. 
b. Definir la forma de la respuesta a asumir. 
c. Establecer la tautología e identificar los escenarios posibles. 
d. Analizar cada uno de los escenarios definidos en la tautología. 
e. Derivar la recurrencia del problema. 
f. Generalizar la recurrencia. 
g. Definir la estructura de memoización y el significado de sus índices. 
h. Definir los casos base. 
i. Escribir el pseudocódigo de la solución (ya sea Top-Down o Bottom-Up). 
	 Debe incluir Reconstrucción.

a. 
El final del problema será el último elemento en ambas subsecuencias
b.
La respuesta será un número que representa la longitud de la subsecuencia más larga entre las dos secuencias
c. 
La pareja de los últimos elementos en cada secuencia pertenece a la LCS o La pareja de los últimos elementos en cada secuencia no pertenece a la LCS.
d.
Sea $S_{1}$ y $S_{2}$ las subsecuencias a trabajar, y $R$ la longitud de la subsecuencia común más larga:
- Si la pareja de $S_{1}[n], S_{2}[n]$ es parte de la LCS, es por que ambas son iguales, por lo tanto $R_{n_{1},n_{2}}=1+R_{n_{1}-1,n_{2}-1}$.
- Si la pareja de $S_{1}[n], S_{2}[n]$ no es parte de la LCS, entonces ambos son distintos.
	- Si $S_{1}[n]$ es parte de la LCS con algún otro elemento previo en $S_{2}$, entonces $R_{n_{1},n_{2}}=R_{n_{1},n_{2}-1}$
	- Si $S_{2}[n]$ es parte de la LCS con algún otro elemento previo en $S_{1}$ entonces $R_{n_{1},n_{2}}=R_{n_{1}-1,n_{2}}$
e.
$$
R_{n_{1},n_{2}}=\begin{cases}
1+R_{n_{1}-1,n_{2}-1},&S_{1}[n]=S_{2}[n] \\
\text{max}(R_{n_{1},n_{2}-1},R_{n_{1}-1,n_{2}})&\text{En otro caso}
\end{cases}
$$
f.
$$
R_{i,j}=\begin{cases}
1+R_{i-1,j-1},&S_{1}[i]=S_{2}[j] \\
\text{max}(R_{i,j-1},R_{i-1,j})&\text{En otro caso}
\end{cases}
$$
g.
La memoización se realizará en una matriz, donde las filas ($i$) representan el i-ésimo objeto de la primera secuencia; y las columnas ($j$) representan el j-ésimo objeto de la segunda secuencia
h.
En el caso de que la primera secuencia sea nula, la longitud máxima será 0, ya que no hay ningún objeto.
En el caso de que la segunda secuencia sea nula, la longitud máxima será 0, ya que tampoco hay ningún objeto.
i.
```Pseudocode
procedure LCS(n1, n2, S1, S2)
	memo = memo[n1+1, n2+1]
	rec = rec[n1+1, n2+1]
	memo[0,j] = 0, for all j
	rec[0,j] = "", for all j
	memo[i,0] = 0, for all i
	rec[i,0] = "", for all i
	
	for i=1...n1 do
		for j=1...n2 do
			if S1[i] = S2[j] then
				memo[i,j] = 1 + memo[i-1,j-1]
				rec[i,j] = rec[i-1,j-1] + S1[i]
			else
				if memo[i-1,j] > memo[i,j-1] then
					memo[i,j] = memo[i-1,j]
					rec[i,j] = rec[i-1,j]
				else
					memo[i,j] = memo[i,j-1]
					rec[i,j] = rec[i,j-1]
				end if
			end if
		end for
	end for
	
	return memo[n1,n2], rec[n1,n2]
end procedure
```