# Docker 101

Docker es una tecnología que facilita la implementación, ejecución y gestión de aplicaciones en contenedores.
Existen alternativas a docker para el manejo de contenedores, entre ellas está **podman**.
Al instalarlo se instala el cliente, que permite realizar instrucciones POST a través de una API al Docker Daemon.
El Docker Daemon recibe dichas instrucciones a través de un endpoint y lo envía a containerd.
Containerd recibe las instrucciones para la creación de contenedores, instruye a la runc para la creación de estos. Sin embargo, este por si solo no puede realizar la creación de contenedores, sino que envía las instrucciones a Runc mediante la creación de una instancia de este y corre el contenedor.
Runc se encarga de interactuar con el núcleo del sistema operativo para reunir todas las construcciones necesarias para crear un contenedor.

## Ecosistema de Docker

**CLI**: Es la herramienta que permite la interacción con docker con los comandos mediante la consola.
**Compose**: Permite el montado de los contenedores de docker.


**DevContainers:** Extensión de VsCode que permite trabajar con docker. Permite abrir carpetas dentro de un contenedor y aprovechar las funciones de visual studio code.

CMD vs ENTRYPOINT: CMD es posible de alterar, mientras que entrypoint no se puede cambiar, y se puede definir en otro archivo.

Es un sistema de orquestación de contenedores de código abierto.
Originalmente fue desarrollado por Google, actualmente se encuentra mantenido por la CNCF, los kubernetes automatiza el despliegue, escalado y gestión de aplicaciones en contenedores.
También se le conoce como K8s (k+8 letras +s). Puede correr tanto en local como en cloud providers.

# Kubernetes
## Importancia

- **Alta disponibilidad:** Sin tiempo de inactividad, nada debería de caerse, es decir que se mantiene al aire en todo momento.
- **Escalabilidad:** Ajuste automático según la demanda.
- **Portabilidad:** Funciona en cualquier tipo de entorno (nube, local, híbrido)
- **Autorrecuperación:** En caso del fallo de un contenedor, reinicia estos automáticamente.
- **Gestión de secretos y configuración:** Seguridad integrada.

## Arquitectura

- **Nodos:** Son las máquinas que ejecutan las aplicaciones.
- **Pods:** Es la unidad más pequeñas de kubernetes
- **Deployments:** Gestionan el estado deseado de las aplicaciones.
- **Servicios:**  Expone las aplicaciones a la red.


## Utilización

- **DevOps:** Despliegues automatizado.
- **Aplicaciones nativas en la nube:** Arquitecturas modernas.
- **Migración a la nube:** Aplicaciones legacy en contenedores.
- **Machine Learning:** Escalado de trabajo de IA.
- **Sitios web de alto tráfico:** Escalado automático.

# Despliegue con Helm y ArgoCD

Durante el proceso de despliegue con cualquier tecnología que utilicemos, solemos intervenir mucho en el proceso, como podría ser ingresar al servidor, clonar el repositorio, montar las imágenes, etc.
Pero como informáticos, deberíamos de buscar siempre la manera de poder automatizar procesos repetitivos, es por eso que existen formas de poder automatizar un despliegue aún si aún necesitamos cambiar unas cosas en producción.

Al trabajar con kubernetes, estos siempre buscan mantener montada una configuración, lo que permite disminuir los tiempos muertos entre despliegues.
Con la configuración mostrada por el expositor, se mostró una forma de realizar un despliegue de una aplicación en un servidor de AWS desde un repositorio donde se aloja el programa; con las configuraciones hechas, utilizando Argo y Helm la página era automáticamente refrescada una vez se hayan subido nuevos cambios en el repositorio. Esto lo hacia al mantener las imágenes de la configuración anterior mientras se estaba montando automáticamente la nueva configuración, y una vez montada, se elimina la anterior y muestra la página con los cambios realizados. Esto permite realizar una actualización del contenido sin la necesidad de finalizar la conexión y desplegar manualmente los nuevos cambios en el servidor.