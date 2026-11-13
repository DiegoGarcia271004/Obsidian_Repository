## Planteamiento del problema
Se plantea que en una pequeña startup de desarrollo de aplicaciones móviles con ciertas limitaciones en personal dedicado a la gestión de servidores es necesaria una plataforma que permita la entrega del código desarrollado.
Debido a que se cuenta con presupuesto y tiempo de despliegue limitado, se propone una solución de una plataforma como servicio (PaaS) sobre una nube pública. De esta forma, la startup mantiene el control total de su código y la lógica de negocio, mientras que la plataforma se encarga de todo el proceso de aprovisionamiento, escalado, parchado y disponibilidad.
## Justificación de solución
El sistema propuesto no solo busca disminuir el problema, sino resolverlo; esto se logra debido a que:
- No es necesario que se gestione el servidor, ya que la configuración de este queda fuera del alcance del equipo, por lo que la startup solo debe centrarse en el desarrollo de código sin preocuparse por la gestión del servidor.
- La escalabilidad es automática, el servidor se auto regula dependiendo de las necesidades sin que se tenga que anticipar los tráficos.
- Foco en el desarrollo, debido a que el equipo no debe de preocuparse por toda la configuración que se tiene detrás, como se mencionó anteriormente, este puede centrarse únicamente en el desarrollo de código, ahorrando grandes cantidades de tiempo a la hora del desarrollo y despliegue.
- Costos variables, si se utilizara un servidor propio este costaría lo mismo el momento que se tiene un único usuario como si tuviera miles. Mientras que la plataforma se ajusta a la cantidad de uso, siendo que el gasto se mueve en la misma dirección que los ingresos, reduciendo el riesgo financiero de los primeros meses, cuando la demanda es aún incierta.

## Arquitectura propuesta
El esquema técnico conecta el flujo de la entrega continua con servicios administrados de AWS, de forma que cada uno de los componentes elimina una responsabilidad operativa concreta:
- Integración continua con GitHub. Con cada push realizado al repositorio dispara un pipeline de CI/CD que construye, prueba y despliega automáticamente las aplicaciones sobre una instancia de EC2 alojada dentro de la VPC con la finalidad de reducir el riesgo humano.
- Almacenamiento y autenticación con S3 y JWT. Con la ayuda de S3  se guardan los archivos y se respalda el módulo de autenticación basado en JWT servido vía Apache con PHP desplegable en Hostinger para permitir no solo la seguridad del servicio, sino que también disminuir costos en las consultas.
- DNS y servicios en tiempo real con Route53. Route53 enruta el tráfico con firebase, entregando notificaciones y sincronización en tiempo real. Para una app movil estos componentes son determinantes para la retención de usuarios como la funcionalidad principal del producto.  

