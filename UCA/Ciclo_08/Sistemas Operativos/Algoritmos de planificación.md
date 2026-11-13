## FCFS (First Comme First Served)

Una computadora está ejecutando varios procesos al mismo tiempo. El sistema operativo debe administrar CPU.
Simular como el sistema operativo administra los procesos utilizando.
Calcular:
1. Tiempo de inicio
2. Tiempo de finalización
3. Tiempo de espera
4. Tiempo de retorno

Calcular:
1. Promedio de retorno

| Proceso | Llegada | Ejecución | Inicio | Finalización | Espera | Retorno |
| ------- | ------- | --------- | ------ | ------------ | ------ | ------- |
| P1      | 0       | 5         | 0      | 5            | 0      | 5       |
| P2      | 1       | 3         | 5      | 8            | 4      | 7       |
| P3      | 2       | 8         | 8      | 16           | 6      | 14      |
| P4      | 3       | 6         | 16     | 22           | 13     | 19      |
| P5      | 4       | 2         | 22     | 24           | 18     | 20      |
$$
\text{Espera}=T_{i}-T_{ll}\qquad\text{Retorno}=T_{f}-T_{ll}
$$

| 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  | 11  | 12  | 13  | 14  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P1  | P1  | P1  | P1  | P1  | P1  |     |     |     |     |     |     |     |     |     |
|     | P2  |     |     |     | P2  | P2  | P2  | P2  |     |     |     |     |     |     |
|     |     | P3  |     |     |     |     |     | P3  | P3  | P3  | P3  | P3  | P3  | P3  |
|     |     |     | P4  |     |     |     |     |     |     |     |     |     |     |     |

| 15  | 16  | 17  | 18  | 19  | 20  | 21  | 22  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|     |     |     |     |     |     |     |     |
|     |     |     |     |     |     |     |     |
| P3  | P3  |     |     |     |     |     |     |
|     | P4  | P4  | P4  | P4  | P4  | P4  | P4  |