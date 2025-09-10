---
date: 2025-09-04
tags:
  - "#probabilidad"
aliases:
  - Principio del palomar
class: apunte
area: "[[Instructoría.base|Instructoría]]"
group: Opportunities
---
# Principio del palomar
---
El principio del palomar es uno que puede que sea un poco complicado de comprender al principio, pero al final es un poco de lógica. Este principio tiene muchas formas de ser planteado, pero la forma matemática puede que tenga un poquito más de sentido.

---

> [!quote] Principio del palomar
> Una función que va de un conjunto finito a otro conjunto finito más pequeño no puede ser una función uno a uno (o inyectiva). Tiene que haber dos elementos del dominio cuya imagen sea el mismo elemento en el codominio.

---
Consideremos un caso sencillo. Hay una cuenta de Netflix con cuatro perfiles que está siendo usada por seis personas.
![[Pasted image 20250904144844.png|650]]

---
Hay muchas formas en las que las personas están usando las cuentas. Puede que dos perfiles sean usados por dos personas.
![[Pasted image 20250904145059.png|650]]

---
Un perfil sea compartido por tres personas...
![[Pasted image 20250904145122.png|650]]

---
Hay muchas formas en las que esto puede funcionar.
![[Pasted image 20250904145237.png|650]]

---
Pero una cosa es seguro, y esta garantizado matemáticamente: **Al menos un perfil está siendo usado por más de una persona.** Esto es lo que describe el principio del palomar.

---
## Principio del palomar generalizado

---
Puede que para problemas específicos, nos sirva saber si *al menos un perfil está siendo usado por más de una persona*; pero este principio se queda corto para problemas con conjuntos más grandes... o es muy específico para poder ser usado. Es por eso que se realizó una generalización más matemática.

---

> [!quote] Principio del palomar generalizado
> Para cualquier función $f$ que va de conjunto finito $X$ con $n$ elementos a otro conjunto finito $Y$ con $m$ elementos... Si existe un entero positivo $k$ tal que $k < n/m$, entonces existe un elemento $y\in Y$ que es la imagen de al menos $k+1$ elementos distintos del conjunto $X$.

---
El negocio de compartir la cuenta de Netflix resultó ser rentable, así que ahora tenemos 9 personas usando la misma cuenta de Netflix.
![[Pasted image 20250904152659.png|625]]

---
- Hay 9 personas usando la cuenta, y hay 4 perfiles.
- Definitivamente se sabe las 9 personas están usando la cuenta.
- Entonces, distribuyendo a las personas con los perfiles... sobra una persona.
- Esa persona **tiene** que estar usando un perfil que otras dos están usando.

---
- El conjunto $X$ es el de las 9 personas, y pues tiene $n=9$ elementos.
- El conjunto $Y$ es el de los 4 perfiles, con $m=4$ elementos.
- Dividiendo $n/m=9/4=2.25$
- Un entero $k$ menor que $9/4$ es $2$.
- Entonces, sabemos que un perfil está siendo usado por al menos $k+1=3$ personas.

---
## Ejercicios

---
> [!example] Ejercicio 1

Tenemos el siguiente conjunto: 
$$S=\{ 3,4,5,6,7,8,9,10,11,12 \}$$
Tomamos seis enteros de este conjunto. ¿Tiene que haber al menos dos enteros cuya suma sea 15? ¿Por qué?

---
> [!example] Ejercicio 2

Un curso de universidad consta de 40 estudiantes, los cuales varían en edad desde 17 hasta 34 años. Quieres hacer una apuesta, de que al menos $x$ cantidad de estudiantes comparte la misma edad. ¿Qué tan grande puede ser $x$, tal que aún esté garantizada tu victoria?

---
> [!example] Ejercicio 3

Un grupo de 15 ejecutivos tienen que compartir 5 asistentes. Se establece que un ejecutivo solo puede tener asignado un asistente; y que un asistente no puede estar trabajando para más de 4 ejecutivos. Demuestre que al menos 3 asistentes están asignados a 3 o más ejecutivos.

---
> [!example] Ejercicio 4

Sea $A$ un conjunto de seis enteros positivos, los cuales son menores que $13$. Demuestre que para cualquier configuración del conjunto $A$, debe existir al menos dos subconjuntos diferentes de $A$ tal que la suma de sus elementos sea el mismo resultado.


-c-c-c-c-c-c-