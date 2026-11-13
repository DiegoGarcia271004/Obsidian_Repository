Los procesos ETL son una parte de la [[Arquitectura de una solución de BI#Integración de datos|integración de datos]], pero es un elemento importante cuya función completa el resultado de todo el desarrollo de la cohesión de aplicaciones y sistemas.

Este proceso se divide en 3 partes:

## Extracción
- Se extraen los datos desde los sistemas de origen
- Analizar los datos extraídos obteniendo un chequeo
- Interpretar este chequeo para verificar que los datos extraídos cumplen la pauta o estructura que se  esperaba. Si no fuese así, los datos deberían ser rechazados
- Convertir los datos a un formato preparado para inicial el proceso de transformación.

Exigir siempre que esta tarea cause un impacto mínimo en el sistema de origen

Si los datos a extraer son muchos, el sistema de origen se podría ralentizar e incluso colapsar, provocando que no pudiera volver a ser utilizado con normalidad para su uso diario

## Transformación

Esta fase aplica una serie de reglas de negocio o funciones sobre los datos extraídos para convertirlos en datos que serán cargados.
- Independientes
- Claras
- Posibles
- Con una finalidad útil para el negocio
La fase de transformación se ocupa de eliminar aquellos datos que puedan ser irrelevantes, desfasados, incorrectos o duplicados.


## Carga

En esta fase, los datos procedentes de la fase anterior son cargados en el sistema de destino.
Dependiendo de los requerimientos de la organización, este proceso puede abarcar una amplia variedad de acciones diferentes:
- Definir modo de carga de los datos
- Definir destino
- Registro de la carga realizada
- Atención oportuna de algún incidente

---

Gracias a los procesos ETL es posible que cualquier organización:
- Mueva datos desde una o múltiples fuentes
- Reformatee esos datos y los limpie, cuando sea necesario
- Los cargue en otro lugar como una base de datos, un data mart, o un datawarehouse.
Una vez alojados en destino, estos datos se analicen.

