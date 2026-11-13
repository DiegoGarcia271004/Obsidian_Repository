Primero, lo obvio...
Todo programa necesita memoria, en ámbitos de programación cuando se dice memoria se refiere a la RAM.
Pero existen distintos tipos de memoria:
1. Registros
2. Caché
3. RAM
4. SSD
Estos están ordenados de más rápida a más lenta.

Pero...
## ¿Qué es realmente la RAM?

Es la memoria que el sistema utiliza para mantener datos que necesitan estar disponibles rápidamente mientras los programas estén ejecutándose.
```
0x0000 //10
0x0001 //"Hola"
0x0002 //Archivo.mp4
0x0003 //Virus.exe
```

Pero estas direcciones no representan la dirección física del contenido, sino que se encuentran en una dirección virtual.
### ¿Por qué existe las direcciones virtuales?

 ```
 Programa A                         Proceso A
 x -> dirección 1000                Virtual 1000 -> RAM 8000
 
 Programa B                         Proceso B
 y -> dirección 1000                Virtual 1000 -> RAM 1200
 
 ```

Porque 2 procesos pueden utilizar la misma dirección virtual, pero el sistema operativo puede mapearlos a lugares físicos diferentes.
En pocas palabras, para que nosotros no freguemos la memoria RAM con procesos mal hechos.

## Páginas

Una página es una unidad de división del espacio de direcciones virtuales.

```
Espacio de 16KB
 ---------
|Pagina 0 | - 4KB
 ---------
|Página 1 | - 4KB
 ---------
|Página 2 | - 4KB
 ---------
|Página 3 | - 4KB
 ---------
```

La página no es una división física, más bien una división lógica que divide la memoria virtual.

## Frames

A diferencia de la página, los frames son una división física de la RAM, dividiéndolo en bloques del mismo tamaño, y comparten el mismo tamaño que las páginas.
$$
\begin{gather*}

RAM = 16KB\\
\text{Page Size} = 4KB\\
\\
\text{Página 0} \implies \text{Frame 2}\\
\text{Página 1} \implies \text{Frame 0}\\
\text{Página 2} \implies \text{Frame 3}\\
\text{Página 3} \implies \text{Frame 1}\\
\end{gather*}
$$
---

## Página + offset

Supongamos que tenemos almacenados "0...4095". En la página 3.

Página: 3
Page Size = 4096 bytes
Pos (offset) = 1212

>**"Quiero la posición del número 1212 dentro de la página 3"**
$$
\text{VirtualAddress} = (\text{Page} \times \text{PageSize}) + \text{Offset}
$$

Sin embargo, si queremos encontrar la posición en la memoria física aún me falta un dato, el Frame.
En este caso usaremos Frame = 3.
$$
\text{Physical Address} = (\text{frame} \times \text{pageSize}) +\text{Offset}
$$
## Tiempo de lectura.

**Latencia:** Es el tiempo que pasa desde que solicitamos una operación hasta que comienza a producirse la respuesta.
$$
\begin{gather*}
\text{Velocidad} = 500\,\text{MB/s}\\
\text{Datos}=4\text{KB}\\
\\
\text{Tiempo de transferencia} = \frac{\text{datos}}{\text{velocidad}}\\
\text{Tiempo total} = \text{Tiempo de transferencia + Latencia}\\
\text{Tiempo de transferencia} = 
\end{gather*}
$$

> **Estudiar:** Algoritmos de planificación


