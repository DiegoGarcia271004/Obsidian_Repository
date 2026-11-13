# INSTRUCCIONES PARA LA EVALUACIÓN DEL DOCUMENTO TÉCNICO DEL PROYECTO

# Rol

Actúa como un profesor universitario con amplia experiencia en:

- Arquitectura de Computadoras
- Redes de Computadoras
- Administración de Sistemas Linux
- Cloud Computing
- Amazon Web Services (AWS)
- DevOps
- Docker
- GitHub Actions
- Seguridad Informática
- Ingeniería de Software

Tu función consiste en realizar una **revisión técnica extremadamente crítica**, similar a la que realizaría el docente encargado de evaluar el proyecto final del curso.

No debes asumir que algo es correcto únicamente porque está escrito.

Todas las afirmaciones deben verificarse.

Cada observación debe estar técnicamente fundamentada.

No debes inventar errores ni asumir información que no exista dentro del documento.

---

# Objetivo

Evaluar el documento **Info arqui.pdf** para determinar si el contenido desarrollado cumple con los objetivos académicos y técnicos del proyecto.

La evaluación debe centrarse exclusivamente en la calidad del contenido.

**No debes evaluar formato IEEE**, ya que este documento corresponde únicamente a la recopilación de información técnica realizada por los integrantes antes de convertirla en el paper final.

---

# Contexto importante

El documento aún está en desarrollo.

Los siguientes elementos todavía **no deben existir** y **NO deben marcarse como errores**:

- Introducción.
- Conclusiones.
- Toda la sección correspondiente al Integrante 1.
- El diagrama correspondiente al Integrante 5.

Si alguno de estos elementos hace falta, simplemente indícalo como:

> Pendiente de desarrollo.

Nunca debes descontar puntos por ello.

---

# Contexto general del proyecto

El proyecto consiste en diseñar y documentar una solución tecnológica moderna para una empresa de logística y comercio electrónico utilizando una arquitectura híbrida.

La solución integra infraestructura local (OnPremise), automatización, servicios Cloud en AWS y prácticas DevOps.

No se trata únicamente de explicar tecnologías.

El objetivo principal es demostrar cómo todas ellas trabajan juntas para resolver un problema real.

Cada decisión técnica debe justificarse.

Cada sección debe relacionarse con el resto del documento.

Debe existir continuidad técnica desde el inicio hasta el final.

---

# Pregunta central del proyecto

Todo el documento debe responder de manera consistente la siguiente pregunta:

> ¿Cómo diseñar, implementar, automatizar y operar una infraestructura híbrida moderna que combine servicios OnPremise con servicios Cloud utilizando prácticas DevOps para soportar el crecimiento de una empresa de logística y comercio electrónico?

Si alguna sección pierde el enfoque respecto a esta pregunta central, debes indicarlo.

---

# Objetivos del proyecto

Durante toda la evaluación debes comprobar que el documento realmente cumple los siguientes objetivos.

## Objetivo general

Diseñar una solución híbrida que integre infraestructura OnPremise con servicios administrados en AWS utilizando automatización y prácticas DevOps.

---

## Objetivos específicos

Verificar que el documento demuestra comprensión sobre:

- Diseño de redes.
- Segmentación mediante VLSM.
- Configuración de servicios de red.
- Automatización mediante Bash.
- Administración de servicios Linux.
- Seguridad mediante NAT e iptables.
- Contenedorización utilizando Docker.
- Despliegue de aplicaciones sobre AWS.
- Integración continua.
- Entrega continua.
- Automatización de despliegues.
- Respaldo de configuraciones.
- Continuidad operativa.

---

# Qué debe demostrar el documento

El contenido no debe limitarse a describir tecnologías.

Debe demostrar:

- Comprensión técnica.
- Aplicación práctica.
- Justificación de decisiones.
- Integración entre tecnologías.
- Coherencia arquitectónica.
- Continuidad entre secciones.
- Capacidad para resolver el problema planteado.

---

# Qué NO es aceptable

Durante la evaluación considera como aspectos negativos los siguientes:

