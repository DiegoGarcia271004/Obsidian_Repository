---
tags:
  - Física_II
---
Consideremos el trabajo efectuado por un sistema durante un cambio de volumen. Cuando un gas se expande, este empuja las paredes donde se encuentra contenido, por lo que teniendo en cuenta el sentido del [[Trabajo y energía cinética#Trabajo con fuerza constante en un ángulo relativo al desplazamiento|trabajo]], podemos afirmar que este siempre será positivo. Esto mismo pasará con cualquier fluido o sólido que se expanda a presión.
Esto se cumple si es una superficie estacionaria, sin embargo, cuando una de estas superficies se encuentran en movimiento (como podría ser un pistón), cuando el pistón se mueve para dejar más espacio al gas, las partículas que chocan contra la pared del pistón generan trabajo positivo, ya que la fuerza (aunque diminuta) se encuentra en la misma dirección que el desplazamiento del pistón. Mientras que, si este se encuentra disminuyendo el volumen del gas, las partículas al chocar con el pistón van en sentido contrario al desplazamiento del pistón, siendo así que estos generan trabajo negativo.

Con esto en mente, si tomamos un cilindro de área transversal $A$, y la presión ejercida sobre el cilindro es de $p$. Entonces su fuerza $F$ es $pA$. Si el pistón se está moviendo una muy pequeña distancia $dx$, entonces el trabajo realizado es de:
$$
dW=F\,dx =pA\,dx
$$
Pero anteriormente vimos que:
$$
A\,dx = dV
$$
por lo que podemos decir que:
$$
dW=p\,dV
$$
De esta manera podemos encontrar el trabajo realizado como:
$$
W=\int _{V_{1}}^{V_{2}}p \, dV 
$$
Si interpretamos esta ecuación desde un punto de vista gráfico, podemos obtener que el trabajo de un proceso termodinámico es igual al área bajo la curva de un diagrama $pV$.

---
### Trabajo efectuado en un sistema con presión constante

Con base a todo lo anterior, podemos encontrar y deducir que si la presión es constante, entonces el trabajo realizado por el sistema es de:
$$
W=p(V_{2}-V_{1})
$$

---
### Trabajo efectuado en un sistema con gases ideales

Si queremos obtener el trabajo realizado para realizar un cambio de volumen en un gas ideal, podemos partir de la [[Ecuaciones de estado#Gases ideales|ecuación de gases ideales]] para poder obtener la presión:
$$
pV=nRT\,→p=\frac{nRT}{V}
$$
entonces el trabajo realizado para cambiar el volumen es de:
$$
W=\int _{V_{1}}^{V_{2}} \frac{nRT}{V} \, dV 
$$
Debido a que $n,\,R,\text{ y }T$ son constantes, pueden salir de la integral:
$$
W=nRT \int_{V_{1}}^{V_{2}}  \frac{dV}{V} 
$$
(Si estas leyendo esto, asumo que sabes [[2.3 Funciones logarítmicas y exponenciales con otras bases|integrar]]) Por lo que:
$$
W=nRT\ln\left( \frac{V_{2}}{V_{1}} \right)
$$
