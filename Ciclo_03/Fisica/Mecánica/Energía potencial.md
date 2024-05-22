---
tags:
  - Física
---
Hemos visto los conceptos y como se definen la energía y el trabajo que se dan cuando existe un movimiento, no obstante, se puede visualizar el trabajo y la energía cinética de una manera distinta, un enfoque que dicta una energía asociada a la posición del sistema, no a su movimiento, esta sería la energía potencial.
La energía potencial sería una energía que es almacenada en los objetos de acuerdo a la posición en la que se encuentran, y esta reserva de energía se termina transformando en energía cinética de movimiento.

En la naturaleza se observan algunos casos en los que se puede aplicar la energía potencial que se encuentra almacenada en un sistema, como podría ser un objeto en un lugar alto, o un resorte estirado, estas energías se pueden clasificar como energía potencial gravitatoria y energía potencial elástica.
## Energía potencial gravitatoria

Anteriormente hemos visto que para que un objeto se mueva de su estado original, es necesario que intervengan fuerzas que cambien su velocidad, y al realizar el desplazamiento, se genera un trabajo.
En muchas ocasiones se puede decir que un sistema guarda cierta cantidad de energía que después utiliza para desplazarse, como colocar un objeto en un lugar alto y luego soltarlo, este caerá al suelo.
Pero, ¿De dónde salió la fuerza para que el objeto se moviera si partió del reposo? entonces, este caso nos puede dar indicios de que existe una energía que está asociada a la posición del cuerpo y respecto a su peso, y debido a lo visto antes, es energía potencial de tipo de gravitatoria.
Ahora se puede afirmar que la energía potencial va disminuyendo respecto un cuerpo va cayendo, y a su vez, la energía cinética aumenta.

Ya que conocemos esto, podríamos buscar una forma de describir la energía potencial gravitatoria, si se considera un cuerpo de masa $m$ el cual se esta moviendo a través del eje $y$, las fuerzas que actúan sobre el cuerpo sería el peso, apuntando al suelo, y ya que el trabajo es la fuerza multiplicada por el desplazamiento y si el objeto parte de una altura $y_{1}$ a una altura menor $y_{2}$ se tendría que el desplazamiento es $s=y_{1}-y_{2}$ y ya que la fuerza esta apuntando en la misma dirección que el desplazamiento, el trabajo ejercido por la gravedad $W_{grav}$ es positivo.
$$
W_{grav}=Fs=w(y_{1}-y_{2})=mgy_{1}-mgy_{2}
$$
Esta misma expresión se puede aplicar cuando se realiza un tiro vertical, solo que en este caso la altura $y_{1}$ sería menor a $y_{2}$, y todo esto junto con que la fuerza del peso se encuentra en sentido contrario al desplazamiento, el trabajo sería negativo.
En la ecuación planteada anteriormente se ve una diferencia de masa, gravedad y la altura del objeto, al producto de los tres datos es lo que se le conoce como la **energía potencial gravitatoria**.
$$
U_{grav}=mgy
$$
Debido a que la energía potencial gravitatoria va desde un punto inicial $U_{grav,1}$ hasta un punto final $U_{grav,2}$, el cambio de $U_{grav}$ se expresaría como $\Delta U_{grav}=U_{grav,2}-U_{grav,1}$ así que se puede expresar el trabajo $W_{grav}$ realizado por la fuerza de gravedad de la siguiente forma:
$$
W_{grav}=U_{grav,1}-U_{grav,2}=-(U_{grav,2}-U_{grav,1})=-\Delta U_{grav}
$$
El signo negativo de la expresión es indispensable, ya que garantiza que cuanto más lejos se encuentre un objeto de la tierra, el trabajo gravitacional es negativo debido a ir en contra del desplazamiento, y la energía potencial gravitatoria aumentará. Y, si el cuerpo baja, el trabajo aumentará y será positivo, y la energía potencial se disminuye y se vuelve negativa.

### Conservación de la energía mecánica

#### Cuando solo la gravedad realiza trabajo

