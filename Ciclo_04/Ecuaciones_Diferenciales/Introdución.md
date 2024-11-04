---
tags:
  - "#EcuacionesDiferenciales"
---
Aproximadamente desde séptimo grado, donde se empieza a estudiar el álgebra, se empieza a contemplar la resolución de ecuaciones algebraicas, en las cuales se buscan una o más soluciones a una expresión específica. Sin embargo, después de adentrarnos más en los abismos más profundos de las matemáticas, ya empezamos a encontrarnos y a trabajar con funciones, las cuales, como ya vimos anteriormente en cursos pasados, podemos trabajar con las derivadas e integrales de estas mismas funciones, es aquí donde entra el concepto de ecuaciones diferenciales.

## ¿Qué es una ecuación diferencial?

A diferencia de las ecuaciones algebraicas mencionadas anteriormente, con las ecuaciones diferenciales no buscamos un conjunto de valores que sirvan de solución a la ecuación, sino que se buscan funciones específicas que cumplan con las condiciones impuestas en la ecuación diferencial, para esto se harán uso de varios métodos de resolución, aplicando principalmente derivadas de funciones e integrales de estas mismas con el fin de resolverse.

## Elementos

En las ecuaciones diferenciales es posible encontrar diversos elementos de los cuales haremos uso.
A continuación presentaremos una lista de los elementos más comunes que se encuentran en estas.

1. **Variables:** Las variables son las principales partes de las ecuaciones, usualmente se suelen utilizar las variables $x$ y $t$, las funciones que buscaremos encontrar se encontraran en términos de estas variables.
2. **Funciones:** Las funciones son de las partes más importantes de las ecuaciones, estas (redundantemente) se encuentran en función de las variables. Para saber en función de que variable se encuentran, se pueden ver los diferenciales (Se explicarán más adelante) presentes en la ecuación, si la ecuación por si misma no especifica en función de que variables se trabajará, se puede tomar una variable a elección. Las funciones se suelen representar con las letras $y,\,f,\,g,\,g,\,h$ además, pueden representarse de la siguiente manera: $y(x),\, f(x),\,g(t),\,h(t)$ donde la variable con la cual se va a trabajar se encuentra dentro de los paréntesis.
3. **Derivadas:** Las derivadas son imperativas de encontrar en estas ecuaciones, estas serán las (obviamente) derivadas de las funciones mencionadas anteriormente, estas pueden estar tanto en notación de Lagrange ($y'$), como en la notación de Leibniz ($\frac{dy}{dx}$), a continuación se dará una lista de las posibles notaciones.

|       Tipo       | Notación Leibniz |    Notación Lagrange    |
| :--------------: | :--------------: | :---------------------: |
| Primera Derivada |       $y'$       |     $\frac{dy}{dx}$     |
| Segunda Derivada |      $y''$       | $\frac{d^{2}y}{dx^{2}}$ |
| Tercera Derivada |      $y'''$      | $\frac{d^{3}y}{dx^{3}}$ |
| n-ésima Derivada |    $y^{(n)}$     | $\frac{d^{n}y}{dx^{n}}$ |

---

## Comprobar que una familia de funciones es solución de una ED

Si se nos proporciona una ecuación diferencial, junto a una posible respuesta, es necesario comprobar que efectivamente esta función dada, si es solución.
Con el fin de realizar la comprobación, se deben de observar las derivadas que se encuentran en la ED, y obtenerlas a partir de la función. luego se ingresan en la ED y se busca que cumpla con la igualdad.

**Ejemplo:**

Probar que la función $y\ln(y)=x+\int _{0}^{x}e^{t^{2}} \, dt$ satisface la siguiente ecuación diferencial:
$$
y(1+\ln(y))y''+(y')^{2}=2xye^{x^{2}}
$$
Como observamos en la ED, se utiliza tanto la primera derivada como la segunda derivada de la función, así que empezaremos derivando nuestra función para obtenerlas.
$$
\begin{align*}
\frac{d}{dx}(y\ln(y))&=\frac{d}{dx}\left( x+\int _{0}^{x}e^{t^{2}} \, dt \right)\\
y'(\ln(y)+1)&=1+e^{x^{2}}\\
\frac{d}{dx}(y'(\ln(y)+1))&=\frac{d}{dx}(1+e^{x^{2}})\\
y''(\ln(y)+1)+\frac{(y')^{2}}{y}&=2xe^{x^{2}}\\
y(1+\ln(y))y''+(y')^{2}&=2xye^{x^{2}}
\end{align*}
$$
En este caso, pudimos ver que al derivar podemos llegar a obtener la ED proporcionada, por lo tanto se cumple que la función es una solución.

## Obtener una ED a partir de una familia de funciones dada

