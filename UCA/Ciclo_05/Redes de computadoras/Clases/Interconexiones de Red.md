---
tags:
  - RedesDeComputadoras
---
Anteriormente hemos visto los protocolos de red, estos suelen ubicarse entre la primera y segunda capa del modelo OSI. 
Sin embargo, tenemos que avanzar en cuanto a las capas, en la tercera capa del modelo OSI tenemos la capa de **Red** y con ella nuevos protocolos que tenemos que estudiar.

TCP/IP es una seria de protocolo 


- Convertir la máscara de red
- Utilizar las fórmulas para las subredes $2^{n}\geq X$
- Calcular la nueva máscara de red
- Calcular la cantidad de host $2^{n}-2=\text{host}$ ($n$ es la cantidad de 0 en la nueva máscara)
- Calcular el salto $256-x$ ($x$ es el valor del octeto modificado)

160.50.7.0/16

**Máscara de red:**
11111111.11111111.00000000.00000000
255.255.0.0

**Calculando las subredes**
$$
\begin{gather*}
2^{n}\geq 10\\
n=4
\end{gather*}
$$
**Calculando la nueva máscara**
11111111.11111111.11110000.00000000
255.255.240.0

**Calculando cantidad de host**
$$
\begin{gather*}
2^{12}-2\\
4094
\end{gather*}
$$
**Calculando el salto**
$$
\begin{gather*}
256-240\\16
\end{gather*}
$$


| Dirección de red | Primera dirección de host asignada | Última dirección de host asignada | Dirección de broadcast |
| ---------------- | ---------------------------------- | --------------------------------- | ---------------------- |
| 160.50.7.0       | 160.50.7.1                         | 160.50.22.254                     | 160.50.22.255          |
| 160.50.23.0      | 160.50.23.1                        | 160.50.38.254                     | 160.50.38.255          |
| 160.50.39.0      | 160.50.39.1                        | 160.50.54.254                     | 160.50.54.255          |
| 160.50.55.0      | 160.50.55.1                        | 160.50.70.254                     | 160.50.70.255          |
| 160.50.71.0      | 160.50.71.1                        | 160.50.86.254                     | 160.50.86.255          |
| 160.50.87.0      | 160.50.87.1                        | 160.50.102.254                    | 160.50.102.255         |
| 160.50.103.0     | 160.50.103.1                       |                                   |                        |
| 160.50.119.0     |                                    |                                   |                        |
| 160.50.135.0     |                                    |                                   |                        |
| 160.50.151.0     |                                    | 160.50.167.254                    | 160.50.167.255         |

---

60.30.0.0 calcular 18 subredes

Ya que el primer octeto es menor a 126, es clase A

60.30.0.0/8

**Calcular la máscara**
11111111.00000000.00000000.00000000

**Calcular subredes**
$$
\begin{gather*}
2^{n}\geq 18\\
n=5
\end{gather*}
$$
**Calcular nueva máscara**
11111111.11111000.00000000.00000000

**Calcular cantidad de host**
$$
\begin{gather*}
2^{19}-2\\
524286
\end{gather*}
$$
**Calcular saltos de red**
$$
256-248=8
$$

| Dirección de red | Primera dirección de host asignada | Última dirección de host asignada | Dirección de broadcast |
| ---------------- | ---------------------------------- | --------------------------------- | ---------------------- |
| 60.30.0.0        | 60.30.0.1                          | 60.37.255.254                     | 60.37.255.255          |
| 60.38.0.0        | 60.38.0.1                          | 60.45.255.254                     | 60.45.255.255          |
| 60.46.0.0        | 60.46.0.1                          | 60.53.255.254                     | 60.53.255.255          |
| 60.54.0.0        | 60.54.0.1                          | 60.61.255.254                     | 60.61.255.255          |
| 60.62.0.0        | 60.52.0.1                          | 60.69.255.254                     | 60.69.255.255          |
| 60.70.0.0        | 60.70.0.1                          | 60.77.255.254                     | 60.77.255.255          |
| 60.78.0.0        | 60.78.0.1                          | 60.85.255.254                     | 60.85.255.255          |
| 60.86.0.0        | 60.86.0.1                          | 60.93.255.254                     | 60.93.255.255          |
| 60.94.0.0        | 60.94.0.1                          | 60.101.255.254                    | 60.101.255.255         |
| 60.102.0.0       | 60.102.0.1                         | 60.109.255.254                    | 60.109.255.255         |
| 60.110.0.0       | 20.110.0.1                         | 60.117.255.254                    | 60.117.255.255         |
| 60.118.0.0       | 60.118.0.1                         | 60.125.255.254                    | 60.125.255.255         |
| 60.126.0.0       | 60.126.0.1                         | 60.133.255.254                    | 60.133.255.255         |
| 60.134.0.0       | 60.134.0.1                         | 60.141.255.254                    | 60.141.255.255         |
| 60.142.0.0       | 60.142.0.1                         | 60.149.255.254                    | 60.149.255.255         |
| 60.150.0.0       | 60.150.0.1                         | 60.157.255.254                    | 60.157.255.255         |
| 60.158.0.0       | 60.158.0.1                         | 60.165.255.254                    | 60.165.255.255         |
| 60.166.0.0       | 60.166.0.1                         | 60.173.255.254                    | 60.173.255.255         |