Supongamos que se posee un cuerpo que cae en caída libre sin fuerzas externas que afecten su trayectoria (solo se considerará el peso), con una variación de velocidad, una velocidad $v_{1}$ en $y_{1}$ y $v_{2}$ en $y_{2}$. 
El [[Trabajo y energía cinética#Teorema trabajo-energía|teorema trabajo energía]] indica que el trabajo realizado por el objeto es igual al cambio de la energía cinética de este, a su vez, ya que el trabajo realizado es puramente influenciado por la gravedad, el trabajo sería $W_{tot}=W_{grav}=-\Delta U_{grav}$. Por lo tanto podemos afirma que $\Delta K=-\Delta U_{grav}$, o a su vez podemos decir que: $K_{2}-K_{1}=U_{grav,1}-U_{grav,2}$.
La cual se puede escribir como 
$$
K_{1}+U_{grav,1}=K_{2}+U_{grav,2}\,\text{   (Si solo la fuerza gravitatoria realiza trabajo)}
$$
La suma de $K+U_{grav}$ es lo que se conoce como la energía mecánica total del sistema, cabe aclarar que a sistema nos referimos al cuerpo de masa $m$ y a la tierra, ya que como dijimos, la energía potencial gravitatoria es una propiedad compartida entre el objeto y la tierra.

Por lo tanto, la ecuación vista anteriormente que si toda la energía se conserva (y si solo la fuerza gravitatoria realiza trabajo) la energía mecánica total se conserva.
Como ejemplo planteemos una pelota que se tira hacia arriba, la velocidad al tirarla va disminuyendo conforme aumenta su altura, es decir su energía cinética disminuye, mientras que su energía potencial aumenta. Algo parecido sucede cuando la pelota empieza a bajar, la energía potencial gravitatoria ira disminuyendo conforme se convierte en energía cinética y su velocidad aumenta. Ahora si en cualquiera de esos momentos, tomamos las dos energías y las sumamos podremos obtener siempre la misma energía mecánica, confirmando la conservación de energía.

> [!important] Variación de la energía potencial gravitatoria
> La energía potencial gravitatoria, por si misma no brinda ningún tipo de información y no pertenece a ningún cuerpo, sino que es una relación entre dos cuerpos (usualmente entre el cuerpo en cuestión y la tierra). Es por eso que la altura es respecto a la tierra, y lo que es realmente importante es la variación final de esta.

#### Cuando otras fuerzas realizan trabajo

En los casos anteriores veíamos que solo la fuerza gravitatoria realizaba trabajo sobre un cuerpo, sin embargo, difícilmente en la naturaleza solamente la gravedad realiza trabajo, en estos casos diversas fuerzas ejercen trabajo sobre el objeto, entonces ahora el trabajo total ejercido sobre un cuerpo serían el trabajo realizado por la fuerza gravitatoria (por que ésta siempre se encuentra) sumado al trabajo realizado por cualquier otra fuerza externa, y ya que eso da como resultado un trabajo total, esto se iguala a la diferencia de energía cinética.
Ya planteándolo cuantitativamente se representa de la siguiente manera:
$$
W_{total}=W_{otras} +W_{grav}=K_{2}-K_{1}
$$
Además ya que hemos visto que el trabajo realizado por la fuerza gravitatoria es el cambio de la energía potencial gravitatoria, podemos concluir:
$$
W_{otras}+U_{grav,1}-U_{grav,2}=K_{2}-K_{1}
$$
Ya expresándola de una forma más familiar:
$$
U_{grav,1}+K_{1}+W_{otras}=K_{2}+U_{grav_{,2}}
$$
El significado de esto es que el trabajo realizado por todas las fuerzas externas a la gravedad es igual al cambio en la energía mecánica total $E=K+U_{grav}$ del sistema. Si $W_{otras}$ es positiva, entonces la energía mecánica $E$ aumenta y $K_{2}+U_{grav,2}$ es mayor a $K_{1}+U_{grav,1}$, y si $W_{tot}$ es negativo, $E$ disminuye, utilizando esta forma, se puede llegar a la ecuación en la que solamente actúa la fuerza gravitatoria, en esos casos, el trabajo de fuerzas externas es 0, por lo tanto volvemos a la forma vista anteriormente.

## Energía potencial gravitacional en trayectorias curvilíneas

Hemos visto anteriormente diversas formas en las que se encuentra la energía potencial gravitatoria en trayectorias rectilíneas, pero, ¿Qué pasaría si la trayectoria de un objeto fuera curvilínea? Pues es lo que sabremos en esta sección. 
Si tenemos que un cuerpo se mueve en una trayectoria cualquiera, siempre actúa sobre el la fuerza gravitatoria (el peso) $\vec{w}=m\vec{g}=-m\hat{\jmath}$, en donde el desplazamiento del cuerpo está dado por $\Delta s=\Delta x\hat{\imath}+\Delta y \hat{\jmath}$, por lo tanto el trabajo efectuado por la fuerza gravitatoria estaría dado por:
$$
\vec{w}\cdot \Delta s=-mg\hat{\jmath}\cdot(\Delta x\hat{\imath}+\Delta y \hat{\jmath})
$$
Debido a que el trabajo efectuado por la fuerza gravitacional depende únicamente del desplazamiento vertical del objeto sin considerar el desplazamiento horizontal de este, por lo tanto el trabajo gravitacional estaría dado por el peso multiplicado por el desplazamiento del cuerpo en el eje vertical:
$$
W_{grav}=-mg(y_{2}-y_{1})=mgy_{1}-mgy_{2}=U_{grav,1}-U_{grav,2}
$$
Esto es similar a la ecuación del trabajo gravitacional planteado anteriormente, por lo tanto, se puede concluir que el trabajo realizado por la fuerza gravitacional **depende solamente de la componente vertical del desplazamiento**.

## Energía potencial elástica

Usualmente podemos encontrar diversas situaciones en las que encontramos energía potencial y esta no es de naturaleza gravitatoria, así como podría ser una banda elástica, que almacena energía al estar estirada y una vez de relaja, convierte esta energía almacenada en velocidad, es decir energía cinética. Gracias a esto podemos decir que los cuerpos elásticos (es decir que regresan a su forma y posición originales después de ser deformados) poseen una energía potencial dependiendo de que tan estirados se encuentren estos. A su vez, podemos encontrar este tipo de comportamiento en los resortes, que al igual que las bandas elásticas, estos al ser deformados, una vez se deja de ejercer fuerza sobre ellos, estos regresan a su estado original.

Por lo tanto podemos definir una energía potencial propia de estos tipos de objetos, la cual sería la **energía potencial elástica**.

### Energía potencial elástica de un resorte.

Anteriormente en [[Trabajo y energía cinética#Trabajo y energía con fuerza variable#Trabajo al estirar o contraer un resorte|trabajo ejercido sobre un resorte]] pudimos observar que para un resorte ideal, la fuerza necesaria para poder deformarlo esta dada por una función de fuerza $F=kx$ donde $k$ es la constante de fuerza del resorte, y x es la elongación del resorte.

Para poder obtener la energía potencial del resorte, podemos iniciar de la misma manera que con la energía potencial gravitatoria, diferenciándose en que la energía potencial gravitatoria es compartida entre un objeto y la tierra, mientras que la energía potencial elástica será almacenada únicamente en el resorte.

Propongamos un bloque de masa $m$ atado a un resorte con una constante de fuerza $k$ el cual esta sujetado a una pared el cual se puede mover horizontalmente en el eje $x$, si el resorte no esta estirado, inicialmente se encuentra en una posición $x=0$, si movemos el bloque en cualquier sentido, este estaría estirando o comprimiendo el resorte, seguidamente se suelta el bloque. Si desplazamos el bloque de una posición $x_{1}$ a una posición $x_{2}$ entonces estaríamos realizando un trabajo *sobre* el resorte dado por:
$$
W=\frac{1}{2}kx_{2}^{2}-\frac{1}{2}kx_{1}^{2}
$$
Al soltar el bloque y relajar el resorte, este tiende a regresar a su posición original, por lo tanto el resorte de la misma manera realizaría un trabajo, ya que en este caso parte de la posición final $x_{2}$ al estirarlo, regresaría a su posición inicial $x_{1}$, por lo tanto, si usamos la tercera ley de newton que dice que si ejercemos una fuerza sobre un objeto, este generará una fuerza de misma magnitud pero en sentido contrario, por lo tanto, el trabajo elástico realizado *por* el resorte estaría dado por:
$$
W_{el}=\frac{1}{2}kx_{1}^{2}-\frac{1}{2}kx_{2}^{2}
$$
Si tenemos que $x_{1} \text{ y } x_{2}$ son positivos con $x_{2}>x_{1}$ entonces el resorte estaría realizando un trabajo negativo sobre el bloque, ya que esta yendo en sentido contrario al desplazamiento del bloque que se mueve en en dirección $+x$, mientras que si $x_{2}<x_{1}$ entonces el resorte estaría realizando un trabajo positivo sobre el bloque.
Al poder entender esto, podemos expresar el trabajo en términos de una cantidad dada al inicio y al final del desplazamiento, esta sería $\frac{1}{2}kx^{2}$, y esto es lo que podemos definir como **energía potencial elástica**.
$$
U_{el} = \frac{1}{2}kx^{2}
$$
Podemos tomar la ecuación dada por el trabajo realizado *por* el resorte para poder obtener la energía potencial del resorte:
$$
W_{el}=\frac{1}{2}kx_{1}^{2}-\frac{1}{2}kx_{2}^{2}=U_{el,1}-U_{el,2}=-\Delta U_{el}
$$
Si un resorte se estira, el trabajo es negativo, y la $U_{el}$ aumenta, así que si el resorte se relaja el resorte realiza trabajo positivo y la $U_{el}$ disminuye, por lo tanto el resorte pierde energía potencial elástica, por lo tanto, cuanto más se comprima o estire un resorte, mayor energía potencial elástica poseerá.


> [!warning] Importante
> A diferencia de la energía potencial gravitatoria, con la energía potencial elástica no podemos elegir donde colocar el $x=0$, debido a que la energía es propia del resorte.
> Por lo tanto el $x=0$ deberá ser colocado en la posición donde el resorte no se encuentra deformado.

Recordando el [[Trabajo y energía cinética#Teorema trabajo-energía|teorema trabajo-energía]] el cual establece $W=K_{2}-K_{1}$, si tenemos un sistema en donde el único trabajo es ejercido por el resorte, entonces:
$$
W_{tot}=W_{el}=U_{el,1}-U_{el,2}
$$
Comparando esto con el teorema de trabajo-energía $W_{tot}=K_{2}-K_{1}$:
$$
U_{el,1}+K_{1}=K_{2}+U_{el,2}
$$
Entonces, en estos casos, la energía mecánica total del sistema estaría dada por $E=K+U_{el}$.

Para que esta forma funcione es fundamental que el resorte no posea masa, de lo contrario este factor intervendría al momento de tomar los cálculos.

## Situaciones con energía potencial gravitatoria y elástica

Las ecuaciones planteadas en la sección anterior funcionan si únicamente el resorte realiza trabajo, sin embargo, normalmente hay varios factores que realizan trabajo en un sistema, no solamente la fuerza del resorte es decir que existe un trabajo $W_{otras}$ realizado por cualquier otra fuerza, por lo tanto el trabajo total del sistema está dado por la suma de todos los trabajos realizados:
$$
W_{grav}+W_{el}+W_{otras}=K_{2}-K_{1}
$$
Debido a que sabemos que $W_{grav}=U_{grav,1}-U_{grav,2}$ y $W_{el}=U_{el,1}-U_{el,2}$, entonces definimos:
$$
K_{1}+U_{grav,1}+U_{el,1}+W_{otras}=U_{grav,2}+U_{el,2}+K_{2}
$$
O de forma resumida:
$$
K_{1}+U_{1}+W_{otras}=K_{2}+U_{2}
$$
Donde $U$ es la suma de las energías potenciales tanto elástica como gravitatoria, así que para abreviar, llamaremos a $U$ energía potencial.

Ya conocido todo esto, es necesario establecer el sistema en donde se trabajarán con las energías potenciales, este estaría compuesto por el cuerpo de masa $m$, la tierra y el resorte de constante $k$.
Si $W_{otras}$ es positivo, entonces $E=K+U$ aumenta, de igual manera, si $W_{otras}$ es negativo, entonces la energía mecánica del sistema disminuirá, y finalmente como tercer caso, si $W_{otras}=0$ entonces la energía mecánica total del sistema se conserva.
