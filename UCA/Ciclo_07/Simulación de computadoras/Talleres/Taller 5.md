1. Seleccionen un lenguaje de programación entre C, C++, Java o Python. a. Justifiquen su selección en base a las características del problema.
Debido a la simpleza del lenguaje y su inmenso parecido al lenguaje natural utilizado para el pseudocódigo, fue más sencillo la implementación mediante la utilización de Python, que a su vez hace más fácil el trabajo de comprender el código.

``` Python
#Implementación sin IA
def LimitlessKnapSack(V, W, n, C):

    memo = [[0 for _ in range(C+1)] for _ in range(n+1)]
    for i in range(1, n + 1):
        for j in range(1, C + 1):
            if W[i-1] <= j:
                memo[i][j] = max(memo[i-1][j], V[i-1] + memo[i][j - W[i-1]])
            else:
                memo[i][j] = memo[i-1][j]

    return memo[n][C]

#Código tomado de ChatGPT
def unbounded_knapsack(valores, pesos, n, capacidad):
    # dp[i] = valor máximo que se puede obtener con capacidad i
    dp = [0] * (capacidad + 1)
    for i in range(capacidad + 1):
        for j in range(n):
            if pesos[j] <= i:
                dp[i] = max(dp[i], dp[i - pesos[j]] + valores[j])

    return dp[capacidad]

  
W = [2, 3, 4, 5]
V = [3, 4, 5, 8]

print(LimitlessKnapSack(V, W, 4, 10))
print(unbounded_knapsack(V, W, 4, 10))
```

(4. ) Efectúen una análisis comparativo siguiendo los mismos lineamientos de la Parte 2 y la Parte 4
En lo general, el código generado por la IA es bastante parecido a la implementación sin hacer uso de esta (además de los nombres de variables).
Sin embargo, existen dos cambios importantes que los diferencian:
1. Primeramente, en la implementación sin IA se toma el caso en el que no se toma el objeto explícitamente mediante el uso de un `else`, mientras que en el caso de la implementación de la IA, el caso en el que el objeto no se toma ya se encuentra implementado implícitamente en la comparación del `max`.
2. La IA decidió no utilizar un arreglo bidimensional para la memo del problema, esto se debe a que al momento de eliminar la restricción de que un objeto pueda ser utilizado una sola vez permitiendo reformular el problema a: "se busca el mejor valor posible con la capacidad `C`". Lo que a su vez permite disminuir la cantidad de memoria utilizada durante el programa. 

