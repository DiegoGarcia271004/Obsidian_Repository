---
date: 2025-11-03
tags:
  - "#bit-masking"
aliases:
  - máscara de bits
class: apunte
area: "[[Análisis de Algoritmos.base|Análisis de Algoritmos]]"
group: University
---
# ¿Qué son las máscaras de bits?
Las cadenas binarias pueden ser bastante útiles para codificar información en ellos, como puede ser banderas o identificadores. Ahora, cuando se recibe la cadena binaria, es posible que haya información que nos interese y otra que no veamos necesaria. 

Entonces, para eso se hace *una máscara*, un filme o filtro que solo deja pasar la información necesaria y obstruye/oculta la que es irrelevante con la ayuda de operaciones binarias. Por ejemplo, digamos que un byte, una cadena binaria de ocho bits, contiene información de banderas.

```
cadena = 0b11010110
```

Nos interesa saber si la tercera bandera se encuentra levantada, entonces, creamos una máscara que tenga un `1` en esa posición, el tercer bit:

```
mascara = 0b00000100
```

Y luego, usamos la operación AND para observar si, en efecto, el tercer bit en la cadena original es un `1` o no.

```
cadena & mascara = 0b00000100
```
## ¿Por qué usar máscaras?
Las cadenas binarias pueden ser usadas para codificar información de conjuntos, y con esto, las operaciones binarias son equivalentes a la aritmética de conjuntos, haciendo que la manipulación de conjuntos sea más sencilla y extremadamente rápida de hacer para las computadoras, pues las operaciones binarias se ejecutan a nivel de hardware.

Además, se puede codificar la cantidad de subconjuntos que tiene un conjunto, pues se sabe que siempre es una potencia de 2. 


# Operaciones a nivel de bits

## AND

En el contexto de operaciones a nivel de bits, el operador AND toma dos números enteros y realiza la operación AND lógica para cada par correspondiente de bits.
El resultado en cada posición es 1 si el bit correspondiente de los dos bits es 1, en cualquier otro caso es 0.
**Ejemplo:**
```
    0101
AND 0011
    -----
    0001    
```

## OR

De igual forma que con el AND, el operador OR toma dos números enteros y realiza la operación OR lógica a cada uno de los pares de bits correspondientes.
El resultado para cada posición es 1 si para al menos uno de los dos bits es 1, es decir, que el resultado será 0 únicamente en el caso que ambos bits del par sean 0.
**Ejemplo:**
```
    0101
OR  0011
    -----
    0111
```

## NOT

El NOT bitwise (bit a bit) es una operación unitaria, es decir que solo se aplica a un único operando, que aplica la negación lógica a cada bit, invirtiendo los bits del número, de tal manera que los 0 se vuelven 1 y, de igual manera, los 1 se vuelven 0.
**Ejemplo:**
```
NOT 0101
	= 1010
```

## XOR

El XOR bitwise, toma dos números enteros y aplica la operación OR exclusivo a cada par de bits correspondientes.
El resultado de aplicar esta operación resulta en 1 solamente si el par de bits es distinto entre sí; es decir que dará como resultado 0 en el caso que ambos registros son iguales:
```
	0101
XOR 1011
	----
	1110
```
