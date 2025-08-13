---
tags:
  - ANumérico
---
Al trabajar con métodos numéricos para la resolución de problemas matemáticos, los números tanto al trabajar con ellos como en su respuesta se pueden representar de diversas maneras.
Los sistemas numéricos más utilizados son:
- Decimal: Cálculos manuales 
- Binario: Cálculos por computadora
- Otros sistemas de numeración: Octal y Hexadecimal
Los cálculos realizados por computadora no se representan necesariamente en base 10 tradicional, sino en el significado relativo de las cifras según su posición con otras bases.

Como generalización:

Sea $\beta \in \mathbb{Z}$, $\beta\geq 2$ entonces cualquier número de base $\beta$ puede representarse mediante los dígitos: $0,1,2,\dots, \beta-1$ con una estructura numérica de la forma:
$$
d_{1}d_{2}d_{3}.d_{4}d_{5}d_{6}\qquad \text{donde } d_{i} \text{ dígitos base } \beta
$$
Con un valor decimal:
$$
d_{1}\beta^{2}+d_{2}\beta^{1}+d_{3}\beta^{0}+d_{4}\beta^{-1}+d_{5}\beta^{-2}+d_{6}\beta^{-3}
$$
**Ejemplo**
Base 10:
$$
197.345=1\cdot 10^{2}+9\cdot10^{1}+7\cdot 10^{0}+3\cdot 10^{-1}+4\cdot 10^{-2}+5\cdot 10^{-3}
$$
Base 2 (binario):
$$
1101.1011_{(2)}=1\cdot2^{3}+1\cdot 2^{2}+0\cdot 2^{1}+1\cdot 2^{0}+1\cdot 2^{-1}+0\cdot 2^{-2}+1\cdot 2^{-3}+1\cdot 2^{-4}=13.6875
$$
---

# Notación de punto flotante

La notación de punto flotante de estandariza de la forma del número así: $±0.d_{1},d_{2},d_{3},\dots,d_{k}\times \beta^{n}$.
Que se puede descomponer de la siguiente manera:
- Mantisa: $0.d_{1},d_{2},d_{3},\dots,d_{k}$
- $n$: Entero o exponente decimal que la caracteriza
- $\beta^{n}$: Expresión exclusivamente decimal

Por ejemplo, podemos expresar el número de Euler en notación de punto flotante con base 10:
$$
\beta=10\qquad2.718281828\dots\approx e \implies \text{Su representación: } 0.2718281828\dots \times10^{1}
$$
Un ejemplo con base binaria:
$$
\beta=2\qquad 1101.1011_{(2)} \implies 0.11011011_{(2)}\times 2^{4}
$$

Esto se puede entender de una mejor manera si hacemos la comparación con la notación científica, se posee un número y con las potencias de $10$, el punto se irá moviendo esa cantidad de dígitos, lo mismo en este último ejemplo. El $2^{4}$ no quiere decir que el número se multiplicará por $16$, sino que al estar en base binaria, el punto se moverá $4$ dígitos tal como se ve en el ejercicio.

---
# Representación numérica en máquinas

Las representaciones de los números en las máquinas tiene una limitante de utilizar únicamente una aproximación de estos. Esto debido a que las máquinas trabajan con representaciones finitas que dependerán del formato que la máquina maneje la aproximación.
Cuando se selecciona una máquina, se debe de poner atención a los siguientes parámetros:
- Base "$\beta$"
- Número de dígitos en la mantisa "$t$"
- El menor exponente de su característica "$N$"
- El mayor exponente de su característica "$M$"


> [!warning] Muy Importante
> El primer dígito que contiene la mantisa, debe ser **obligatoriamente** diferente de 0 ($d_{1}\neq 0$)

Finalmente, el conjunto de todos los números que pueden ser representados por la máquina se denota:
$$
F(\beta,t,N,M)
$$


$$
\begin{gather*}
\cos x=1-\frac{x^{2}}{2!}+\frac{x^{4}}{4!}-\frac{x^{6}}{6!}\\
\cos x-1+\frac{x^{2}}{2}-\frac{x^{4}}{24}=-\frac{x^{6}}{6!}\\
|\cos x-1+\frac{x^{2}}{2}-\frac{x^{4}}{24}|\approx\frac{x^{6}}{6!}\\
\frac{|\cos x-1+\frac{x^{2}}{2}-\frac{x^{4}}{24}|}{|x^{6}|}\leq\frac{1}{6!}
\end{gather*}
$$
