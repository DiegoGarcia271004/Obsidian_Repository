---
tags:
  - "#ProbabilidadYEstadística"
---
## Conceptos básicos de funciones de probabilidad

Sea f(x) una función de probabilidad, se cumple que:
- $f(x)>0$
- $\sum f(x)=1$
La esperanza o el valor esperado de una función de probabilidad es de:
$$
E(x)=\sum xf(x)
$$
La varianza se define como:
$$
\sigma^{2}=E((x-\mu)^{2})=\sum(x-\mu)^{2}f(x)=E(x^{2})-\mu^{2}=\sum x^{2}f(x)-\mu^{2}
$$

---

# Funciones teóricas de probabilidad discreta
## Función binomial
Se utiliza cuando se tiene un experimento con únicamente 2 posibles resultados (usualmente éxito y fracaso) y cuyas probabilidades de ocurrencia se mantengan constantes.
Para estos se le define $p$ como la probabilidad de éxito y $q$ como la probabilidad del fracaso. 
Ya que $q$ es el complemento de $p$, entonces se puede definir como:
$$
q=1-p
$$
Si este proceso se repite $n$ ocasiones, entonces se conoce como proceso de Bernoulli, y se expresa de la siguiente forma:
$$
f(x)=\left( \begin{matrix}
n \\
x
\end{matrix} \right)p^{x}(1-p)^{n-x}
$$
Esto expresa la probabilidad de que en $n$ ocasiones se obtuvieron $x$ aciertos.

Para la ecuación de Bernoulli existen expresiones para obtener  la media y la varianza sin necesidad de realizar otra vez el proceso mencionado anteriormente, este es:
$$
\mu=np\qquad \text{y} \qquad \sigma^{2}=npq
$$

## Distribución hipergeométrica

Si en un proceso de Bernoulli no se puede garantizar la independencia de los ensayos, o la probabilidad de éxito no es constante, entonces debemos aplicar la distribución hipergeométrica.

Si tenemos una situación en la que queremos  extraer una cantidad $x$ de objetos con una característica específica de un conjunto de $N$ objetos, si tomamos una muestra $n$ entonces la probabilidad de obtener $x$ objetos está dada por la distribución:
$$
f(x)=\frac{\left( \begin{matrix} n_{1} \\
x \end{matrix} \right)\cdot \left( \begin{matrix} N-n_{1} \\
n-x \end{matrix} \right)}{\left( \begin{matrix} N \\
n \end{matrix} \right)}
$$
Donde $n_{1}$ es la cantidad de objetos que poseen la característica que buscamos.

La media y la varianza de esta distribución se pueden obtener mediante las expresiones:
$$
\mu=np\quad \text{y} \quad \sigma^{2}=npq\cdot \frac{N-n}{N-1}
$$
donde $p=n_{1}/N$ y $q$ sigue la definición dada en la distribución binomial.


## Distribución de Poisson

La distribución de Poisson nace a partir de la distribución Binomial, siendo este un caso donde se tiene una gran cantidad de repeticiones de un evento $n \to \infty$ y la probabilidad de que ocurra  un éxito es muy baja $(p \to 0)$. 
Entonces la distribución de Poisson está dada por la expresión:
$$
f(x)=\frac{e^{-\lambda}\cdot\lambda^{x}}{x!}, \quad \lambda=np
$$


Para el caso de los procesos de Poisson (que se suelen utilizar en casos donde suceden $x$ ocurrencias en un intervalo continuo) se utiliza que la media de que suceda el evento $x$ es $\mu=\lambda =np$.

### Procesos de Poisson

Si bien hemos obtenido que la distribución de Poisson aparece de un caso específico de la distribución binomial, los **procesos de Poisson** nos ayudan para ciertos casos donde la variable aleatoria $x$ es definida como la *cantidad de ocurrencias de un evento dentro de un intervalo continuo*.
En los proceso de Poisson, se puede mencionar en los enunciados que la media ($\lambda$) posee un valor dado en un pequeño intervalo, en caso de necesitar ampliar (o reducir) el intervalo sobre el cuál se busca evaluar.
Por ejemplo, si tenemos el caso de:
En un conmutador se reciben 1.2 llamadas por minuto entre las 10 y las 11. Suponiendo que las llegadas siguen una ley de Poisson, calcule la probabilidad de que:

a) En un minuto cualquiera entren 3 llamadas. 
b) Entre al menos una llamada en un intervalo de un minuto. 
c) Se reciban al menos 3 llamadas en un intervalo de 5 minutos. 
d) Entren 4 llamadas entre las 10:30 y las 10:35

a) 
Como mencionamos anteriormente, la media dada en el ejercicio podemos tomarla como nuestra $\lambda$, por lo que $\lambda=1.2$, así que para calcular la probabilidad de que en un minuto entren tres llamadas, sería:
$$
f(3)=\frac{e^{-1.2}(1.2)^{3}}{3!}=0.086744
$$
b) 
Para este caso, retomemos lo que sabemos de los complementos de una probabilidad. Estamos calculando la probabilidad de que al menos una llamada entre en un minuto, es decir que es la probabilidad de que lleguen cualquier número de llamadas a excepción del ninguna llamada, es decir:
$$
P(X\geq 1)=1-f(0)=1- \frac{e^{-1.2}(1.2)^{0}}{0!}=1-0.301194=0.698806
$$
c) 
Ya que sabemos que se reciben 1.2 llamadas como media en un minuto, es decir que si buscamos encontrar la probabilidad de recibir $x$ llamadas en 5 minutos, sería 5 veces la media, por lo que $\lambda=5(1.2)=6$:
$$
P(x\geq 3)=1-(f(0)+f(1)+f(2))=1- e^{-6}(1+6+18)=1-25e^{-6}=0.93803
$$
d)
De igual forma, ya que estamos trabajando con un intervalo de 5 minutos, volvemos a utilizar $\lambda=6$:
$$
f(4)=\frac{e^{-6}6^{4}}{4!}=0.1386
$$