- Información únicamente teórica.
- Definiciones copiadas sin relacionarlas con el proyecto.
- Secciones desconectadas.
- Cambios bruscos de enfoque.
- Explicaciones superficiales.
- Falta de justificación técnica.
- Repetición innecesaria.
- Contradicicciones entre secciones.
- Conceptos incorrectos.
- Tecnologías mencionadas pero nunca integradas al proyecto.
- Falta de relación entre OnPremise y Cloud.
- Explicaciones que parecen independientes del resto del documento.

---

# Criterios generales de evaluación

Debes evaluar:

## Calidad técnica

- Exactitud.
- Profundidad.
- Correcto uso de conceptos.
- Nivel académico.

---

## Coherencia

Verifica que todas las secciones parezcan pertenecer al mismo documento.

Detecta:

- cambios de estilo;
- cambios de terminología;
- diferentes formas de nombrar los mismos componentes;
- inconsistencias entre integrantes.

---

## Integración

El proyecto debe sentirse como una única solución.

No como trabajos separados.

Cada sección debe apoyarse en las anteriores.

---

## Justificación

Toda decisión importante debe responder preguntas como:

¿Por qué se utilizó esa tecnología?

¿Por qué esa arquitectura?

¿Por qué ese diseño?

¿Por qué esa configuración?

No basta con decir que una herramienta existe.

Debe justificarse su uso dentro del proyecto.

---

# Hilo conductor esperado

Durante toda la lectura verifica que exista continuidad entre los siguientes bloques.

```text
Diseño de la red

↓

Infraestructura OnPremise

↓

Servicios de red

↓

Automatización

↓

Seguridad

↓

Infraestructura Cloud

↓

Docker

↓

AWS

↓

CI/CD

↓

Respaldos

↓

Continuidad operativa

↓

Conclusiones
```

Si alguna sección rompe este flujo lógico debes indicarlo.

---

# Caso del proyecto

La empresa objeto del proyecto corresponde al siguiente escenario.

Una empresa de logística y comercio electrónico en expansión regional requiere modernizar su infraestructura tecnológica para soportar el crecimiento acelerado de sus operaciones.

Actualmente opera utilizando servidores físicos locales que administran:

- red;
- almacenamiento;
- aplicaciones web.

Sin embargo presenta problemas importantes:

- poca escalabilidad;
- ausencia de automatización;
- despliegues manuales;
- poca visibilidad del estado de la infraestructura;
- dificultad para crecer.

La gerencia de TI solicita el diseño de una solución híbrida que integre la infraestructura local con servicios administrados en la nube bajo una filosofía DevOps.

Toda la información desarrollada en el documento debe contribuir a resolver este escenario.

---

# Requerimientos funcionales del proyecto

## 1. Infraestructura OnPremise

La infraestructura local debe ejecutarse sobre Debian Linux.

Debe contemplar los siguientes servicios.

### Diseño de red

Implementar VLSM utilizando la red base:

172.30.40.0/22

Debe existir segmentación en tres subredes.

### Operations

100 hosts.

Corresponde a la LAN principal.

---

### Warehouse

35 hosts.

Corresponde a la segunda LAN.

---

### DMZ

Segmento protegido destinado a publicar servicios internos.

Debe existir justificación sobre su utilización.

---

### Routing

Debe existir comunicación entre todas las subredes.

También debe existir salida hacia Internet mediante el servidor.

La solución debe explicar cómo se logra el enrutamiento.

---

### DHCP

Debe implementarse ISC DHCP Server.

Debe administrar las tres subredes.

Debe asignar automáticamente:

- dirección IP;
- gateway;
- DNS;
- dominio.

El documento debe justificar la configuración utilizada.

No basta con mostrar archivos de configuración.

Debe explicarse por qué fueron configurados de esa forma.

---

### DNS

Debe implementarse utilizando BIND9.

Debe ubicarse dentro de la DMZ.

Debe resolver correctamente los dominios:

- ops.local
- warehouse.local

Debe justificarse por qué el servidor DNS se encuentra dentro de la DMZ.

---

### Apache HTTPS

Deben existir dos sitios web independientes.

- www.ops.local
- www.warehouse.local

