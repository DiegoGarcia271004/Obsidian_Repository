## Parte III

### Estructura de la memoización
La estructura a utilizar para la memoización dentro del problema dependerá de la cantidad de parámetros variables que el problema utilice. En este caso, se estaría utilizando una matriz ya que los subproblemas planteados quedan con dos índices variables: el índice del objeto utilizado, y la capacidad restante de la mochila.

### Significado de los índices
Como se mencionó anteriormente, los índices $i$ y $C$ representan el índice del objeto utilizado; es decir que se trata de la posición del objeto actual. Y a su vez, $C$ representa la capacidad restante de la mochila.

### Casos base
Para este problema solamente existe un solo caso base, el cuál sería cuando no hay ningún objeto inicial.
No se toma en cuenta el caso en el que solamente existe un objeto, aún puede ser derivado de la recurrencia general, ya que si por ejemplo, el único objeto sobrepasara la capacidad de la mochila, se tendría que tomar la decisión de no ingresarlo, por lo que no podría considerarse un caso base,
Por lo que se puede concluir que:
- En caso que no hubiera ningún elemento que ingresar, no habría ninguna suma de valores, ya que al no haber objetos, no hay nada que le de valor a la suma. por ente: $V_{0,W}=0$. De igual forma $V_{i,0}=0$.

### Bottom-Up o Top-Down
Para este problema se decidió hacer uso de bottom-up. Debido a que de esta manera es posible aplicar un bucle que llene la matriz en orden creciente, permitiendo que valores menores ya se encuentren dentro de la matriz al momento de realizar la verificación de dependencias.

### Pseudocódigo


```pseudocode
El diccionario de dependencias tiene la forma:
D = {1:[d1], 2:[d2], 3:[d3], ..., n:[dn]}

PROCEDURE DependentKnapsack(V, W, D, n, C)
                                        //donde D el diccionario de dependencias
	memo = memo[n+1][C+1]                 //matriz de memoización
	memo[0,j] = 0, para todo j            //Se inicializan todas las filas en 0
	memo[i,0] = 0, para todo i           //Se inicializan todas las columnas en 0
	
	for i = 1..n do
		for j = 1..C do
			if W[i-1] <= j then
				dep_satisfecha = true
				for d in D[i] do
					if memo[d,j - W[i-1]] == memo[d - 1,j - W[i-1]] then
						dep_satisfecha = false
						break
					end if
				end for
					
				if dep_satisfecha
					memo[i,j] = max(memo[i-1, j], V[i-1] + memo[i-1,j-W[i-1]])
				else
					memo[i,j] = memo[i-1,j]
				end if
			else
				memo[i,j] = memo[i-1,j]
			end if
		end for
	end for
	
	return memo[n,C]
end procedure
```