---

| Departamento  | # host |
| ------------- | ------ |
| Ventas        | 200    |
| RRHH          | 1000   |
| Informática   | 1500   |
| Gerencia      | 130    |
| Mantenimiento | 60     |
| Total         | 2890   |

Se suman todos los host, y dependiendo del valor, se busca la clase que lo pueda contener, en este caso una clase B.

Ordenando por orden de host

| Departamento  | # Host | $n$ |
| ------------- | ------ | --- |
| Informática   | 1500   | 11  |
| RRHH          | 1000   | 10  |
| Ventas        | 200    | 8   |
| Gerencia      | 130    | 8   |
| Mantenimiento | 60     | 6   |
Para este ejercicio, trabajaremos con una IP: 190.0.0.0

| Red           | IP         | Primera IP | Última IP    | Broadcast    |
| ------------- | ---------- | ---------- | ------------ | ------------ |
| Informática   | 190.0.0.0  | 190.0.0.1  | 190.0.7.254  | 190.0.7.255  |
| RRHH          | 190.0.8.0  | 190.0.8.1  | 190.0.11.254 | 190.0.11.255 |
| Ventas        | 190.0.12.0 | 190.0.12.1 | 190.0.12.254 | 190.0.12.255 |
| Gerencia      | 190.0.13.0 | 190.0.13.1 | 190.0.13.254 | 190.0.13.255 |
| Mantenimiento | 190.0.14.0 | 190.0.14.1 | 190.0.14.62  | 190.0.14.63  |

**1° Subred**
Para la primera subred, la máscara sería:
11111111.11111111.00000000.00000000
Para encontrar el host se necesita un $n$ que $2^{n}-2\geq 1500$. Que para este caso sería $n=11$.
La nueva máscara será:
11111111.11111111.11111000.00000000
255.255.252.0
El salto será $256-248=8$ 

**2° Subred**
La nueva máscara será:
11111111.11111111.11111100.00000000
255.255.248.0
El salto será $256-252=4$ 

**3° Subred** 
La nueva máscara será:
11111111.11111111.11111111.00000000
255.255.255.0
El salto será $256-255=1$

**4° Subred**
La nueva máscara será:
11111111.11111111.11111111.00000000
255.255.255.0
El salto será $256-255=1$

**5° Red**
La nueva máscara será:
11111111.11111111.11111111.11000000
255.255.255.192
El salto será $256-192=64$

---

| Red   | Hosts |
| ----- | ----- |
| Red A | 2000  |
| Red B | 3000  |
| Red C | 4000  |
| Red D | 2000  |
| Red E | 1500  |
| Total | 12500 |
Ordenando

| Red   | Host | $n$ |
| ----- | ---- | --- |
| Red C | 4000 | 12  |
| Red B | 3000 | 12  |
| Red A | 2000 | 11  |
| Red D | 2000 | 11  |
| Red E | 1500 | 11  |

| Red   | IP         | Primera IP | Última IP    | Broadcast    |
| ----- | ---------- | ---------- | ------------ | ------------ |
| Red C | 170.0.0.0  | 170.0.0.1  | 170.0.15.254 | 170.0.15.255 |
| Red B | 170.0.16.0 | 170.0.16.1 | 170.0.31.254 | 170.0.31.255 |
| Red A | 170.0.32.0 | 170.0.32.1 | 170.0.39.254 | 170.0.39.255 |
| Red D | 170.0.40.0 | 170.0.40.1 | 170.0.47.254 | 170.0.47.255 |
| Red E | 170.0.48.0 | 170.0.48.1 | 170.0.55.254 | 170.0.55.255 |


**Red C**
11111111.11111111.11110000.00000000
255.255.240.0
Salto $256-240=16$

**Red B**
Igual que red C

**Red A**
11111111.11111111.11111000.00000000
255.255.248.0
Salto $256-248=8$

**Red D**
Igual que red A

**Red E**
Igual que red D