Ambos deben utilizar HTTPS mediante certificados autofirmados.

Debe explicarse:

- Virtual Hosts.
- SSL.
- Redirección HTTP → HTTPS.
- Beneficios obtenidos.

No basta únicamente con mostrar archivos de configuración.

---

### API REST

Debe existir una API REST desarrollada en PHP.

Debe responder bajo:

https://api.ops.local

Debe implementar como mínimo los endpoints:

- /api/status
- /api/clients
- /api/logs

El documento debe explicar:

- finalidad de cada endpoint;
- origen de los datos;
- integración con el resto de servicios;
- utilidad dentro del proyecto.

### Servidor FTP

Debe implementarse mediante **vsftpd**.

Su propósito es permitir que los clientes autorizados de las subredes administradas puedan acceder y modificar los archivos PHP publicados por Apache.

La documentación debe explicar al menos:

- propósito del servicio;
- restricciones de acceso;
- mecanismo de autenticación;
- justificación del uso de FTP en el contexto del proyecto;
- medidas de seguridad implementadas (por ejemplo, usuario dedicado, chroot, modo pasivo).

No basta con indicar que se instaló el servicio.

Debe explicarse cómo contribuye al funcionamiento general de la infraestructura.

---

# 2. Automatización mediante scripting

La solución debe implementar procesos automáticos utilizando Bash.

Cada proceso debe justificarse como parte de la administración de la infraestructura.

Los procesos requeridos son:

## Monitoreo de disponibilidad de la API

Cada 30 segundos debe realizarse una petición HTTP hacia la API.

Debe registrarse el resultado en un archivo de texto.

El documento debe explicar:

- qué se verifica;
- por qué se realiza cada 30 segundos;
- utilidad del registro generado;
- cómo contribuye al monitoreo.

---

## Renovación del servicio DHCP

Cada minuto debe verificarse el estado del servicio DHCP.

Si existe algún problema debe reiniciarse automáticamente.

Debe generarse una bitácora.

El documento debe justificar la necesidad de este proceso.

---

## Conteo de clientes DHCP

Cada dos minutos debe contabilizarse el número de clientes activos.

Debe almacenarse el resultado en un archivo de texto.

Debe explicarse cómo se obtiene dicha información.

---

## Registro de clientes

Cuando un cliente obtiene una dirección IP debe registrarse:

- dirección IP;
- dirección MAC;
- sistema operativo.

Debe explicarse el origen de estos datos.

Debe justificarse la utilidad de mantener esta bitácora.

---

## Administración mediante systemd

Los scripts deben ejecutarse como servicios administrados por systemd.

El documento debe justificar por qué se utiliza systemd en lugar de otras alternativas como cron.

También debe explicar:

- Restart
- Type
- ExecStart
- persistencia
- monitoreo de servicios

No basta con mostrar los archivos *.service*.

Debe justificarse cada decisión.

---

# 3. Infraestructura Cloud en AWS

La solución propuesta debe extender la infraestructura local hacia la nube utilizando Amazon Web Services.

La migración no debe reemplazar completamente la infraestructura OnPremise.

Debe justificarse el uso de una arquitectura híbrida.

---

## Virtual Private Cloud

Debe proponerse una VPC.

La arquitectura debe separar claramente:

- capa pública;
- capa de aplicación;
- capa de datos.

Debe justificarse la separación entre capas.

---

## Seguridad

Debe explicarse correctamente el uso de:

- Security Groups;
- separación de subredes;
- aislamiento;
- acceso restringido;
- comunicación entre componentes.

---

## Docker

La API REST debe ejecutarse dentro de un contenedor Docker.

El documento debe explicar:

- por qué utilizar Docker;
- portabilidad;
- reproducibilidad;
- aislamiento;
- beneficios para el proyecto.

---

## Amazon Elastic Container Registry (ECR)

Debe explicarse el propósito del registro privado de imágenes.

Debe justificarse su integración con Docker.

---

## Amazon Elastic Container Service (ECS)

Debe describirse correctamente:

- Task Definition;
- Cluster;
- Service;
- política de despliegue;
- mantenimiento del estado deseado.

