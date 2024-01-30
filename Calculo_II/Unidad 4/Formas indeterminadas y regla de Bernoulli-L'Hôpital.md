---
tags:
  - Calculo2
  - Funciones
  - Matematica
---

## Indeterminaciones

Al momento de realizar límites de funciones y su tendencia, puede que lleguemos a ciertas indeterminaciones, es decir a unos resultados que en las matemáticas no es posible de determinar (de ahí indeterminación), como algunos ejemplos tenemos las siguientes indeterminaciones:

$$
\begin{align*}
& \frac{0}{0}& &\frac{\infty}{\infty}
\end{align*}
$$
Este tipo de indeterminaciones se conocen como indeterminaciones de tipo cociente.

A su vez existe la indeterminación de tipo producto:
$$
(0)(\infty)
$$
Finalmente encontramos las indeterminaciones de tipo exponencial:
$$
\begin{align*}
&1^{\infty}&&\infty^{0}&&0^{0}
\end{align*}
$$

Cualquiera de las indeterminaciones anteriores suelen aparecer al momento de intentar encontrar límites de funciones. A pesar de existir diversas formas de resolver límites indeterminados, hoy nos centraremos en una técnica especial, **La regla de Bernoulli-L'Hôpital**.


## Regla de Bernoulli-L'Hôpital

Es una forma en la que se pueden resolver las indeterminaciones de tipo cociente, esta regla dicta que el límite de la función es igual al límite del cociente de las razones de cambio de las funciones que conforman la función original.

$$
\lim_{ x \to c } \frac{f(x)}{g(x)} =\frac{0}{0} \vee \frac{\infty}{\infty}\Rightarrow \lim_{ x \to c } \frac{f(x)}{g(x)}=\lim_{ x \to c } \frac{f'(x)}{g'(x)} 
$$
**Ejemplo**:
Demuestre que $\lim_{ x \to 0 } \frac{\sin(x)}{x}=1$

$$
\begin{align*}
&\lim_{ x \to 0 } \frac{\sin(x)}{x}=\frac{\sin(0)}{0}=\frac{0}{0};\,A.B.L'H.&\text{(Aplicamos Bernoulli L'Hôpital)}\\
&\lim_{ x \to 0 } \frac{\cos(x)}{1}=\cos(0)=1\\
&Q.E.D 
\end{align*}
$$


A pesar de que la regla de L'Hôpital es bastante efectiva, esta solo se aplica en casos donde hay una indeterminación de tipo cociente, pero como ya vimos anteriormente, existen otros tipos de indeterminación además de las de tipo cociente, entre estas las de tipo producto y tipo exponencial. Sin embargo, podemos adaptarlas para que de esta manera podamos aplicar L'Hôpital a este tipo de indeterminaciones.

### Límites con indeterminaciones tipo producto

En este tipo de casos, debemos utilizar métodos algebraicos con el fin de encontrar una expresión equivalente que nos permita obtener una indeterminación de tipo cociente.

**Ejemplo**
$$
\begin{align*}
&\lim_{ x \to 0^{+} } x\ln\left( \frac{1}{x} \right)=(0)(\infty);\,\text{reescribiendo}\\
&\lim_{ x \to 0^{+} } \frac{\ln\left( \frac{1}{x} \right)}{\frac{1}{x}}=\frac{\ln\left( \frac{1}{0} \right)}{\frac{1}{0}}=\frac{\ln(\infty)}{\infty}=\frac{\infty}{\infty};\,A.B.L'H.\\
&\lim_{ x \to 0^{+} } \frac{-\frac{1}{x}}{-\frac{1}{x^{2}}}=\lim_{ x \to 0^{+} } x=0\\
&\therefore \lim_{ x \to 0^{+} } x\ln\left( \frac{1}{x} \right)=0;\, x\neq 0 
\end{align*} 
$$

