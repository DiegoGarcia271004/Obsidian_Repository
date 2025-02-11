---
tags:
  - Física_II
---
Si usted ha andado de metido, puede que en esta carpeta, en el archivo de anexos haya encontrado unos nombres algo extraños, estos nombres son tipos de procesos por los que puede pasar un sistema termodinámico, entre estos pueden estar los procesos Isocóricos, Isobáricos, Isotérmicos y Adiabáticos.

## Procesos adiabáticos

Un proceso adiabático se define como un proceso termodinámico el cuál posee la peculiaridad que durante la realización de este, no existe un intercambio de calor, es decir que el calor es 0 ($Q=0$), esto ya sea porque el sistema se encuentra aislado o que el proceso se de con tal rapidez que no permite este intercambio. Esto aplicado a la [[Energía Interna y Primera ley de la Termodinámica|primera ley de la termodinámica]]:
$$
U_{2}-U_{1}=\Delta U=-W
$$
Cuando un sistema es adiabático, al expandirse, realiza trabajo contra su entorno, y ya que este no está siendo "alimentado" con una fuente de calor externa al sistema, únicamente hay un "gasto", por lo que el cambio de energía interna del sistema es negativa

## Procesos isocóricos

Un proceso isocórico se da cuando el proceso del sistema termodinámico sucede a volumen constante, o que no existe una variación de volumen a lo largo de la realización del proceso termodinámico, de igual forma, esto se puede expresar utilizando la primera ley de la termodinámica:
$$
U_{2}-U_{1}=\Delta U=Q
$$
Para un sistema con volumen constante, el trabajo es 0, para entender el porque de esto, retomemos la ecuación del [[Trabajo realizado al cambiar el volumen]]:
$$
W=\int _{V_{1}}^{V_{2}}p \, dV 
$$
En este caso como el volumen se mantiene constante, entonces $V_{1}=V_{2}$:
$$
W=\cancelto{ 0 }{ \int _{V_{1}}^{V_{2}}p \, dV  }=0
$$
Por lo que se concluye que en efecto, el trabajo realizado es 0.

## Procesos isobáricos

Para los procesos isobáricos, la presión del sistema es constante. Ahora, si aplicamos esto a la ecuación de la primera ley de la termodinámica, ninguna de las cantidades ($\Delta U,\,V\,\text{ o }W$) se anulan, sin embargo, el trabajo ahora es más fácil de calcular, ya que como  la presión $p$ es constante, entonces:
$$
W=\int _{V_{1}}^{V_{2}}p \, dV=p \int _{V_{1}}^{V_{2}} \, dV=p(V_{2}-V_{1})  
$$
Por lo que para la primera ley de la termodinámica, obtenemos la siguiente expresión:
$$
U_{2}-U_{1}=\Delta U=Q-p(V_{2}-V_{1})
$$

## Procesos isotérmicos

Si usted es perceptivo, puede que sepa por donde va este asunto. Los procesos isotérmicos son procesos termodinámicos que mantienen la temperatura constante. De igual forma que con los procesos isobáricos, ninguna de las cantidades se anula, por lo que no nos "simplifica" la ecuación de la primera ley.
Sin embargo, en algunos casos especiales la energía interna del sistema depende únicamente de la temperatura, no de su presión ni su volumen. Estos casos se dan con los gases ideales, por lo que si se tiene un sistema termodinámico con gases ideales, su variación de energía interna es nula $\Delta U=0$, por lo que $Q=W$. Es decir que toda energía en forma de calor que entre al sistema debe salir en forma de trabajo.
Pero lo anteriormente mencionado (repito) solo se da en gases ideales, para el resto de los sistemas la energía depende de la presión y de la temperatura, por lo que $U$ podría variar aún si la temperatura se mantiene constate.