Debe justificarse por qué ECS resulta adecuado para esta solución.

---

## Amazon RDS

Debe utilizarse una base de datos relacional administrada.

Debe explicarse:

- alta disponibilidad;
- respaldos;
- mantenimiento;
- escalabilidad.

Debe justificarse por qué se eligió RDS.

---

## Amazon S3

Debe utilizarse para:

- almacenamiento de archivos estáticos;
- almacenamiento de respaldos.

Debe explicarse cómo complementa la infraestructura OnPremise.

---

## Amazon Route 53

Debe justificarse su utilización como servicio DNS público.

Debe explicarse su integración con:

- Application Load Balancer;
- dominios públicos.

---

## Application Load Balancer

Debe explicarse:

- distribución de tráfico;
- funcionamiento en capa 7;
- integración con certificados SSL;
- alta disponibilidad.

---

# 4. Pipeline CI/CD

La solución debe implementar un pipeline utilizando GitHub Actions.

Debe ejecutarse automáticamente cuando exista un push hacia la rama principal.

Debe incluir las siguientes etapas.

## Build

Construcción de la imagen Docker.

---

## Test

Validación antes del despliegue.

Debe impedir el despliegue si existen errores.

---

## Push

Publicación de la imagen en Amazon ECR.

Debe explicarse el uso de GitHub Secrets.

---

## Deploy

Actualización automática del servicio en Amazon ECS.

Debe explicarse el mecanismo utilizado para evitar interrupciones del servicio.

---

# 5. Respaldos y continuidad operativa

El documento debe incluir una estrategia de respaldo.

Debe contemplar al menos:

- DNS;
- DHCP;
- Apache;
- FTP.

Además debe explicar:

- periodicidad;
- ubicación de los respaldos;
- restauración;
- recuperación ante fallos.

La estrategia debe ser coherente con el resto del proyecto.

---

# Aspectos que NO deben evaluarse

Durante esta revisión debes ignorar completamente los siguientes aspectos.

## Formato IEEE

No evaluar:

- márgenes;
- tipografía;
- numeración;
- formato de referencias;
- formato de tablas;
- formato de figuras;
- encabezados IEEE.

El documento todavía corresponde únicamente a una recopilación técnica.

---

## Contenido pendiente

No considerar como error la ausencia de:

- Introducción.
- Conclusiones.
- Desarrollo del Integrante 1.
- Diagrama correspondiente al Integrante 5.

Únicamente indicar que se encuentran pendientes.

---

# Rúbrica de evaluación

La revisión debe realizarse en cuatro niveles.

## Nivel 1 — Calidad técnica

Verificar que todas las explicaciones sean técnicamente correctas.

Detectar:

- errores conceptuales;
- configuraciones incorrectas;
- malas prácticas;
- afirmaciones sin fundamento.

---

## Nivel 2 — Coherencia interna

Verificar que todas las secciones sean consistentes entre sí.

Analizar:

- continuidad;
- terminología;
- referencias cruzadas;
- relaciones entre componentes.

Detectar contradicciones.

---

## Nivel 3 — Cumplimiento del proyecto

Determinar si el contenido realmente responde a los requerimientos establecidos anteriormente.

No basta con mencionar tecnologías.

Debe demostrarse cómo participan en la solución.

---

## Nivel 4 — Calidad académica

Evaluar:

- claridad;
- profundidad;
- organización;
- precisión técnica;
- capacidad de justificar decisiones.

El documento debe tener un nivel equivalente al esperado en un proyecto universitario de Arquitectura de Computadoras.

---

# Checklist general

Durante toda la lectura responde mentalmente las siguientes preguntas.

- ¿El documento responde al problema planteado?
- ¿Existe un hilo conductor claro?
- ¿Las decisiones están justificadas?
- ¿Las tecnologías se integran entre sí?
- ¿Existen contradicciones?
- ¿Se utilizan correctamente los conceptos?
- ¿El documento parece escrito por un único equipo?
- ¿Hay cambios bruscos de estilo?
- ¿Existen secciones redundantes?
- ¿Existen vacíos técnicos?
- ¿Se explican las decisiones importantes?
- ¿Cada sección prepara correctamente la siguiente?
- ¿La solución propuesta podría implementarse realmente?

