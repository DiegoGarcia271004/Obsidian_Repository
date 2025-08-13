---
tags:
  - EMA
---
Tras haber trabajado con circuitos comunes (se asume que el lector ya ha trabajado con este tipo de circuitos), el lector terminará encontrando diversos circuitos los cuales no será posible reducirlos a un estado de resistencia equivalente, por esto mismo es que Kirchhoff como el superdotado que es, durante sus años de estudio planteó dos reglas para circuitos que facilitarían en gran medida el trabajar con circuitos más complejos.

## Regla de los nodos

La primera regla de Kirchhoff establece que para todo nodo que se encuentre en un circuito, la intensidad entrante neta debe ser *exactamente* igual a la intensidad neta saliente, es decir que al sumar las intensidades entrantes y salientes del nodo (estas últimas se les considera con un signo negativo) debe de dar 0:
$$
\sum I=0
$$
Un ejemplo para trabajar con esta regla es el siguiente ejemplo:

![[Kirchhoff1|center]] 
En este se puede ver que tanto la $I_{1}$ como la $I_{2}$ están entrando al nodo, por lo que las intensidades que salen en conjunto deben tener el mismo valor que las dos entrantes:
$$
I_{1}+I_{2}-I_{3}-I_{4}=0
$$
De esta forma se puede aplicar la primera ley de Kirchhoff.

## Regla de las mallas

La regla de las mallas establece que dentro de un circuito eléctrico, el diferencial de potencial en toda la malla debe ser el mismo una vez se completa el recorrido aún con sus caídas de potencial, por lo que su suma algebraica debe ser 0.
$$
\sum V=0
$$
![[Kirchhoff2|center]]
En el ejemplo anterior, si empezamos nuestro recorrido desde el lado positivo de la batería hasta el lado negativo, al obtener todos los cambios de potencial y sumarlos algebraicamente, este debe de dar 0.

