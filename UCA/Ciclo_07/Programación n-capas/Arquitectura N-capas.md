## Cliente-Servidor

Es una distribución de roles basada en petición y respuesta, el cliente realiza la petición al servidor, y este devuelve una respuesta con lo que sea que el cliente haya solicitado.

### Ventajas
- Centraliza los datos
- Es escalable horizontalmente (se le pueden agregar más servidores para agilizar el proceso de comunicación)
- Separación de operaciones

### Desventajas
- Dependencia al servidor (se cae el server y se va todo alv)
- Dependencia a la latencia de red (si no hay buena red, la información será más lenta en su comunicación)

## Monolítica

Es un estilo de desarrollo donde toda la aplicación de construye y es desplegada como una sola unidad. Es decir que todos los componentes se encuentran en un solo bloque de código. 

### Ventajas
- Desarrollo rápido
- Comunicación entre módulos rápida
- Despliegue simple

### Desventajas
- Pérdida de control de versiones
- Difícil de escalar
- Difícil de mantener en el tiempo

## MVC (Modelo Vista Controlador)

Es un [[Conceptos#Patrón de diseño|patrón de diseño]] que organiza el código de una aplicación separándolo en tres capas con responsabilidades definidas. Como se podrá inferir, el objetivo principal de este patrón es el de **separar responsabilidades**.

- La *vista* es lo que el cliente observa (toda la UI/UX).
- El *controlador* es el intermediario entre la vista y los modelos, recibe datos, decide que hacer con ellos y los redirige.
- El *modelo* son los datos que se maneja en la aplicación, esta capa incluye la base de datos y la lógica de negocio.

### Ventajas
- Separación de responsabilidades.
- Colaboración entre miembros

### Desventajas
- Repetición de código alta
- No es ideal para escalar sistemas grandes

## N-Capas

Es un **patrón** que organiza la aplicación en capas lógicas y/o físicas, donde cada capa tiene una responsabilidad específica y solo se comunica con la capa adyacente. 

### Ventajas
- Estructura clara
- Mantenible y escalable
- Reutilización de capas
- Versatilidad

### Desventajas
- Susceptible a baja cohesión (puede que la conexión entre capas sea un coñazo)
- Complejidad aumenta al aumentar capas (si tenés $2^{n}$ capas, te tenes que acordar de q hacen todas esas malditas capas y el código de q están hechas).
- Dependencias entre capas (si una se quita puede que todo valga vrg)

## Hexagonal

La idea de esta arquitectura es que el núcleo de la aplicación (la lógica del negocio) debe estar completamente aislada del mundo exterior, comunicándose únicamente a través de interfaces definidas llamadas puertos y adaptadores.

### Ventajas
- Testeable, mantenible, escalable
- Independencia y desacoplamiento de módulos.

### Desventajas
- Complejidad más alta
- Excesiva en la mayoría de proyectos

## Microservicios

Es un estilo arquitectónico donde una aplicación se construye como un conjunto de servicios pequeños, independientes  desplegables por separado, cada uno es responsable de una función específica y se comunica entre sí a través de la red.

### Ventajas
- Alto desacoplamiento
- Alta escalabilidad
- Independencia de servicios

### Desventajas
- Infraestructura compleja y cara de mantener
- Complejidad de red a medida escala
- Dependencia a la red.

## Broker

Es un patrón arquitectónico donde un componente intermediario central (el broker) que coordina la comunicación entre clientes y servidores de modo que ninguno de los dos necesita conocerse directamente. El broker actua como un mediador desacoplado.

