---
tags:
  - IREC
---
Un microprocesador es un circuito integrado de las computadoras que ejecuta programas que van desde el propio sistema operativo hasta las aplicaciones de usuario.

## Partes de un microprocesador

Un microprocesador esta conformado por varios transistores que componen los módulos internos.
- Unidad de control: Encargada de la lectura, codificación y ejecución de programas que se encuentran dentro de la memoria principal, algunos de los componentes que lo conforman son: Decodificador y contador de programas.
- Unidad de proceso: Realiza operaciones aritméticas y lógicas con números enteros y números decimales, algunos de sus componentes son: ALU (unidad aritmético lógica), acumulador y registro.
- Bus de entrada y salida: Es el cableado por donde el microprocesador se comunica con los periféricos y dispositivos de la tarjeta madre, sirven tanto para entrada de datos como para su salida.
- Memoria principal: Encargada de almacenar el programa a ejecutar.
- Reloj: Maneja un tren de pulsos que sincroniza los procedimientos a realizar al momento de ejecutar un programa. La frecuencia del reloj se mide en Hertz, y un reloj de computadora suele estar en el orden de los GHz, mientras mayor frecuencia posea el reloj del microprocesador, mayor rapidez poseerá este.

## Funcionamiento del microprocesador

Cuando se va a ejecutar un programa se realiza una serie de pasos dentro del microprocesador para su ejecución:
1. Primeramente se carga en la memoria el programa que se va a ejecutar, la unidad de control lee la instrucción del programa.
2. El decodificador de la unidad de control convierte la instrucción en lenguaje máquina y procede a ejecutarse.
3. En caso de que la instrucción sea alguna operación aritmética o lógica, se manda a la ALU para procesar la instrucción y se guarda el resultado en el acumulador de la unidad de proceso.
4. En el contador de programa de la unidad de control incrementa en 1 y se procede a leer la siguiente instrucción, repitiendo el proceso.
5. Finalmente, los resultados se envían a través del Bus de entrada y salida hacia los [[Estructura de una computadora#|periféricos]]. 

**Ejemplo**
Cuando nosotros movemos el mouse a través de nuestro escritorio, el microprocesador se debe de encargar de reflejar este movimiento en la pantalla de la computadora.
Esto se logra ya que en cada momento, el microprocesador manda la instrucción de actualizar la posición del ratón en todo momento, una vez actualizada, manda ordenes a la ALU de comparar estas posiciones en un sistema de coordenadas, y una vez realizado esto muestra este cambio en el monitor.
Este proceso se realiza muchísimas veces, por esto mismo es que nosotros podemos ver con gran fluidez el movimiento del cursor en la pantalla.
La cantidad de instrucciones que el procesador puede realizar en un momento está ligado a la frecuencia del reloj, he de aquí su velocidad.

---
## Núcleos

### Núcleos físicos

Los procesadores ejecutan las instrucciones de manera secuencial, es decir que no es posible realizar dos tareas a la vez. Para solucionar este problema, en los chips se agregan más de un procesador volviéndolos así en multinúcleos, cada uno de estos procesadores contiene su propia unidad de control y de proceso, mientras que comparten los mismos buses de entrada y salida. Estos procesadores trabajan a la misma frecuencia, resultando en una mayor eficiencia y velocidad al momento de realizar procesos

### Núcleos lógicos

A diferencia de los físicos, estos son resultados de la programación, estos núcleos no existen físicamente, si no que se hace creer a los procesadores que tienen más núcleos, lo que afecta en la velocidad del procesador pero aumenta en gran manera su eficiencia.

---

A cada instrucción que se pueda procesar al mismo tiempo en el chip del microprocesador se le llama *hilo o thread*. Al realizar una compra de uno de los chips de microprocesador, los vendedores suelen aportar tres datos:
1. Frecuencia del reloj
2. Número de núcleos
3. Número de hilos.