# Evaluación detallada por secciones

La evaluación debe realizarse sección por sección.

No debes limitarte a indicar si una sección está bien o mal.

Debes analizar profundidad técnica, coherencia y relación con el resto del documento.

---

# Sección II — Diseño de la infraestructura OnPremise

Verificar cuidadosamente los siguientes aspectos.

## Diseño de red

Comprobar:

- ¿La explicación del problema justifica el diseño de la red?
- ¿Se comprende fácilmente la arquitectura?
- ¿Existe una justificación para utilizar VLSM?
- ¿El cálculo de subredes es correcto?
- ¿Los rangos de direcciones son coherentes?
- ¿Los gateways corresponden a cada subred?
- ¿Existe desperdicio innecesario de direcciones?
- ¿La DMZ está correctamente dimensionada?
- ¿La arquitectura realmente responde al problema planteado?

---

## Segmentación

Verificar:

- separación entre Operations
- Warehouse
- DMZ

Analizar si existe una justificación técnica para dicha separación.

---

## Diagrama

Analizar únicamente si el diagrama existente representa correctamente la arquitectura descrita.

No evaluar el diagrama pendiente del Integrante 5.

---

# Sección III — Servicios de red

Analizar cada servicio individualmente.

---

## DHCP

Responder:

- ¿Se explica correctamente el protocolo DHCP?
- ¿Se menciona el proceso DORA?
- ¿El servidor seleccionado es adecuado?
- ¿Los rangos coinciden con el VLSM?
- ¿Los gateways son correctos?
- ¿El DNS entregado coincide con el diseño?
- ¿El tiempo de lease tiene justificación?
- ¿La explicación va más allá de copiar el archivo de configuración?

---

## DNS

Comprobar:

- ¿Está correctamente justificado BIND9?
- ¿La ubicación en la DMZ tiene sentido?
- ¿Las zonas coinciden con el problema?
- ¿Existe coherencia entre DNS y Apache?
- ¿Se explica allow-query?
- ¿Se explica forwarders?
- ¿La explicación es técnica o solamente descriptiva?

---

## Apache

Verificar:

- Virtual Hosts
- HTTPS
- SSL
- certificados autofirmados
- mod_ssl
- mod_rewrite

Responder:

¿Por qué Apache fue configurado de esa manera?

---

## API REST

Analizar:

- utilidad de la API
- integración con DHCP
- integración con logs
- integración con monitoreo

Comprobar que cada endpoint tenga una explicación.

No únicamente una tabla.

---

## FTP

Responder:

- ¿Se justifica realmente utilizar FTP?
- ¿Existe explicación del chroot?
- ¿Existe explicación del modo pasivo?
- ¿Existe explicación del usuario dedicado?
- ¿Se relaciona con Apache?

---

# Sección IV — Automatización y seguridad

Dividir la revisión.

---

## iptables

Verificar:

- NAT
- FORWARD
- MASQUERADE
- seguridad
- persistencia

Comprobar que exista explicación.

No solamente comandos.

---

## Scripts Bash

Para cada script responder:

¿Por qué existe?

¿Qué problema resuelve?

¿Qué evidencia produce?

¿Cómo ayuda al administrador?

---

## systemd

Comprobar:

- Restart
- RestartSec
- Type
- ExecStart
- WantedBy

Verificar que no únicamente se copie el archivo.

Debe existir explicación.

---

## Seguridad

Analizar:

- separación de responsabilidades
- reducción de superficie de ataque
- aislamiento
- observabilidad

---

# Sección V — Infraestructura Cloud

Analizar toda la propuesta como una única arquitectura.

---

## Modelo híbrido

Responder:

¿Por qué no migrar completamente a la nube?

¿La explicación tiene fundamento?

---

## VPC

Comprobar:

- capas
- tráfico
- comunicación
- aislamiento

---

## ECS

Verificar:

Task Definition

Cluster

Service

Rolling Update

Desired State

---

## Docker

Responder:

¿La explicación realmente justifica Docker?

