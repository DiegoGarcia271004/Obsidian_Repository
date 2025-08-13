Sea la superficie $S\subset \mathbb{R}^{3}$
$$
z=x^{2}+y^{2}
$$
y sea $C$ la curva sobre $S$ que proyectada sobre el plano $xy$ forma el cuadrado de lado 2 centrado en el origen, es decir, el borde del cuadrado se encuentra en los vértices $(±1,±1)$ recorrido en sentido antihorario.

Sea la función escalar:
$$
f(x,y,z)=\sqrt{ x^{2}+y^{2}+z^{2} }
$$
Calcular la integral de línea:
$$
\int _{C} f(x,y,z) \, ds 
$$
---
El enunciado nos indica que tenemos un cuadrado, formado por (obviamente) 4 lados, en este caso. No se puede parametrizar la curva de una sola vez, por lo que tendremos que trabajar cada curva por su parte.

**Curva 1:**
Nuestra primera curva es aquella que va desde $(-1,-1)$ a $(1,-1)$.
Por el comportamiento de la curva, podemos inferir que:
$$
x=t\quad y=-1
$$
Pero, la altura, el ejercicio ya nos dice cuanto es. Siendo esta $z=x^{2}+y^{2}$, entonces solo debemos de sustituir los valores de $x$ y $y$.
$$
z=t^{2}+1
$$
por lo que nuestra primera curva es:
$$
\vec{r}_{1}(t)=(t,-1,t^{2}+1)
$$
también es necesario recordar que:
$$
ds=\sqrt{ \left( \frac{dx}{dt} \right)^{2}+\left( \frac{dy}{dt} \right)^{2}+\left( \frac{dz}{dt} \right)^{2}  }dt
$$
$$
\frac{dx}{dt}=1\qquad \frac{dy}{dt}=0\qquad \frac{dz}{dt}=2t
$$
por lo que si nuestra integral es
$$
\int _{C}f(x(t),y(t),z(t)) \, ds 
$$
entonces lo que tendremos que resolver es:
$$
\int _{-1}^{1} \sqrt{ t^{2}+1+(t^{2}+1)^{2} }\cdot\sqrt{ 1+4t^{2} } \, dt
$$

**Curva 2:**
Para el resto de las curva, el procedimiento es el mismo, por lo que tomaré la libertad de no explicarlos a profundidad.

Vértices: $(1,-1)$ a $(1,1)$ 
$$
x=1\quad y=t\quad z=1+t^{2}
$$
$$
ds=\sqrt{ 1+4t^{2} }\,dt
$$
$$
\int _{-1}^{1}\sqrt{ 1+t^{2}+(1+t^{2})^{2} }\cdot\sqrt{ 1+4t^{2} } \, dt 
$$
**Curva 3:**
Vértices: $(1,1)$ a $(-1,1)$
$$
x=t\quad y=1\quad z=1+t^{2}
$$
$$
ds=\sqrt{ 1+4t^{2} }\,dt
$$
$$
\int _{-1}^{1} \sqrt{ t^{2}+1+(1+t^{2})^{2} }\cdot \sqrt{ 1+4t^{2} } \, dt
$$

Quizás ya vayan viendo por donde se va este asunto, pues resulta que para todas las integrales, ¡Es el mismo!, por lo que podemos simplemente obtener el valor de cualquiera de las integrales, y multiplicarlo por 4, y de esta manera obtendríamos el valor final.

---

Encuentre el área dentro de la rosa $r=\cos(2\theta)$ y fuera de la circunferencia $r=\frac{1}{\sqrt{ 2 }}$

---
Para este ejercicio, es muy importante la gráfica, en esta solución no se presentará. Pero si gusta, puede graficarla en su graficador de confianza.

También trabajaremos con simetría, obtendremos solo la mitad del primer pétalo que se forma, y lo multiplicaremos por la cantidad de simpétalos que haya.

Primero encontremos la intersección. Esta ocurre cuando las dos gráficas son iguales, es decir:
$$
\begin{gather*}
\cos(2\theta)=\frac{\sqrt{ 2 }}{2}\\
2\theta=\frac{\pi}{4}\\
\theta=\frac{\pi}{8}
\end{gather*}
$$
Por lo que podemos realizar nuestra integral en coordenadas polares:
$$
\int _{0}^{\pi/8}\int _{1/\sqrt{ 2 }}^{\cos(2\theta)}r \, dr  \, d\theta =\frac{1}{2}u^{2}
$$

---

Calcule el volumen encerrado arriba y abajo por $\rho=3$ y lateralmente por el cilindro delimitado por el exterior de la curva $x^{2}+y^{2}=y-x$ y el interior de la curva $x^{2}+y^{2}=2y$

---

Aquí tenemos una esfera de radio $3$, y dos cilindros, de igual forma, busquen graficarlos.
Al estar trabajando con cilindros, casi siempre es recomendable trabajar con coordenadas cilíndricas, así que pasémoslos.

$$
\begin{gather*}
\rho=3\\
\sqrt{ x^{2}+y^{2}+z^{2} }=3\\
x^{2}+y^{2}+z^{2}=9\\
r^{2}+z^{2}=9
\end{gather*}
$$
$$
\begin{gather*}
x^{2}+y^{2}=y-x\\
r^{2}\cos ^{2} \theta +r^{2}\sin ^{2}\theta=r\sin \theta-r\cos \theta\\
r=\sin \theta-\cos \theta
\end{gather*}
$$
$$
\begin{gather*}
x^{2}+y^{2}=2y\\
r^{2}\cos ^{2}\theta+r^{2}\sin ^{2} \theta=2r\sin \theta\\
r=2\sin \theta
\end{gather*}
$$
Ahora, buscamos los puntos de intersección entre los cilindros:
$$
\begin{gather*}
\sin \theta -\cos \theta=2\sin \theta\\
\end{gather*}
$$
Con esto, obtendremos que $\theta=\frac{3\pi}{4}$, pero al ver la gráfica, vemos que hay otro punto, que es $\theta=\frac{\pi}{4}$.
Ahora, al plantear las integrales, vemos que de 0 a $\frac{\pi}{4}$, solo se encuentra $r=2\sin \theta$. Así que en este intervalo trabajamos solamente con esta función:
$$
\int _{0}^{\pi /4}\int _{0}^{2\sin \theta}\int _{-\sqrt{ 9-r^{2} }}^{\sqrt{ 9-r^{2} }}r \, dz  \, dr  \, d\theta 
$$
Para después de $\frac{\pi}{4}$ ya encontramos también a $r=\sin \theta-\cos \theta$, por lo que debemos de agregarlo a los límites.

$$
\int_{1\pi/4}^{3\pi/4}\int _{\sin \theta-\cos \theta}^{2\sin \theta}\int _{-\sqrt{ 9-r^{2} }}^{\sqrt{ 9-r^{2} }} r\, dz  \, dr  \, d\theta  
$$

