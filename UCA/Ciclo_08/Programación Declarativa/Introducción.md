## Programación declarativa VS Programación imperativa

### Programación imperativa
La programación imperativa es prácticamente lo que se lleva haciendo desde el inicio de la carrera, es el paradigma de programación donde el desarrollador codifica exactamente lo que se piensa hacer y el programa se ejecuta verticalmente siguiendo las instrucciones especificadas.

Entre los lenguajes que aplican este tipo de programación se encuentra:
- C
- C++
- Java
- Python

> Si bien el paradigma de programación orientada a objetos es distinto, pero sigue siendo imperativo.


### Programación declarativa


#### Conceptos

**Lenguajes:**
- Prolog: Viene del francies: Programation et logique y está basado en la lógica simbólica o proposicional.
- Racket: Más orientado a cálculos.

**Características:**
- No poseen estructuras de control o flujo (nada de while ni for).
- Son altamente recursivos (here we go again)
- Las variables no se declaran
- Las variables se *ligan* y *unifican* (A1)
- En el recorrido de ejecución secuencial vertical, las variables no cambian de estado una vez se ligan a un valor.
- Utilizan notación prefija para la escritura de sus módulos e instrucciones. ($\cancel{a+b} \implies +ab$)
- Uno de ellos siempre retorna cierto o falso y el otro siempre retorna un valor calculado.
- Ambos se utilizan dentro del campo de la inteligencia artificial.
##### Conceptos dentro de la programación declarativa
**Objeto:** Es cualquier entidad presente en la realidad o en la ficción. En el lenguaje Prolog los objetos se escriben con la primera letra en minúscula:
- fido
- mesa
- kiwi
- anita
**Conocimiento:**
1. Datos adquiridos por una persona a través de la experiencia o la educación, la comprensión teórica o práctica de un asunto u objeto de la realidad.
2. Lo que se adquiere como información relativa a un campo determinado o a la totalidad del universo.
3. Conciencia o familiaridad adquirida por la experiencia de un hecho o situación.

Incluye el "saber qué" (*know what*), el "saber cómo" (*know how*) y el saber dónde (*know where*).

**Base de conocimiento:**
Em una analogía con las bases de datos, es el lugar donde se acumula o almacena el conocimiento. Incluye los datos específicos sobre objetos determinados y también la forma de manipularlos o hacer deducciones sobre ellos. (Es decir que en PD a los programas se les conocerá como *bases de conocimiento*).

El contenido de una base de conocimiento es:
- Hechos
- Relaciones
- Reglas

**Dominio:** Es el campo para el cual ese conocimiento es útil. Ejemplo: cardiología, reino animal, etc.

**Hechos:** Describen o muestran características de los objetos. Un hecho es una observación verificable y objetiva sobre un objeto.
El formato con el que se escriben en la base de conocimiento en Prolog es el siguiente:
```prolog
<hecho> (<objeto>)
```
Los símbolos '<' y '>' indican que en esa posición se colocan los identificadores de los elementos: el identificador del hecho por fuera y a la izquierda de los paréntesis; y el identificador del objeto dentro de los paréntesis.

**Relaciones:** En Prolog, el conocimiento acerca de los objetos se formaliza mediante un conjunto de relaciones que describen, de forma simultánea, las propiedades y las interrelaciones entre ellos. Las relaciones también son hechos.

Supongamos que queremos expresar el hecho de que "un pez tiene escamas". Este hecho, consta de dos objetos, "pez" y "escamas", u de una relación llamada "tiene". La forma de representar las relaciones es:
```prolog
tiene(pez, escamas).

% Otros ejemplos

come(kiwi, masa).
auto(toyota, land_cruiser, 2005, gris).
```

La abuela de Manuel es Estela: Si queremos establecer la relación abuela, debemos escribir `abuela(estela, manuel).`.
Pero, si a partir de la frase queremos establecer la relación nieto, deberíamos escribir. `nieto(manuel, estela).`.

**Reglas:** La regla es una cláusula de Horn, de la forma; $q:-p.$

**Clausula de Horn:** Los programas en prolog que constituyen reglas del tipo "modus ponens", es decir, "Si es verdad el antecedente, entonces es verdad el consecuente".

La forma de escribir las clausulas de Horn es al revés de lo acostumbrado en los cursos de MD. Por lo que primero se escribe el consecuente y después el precedente:
$$
q \leftarrow p
$$
en donde $\leftarrow$ se sustituye por $:-$ en la computadora. De esta forma, la cláusula de Horn se escriben así:
$$
q:-p
$$
Ejemplo:
```prolog
% El barco es grande
grande(barco).

% Kiwi es una lora
lora(kiwi)

% -- Ejemplos de propocisiones compuestas conectadas con 'Y' -- 

% Jaimito y Pepito son estudiosos
% equivale a: Jaimito es estudioso y Pepito es estudioso
estudioso(jaimito), estudioso(pepito).

% Jaimito es estudioso y Pepito no es estudioso
estudioso(Jaimito), \+ estudioso(pepito).

% Dori tiene aletas y dori tiene branquias y dori vive en el mar.
tiene(dori, aletas), tiene(dori, branquias), vive(dori, mar).

% -- Ejemplos de cláusulas de Horn --
pez(dori) :- tiene(dori, aletas), tiene(dori, branquias), vive(dori, mar).
% Si dori tiene aletas y dori tiene branquias y dori vive en el mar, entonces dori es un pez.

% Susituyendo los objetos por variables, se tiene:
pez(X) :- tiene(X, aletas), tiene(X, branquias), vive(X, mar).

```
