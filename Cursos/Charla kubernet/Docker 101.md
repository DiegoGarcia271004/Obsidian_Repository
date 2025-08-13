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


