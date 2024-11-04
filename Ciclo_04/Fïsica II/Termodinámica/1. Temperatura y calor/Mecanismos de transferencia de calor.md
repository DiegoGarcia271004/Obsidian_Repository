---
tags:
  - Física_II
---
Hemos hablado de materiales conductores y aislantes, los cuales permiten o impiden la transferencia de calor entre cuerpos. Sin embargo, el calor se puede transmitir de varias formas, como una olla puesta al fuego, hecha de un material que facilita y ayuda a la transferencia de calor a la comida, o un refrigerador, que impide el paso de calor a la comida que se encuentra adentro.
A continuación hablaremos acerca de los tres mecanismos de transferencia de calor, los cuales son *conducción, convección y radiación.* La conducción dándose entre dos objetos que se encuentran en contacto. La convección dado por el movimiento de un objeto de una región del espacio a otra. Y la radiación, siendo esta la transferencia de calor por medio de la radiación electromagnéticas.

---

## Conducción

Si se sujeta una varilla de metal a un extremo, y el otro extremo se coloca sobre una llama, el extremos que se sostiene se irá calentando cada vez más, aún si este no se encuentra en contacto directo con la llama, el calor llega al otro extremo de la varilla por conducción a través del material.
Si se mira desde un nivel atómico, los átomos de las regiones más calientes del material poseen una mayor energía cinética que aquellos que no están expuestos, lo que hace que estos sean empujados, que a su vez empujan a más átomos y así sucesivamente. Los átomos en si no se mueven dentro del material, pero la energía que contienen si.

Al transferir una cantidad de calor $dQ$ a una varilla en un tiempo $dt$, la rapidez del flujo de calor es $dQ/dt$. A esta rapidez se le conoce como *corriente de calor*, y se denota por $H$. Mediante observaciones se concluye que la corriente de calor es proporcional al área de la sección transversal de la varilla $A$, a la diferencia de temperatura $T_{H}-T_{C}$, e inversamente proporcional a la longitud de la varilla $L$, agregándole una constante de proporcionalidad llamada conductividad térmica del material, obtenemos la siguiente expresión:
$$
H=\frac{dQ}{dt}=kA \frac{T_{H}-T_{C}}{L}
$$
Si se quiere generalizar la expresión debido a que la temperatura que recorre el material no es uniforme, se puede agregar una coordenada $x$ a lo largo de la varilla y se generaliza el gradiente de temperatura:
$$
H=\frac{dQ}{dt}=-kA  \frac{dT}{dx}
$$
El signo negativo representa que el calor siempre fluye en la dirección de temperatura decreciente.

---

## Convección

La convección es la transferencia de calor provocada por el movimiento de una masa o un fluido de una región a otra. Como un ejemplo bastante común tenemos el aire expulsado por un ventilador. Si un fluido circula mediante esta forma o impulsado por un motor se le llama convección forzada, en cambio si el flujo se debe a diferencias de densidad causadas por expansión térmica, como el ascenso del aire caliente se le considera una convección natural.
Para este caso, la ecuación que describe la convección es muy compleja por lo que no se estudiará en esta unidad (ni en la material 🤡).

---
## Radiación

La radiación es un mecanismo de transferencia de calor provocado por ondas electromagnéticas como la luz visible, rayos infrarrojos, y la radiación ultravioleta. 
Todo cuerpo sin excepción de manera natural emite radiación electromagnética, si bien en menor o mayor cantidad.
A una temperatura de 20°C toda la energía transmitida se transporta en ondas de infrarrojo, conforme va a aumentando la temperatura, las longitudes de onda van disminuyendo, lo que permite a nuestro ojo observarlas, como cuando se calienta un carbón al rojo vivo.

La tasa de radiación producida por un cuerpo es proporcional al área superficial $A$ del cuerpo, y a la cuarta potencia de la temperatura absoluta (en Kelvin). A su vez depende de una constante $e$ conocida como emisividad, un número entre 0 y 1 que representa la relación entre la tasa de radiación de una superficie dada y la de un área igual de una superficie radiante ideal a la misma temperatura. Por lo que la corriente de calor $H$ esta dada por:
$$
H=Ae\sigma T^{4}
$$
donde $\sigma$ es la constante física fundamental llamada constante de Boltzmann, y cuyo valor numérico es de:
$$
\sigma=5.6704\times10^{-8}\, \frac{W}{m^{2}}K^{4}
$$

Es importante aclarar que si bien un cuerpo puede estar emitiendo radiación, el entorno en el que se encuentra también la emite, por lo que el cuerpo también recibe esta radiación, absorbiéndola.
Si el cuerpo se encuentra en equilibrio térmico con su entorno, $T=T_{s}$ y las tazas de radiación y absorción deben ser iguales. Para ello la tasa neta de absorción también estará dada por $H=Ae\sigma T_{s}^{4}$. Por lo que la tasa de radiación neta de un cuerpo a una temperatura $T$ en un entorno con temperatura $T_{s}$ está dada por:
$$
H_{\text{neta}}=Ae\sigma T^{4}-Ae\sigma T_{s}^{4}=Ae\sigma(T^{4}-T_{s}^{4})
$$