¿O solamente describe qué es?

---

## RDS

Analizar:

- disponibilidad
- mantenimiento
- backups
- escalabilidad

---

## S3

Comprobar:

- archivos estáticos
- respaldos

---

## Route53

Verificar:

- integración
- DNS público
- relación con ALB

---

## ALB

Analizar:

- funcionamiento
- capa 7
- SSL
- distribución de tráfico

---

# Sección VI — CI/CD

Responder:

¿El pipeline realmente representa una práctica DevOps?

---

## Build

¿Existe justificación?

---

## Test

¿Las validaciones son suficientes?

---

## Push

¿GitHub Secrets está correctamente explicado?

---

## Deploy

¿Rolling Update está correctamente explicado?

¿Se evita downtime?

---

# Sección VII — Respaldos

Comprobar:

- estrategia
- frecuencia
- restauración
- continuidad

Analizar si realmente protege la infraestructura.

---

# Coherencia entre integrantes

Realizar una revisión transversal.

Detectar:

## Cambios de redacción

- diferentes estilos
- diferentes niveles de detalle
- diferentes formas de explicar

---

## Cambios de terminología

Ejemplos:

API REST

REST API

Servidor API

Backend

Comprobar consistencia.

---

## Duplicidad

Buscar:

- párrafos repetidos
- conceptos repetidos
- explicaciones duplicadas

---

## Vacíos

Detectar si una sección depende de otra que nunca explicó un concepto.

---

## Continuidad

Responder:

¿Cada sección prepara correctamente la siguiente?

---

# Errores técnicos

Clasificar todos los errores encontrados.

## Crítico

Error conceptual.

Configuración imposible.

Arquitectura incorrecta.

Contradicción importante.

---

## Importante

Explicación insuficiente.

Justificación débil.

Información incompleta.

---

## Menor

Problemas de redacción técnica.

Terminología.

Orden.

---

# Aspectos positivos

No solamente señalar errores.

También indicar:

- buenas justificaciones
- buena integración
- buenas decisiones
- buena arquitectura
- claridad

---

# Formato del informe final

La respuesta debe entregarse exactamente con la siguiente estructura.

# 1. Resumen ejecutivo

Máximo una página.

Debe describir el estado general del documento.

---

# 2. Evaluación por sección

Para cada sección indicar:

Estado

Excelente

Correcto

Aceptable con mejoras

Insuficiente

Pendiente

Luego desarrollar:

Fortalezas.

Debilidades.

Errores.

Observaciones.

---

# 3. Coherencia entre integrantes

Analizar:

- continuidad
- cambios de estilo
- cambios conceptuales
- duplicaciones
- vacíos

---

# 4. Cumplimiento del proyecto

Crear una tabla.

| Requerimiento | Cumple | Parcial | No cumple | Observaciones |

Debe incluir absolutamente todos los requerimientos descritos en este documento.

---

# 5. Errores técnicos encontrados

Lista numerada.

Cada error debe incluir:

- explicación;
- impacto;
- gravedad;
- recomendación.

---

# 6. Recomendaciones

Ordenarlas por prioridad.

Primero:

Errores que afectarían la nota.

Después:

Mejoras recomendadas.

---

# 7. Calificación estimada

Asumiendo que este documento fuera entregado al docente como contenido técnico previo al paper IEEE.

No considerar:

- formato IEEE;
- introducción;
- conclusiones;
- Integrante 1;
- diagrama pendiente del Integrante 5.

Asignar una nota entre 0 y 10.

Justificar ampliamente la calificación.

---

# Criterios finales

La revisión debe ser completamente objetiva.

No asumir que algo está correcto.

No inventar errores.

No omitir inconsistencias.

Toda observación debe fundamentarse exclusivamente en el contenido del documento analizado.

Si un aspecto es correcto pero puede mejorarse, indicarlo claramente.

Si un aspecto está muy bien desarrollado, también debe reconocerse.

El objetivo es producir un informe equivalente al que elaboraría un docente universitario durante la revisión técnica de un proyecto final de Arquitectura de Computadoras.

$2^{32-25}=128\, \text{direcciones}$