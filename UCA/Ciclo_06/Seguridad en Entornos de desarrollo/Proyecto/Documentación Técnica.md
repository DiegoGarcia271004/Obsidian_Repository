# Proyecto: Seguridad en entornos de desarrollo.
---

**Integrantes:**

- Mauricio Alejandro Montes Varela.
- Diego Benjamín García Alfaro.
- Gabriel Ernesto Iraheta Guardado 00021223.

**Nombre del proyecto:** Sistema de compra de productos.

# Arquitectura
---

![[Documentación Técnica 2025-11-22 18.43.01.excalidraw|800]]

# Frontend
---
### Descripción general.

El frontend del proyecto está implementado como una Single Page Application (SPA), utilizando únicamente:

- HTML
- CSS3
- JavaScript Vanilla
- Vite
- Sin frameworks
- Navegación manejada mediante `history.pushState`
- Vistas cargadas dinámicamente desde archivos HTML parciales
- Comunicación con el backend mediante el uso de `fetch`

El objetivo de esta arquitectura es proveer una experiencia fluida sin recargas completas de página, manteniendo una estructura ligera y fácil de desplegar en un entorno controlado.

### Estructura del proyecto.

```
/Frontend
 ├── index.html
 ├── main.js
 ├── /src
 |    ├── router.js
 |    ├── style.css
 │    ├── /pages
 │    │      ├── /AdminView
 │    │      |     ├── adminView.html
 │    │      |     └── adminView.css
 │    │      ├── /Cart
 │    │      |     ├── cart.html
 │    │      |     └── cart.css
 │    │      ├── /EmployeeProducts
 │    │      |     ├── EProducts.html
 │    │      |     └── Eproducts.css
 │    │      ├── /Home
 │    │      |     ├── home.html
 │    │      |     └── home.css
 │    │      ├── /Login
 │    │      |     ├── login.html
 │    │      |     └── login.css
 │    │      ├── /NotFound
 │    │      |     ├── notFound.html
 │    │      |     └── notFound.css
 │    │      ├── /Products
 │    │      |     ├── products.html
 │    │      |     └── products.css
 │    │      └── /Register
 │    │            ├── register.html
 │    │            └── register.css
 │    ├── /Scripts
 │    │      ├── adminView.js
 │    │      ├── cart.js
 │    │      ├── empleados-productos.js
 │    │      ├── login.js
 │    │      ├── products.js
 │    │      └── register.js
 │    ├── /utils
 │    │      └── getUserRoles.js
 |    └── /assets
	         └── Logo.png
```

### Arquitectura lógica.

La arquitectura se organiza en tres capas principales:

1. **Presentación.**

	- Las vistas son archivos HTML parciales en `src/pages`
	- Son inyectadas dentro de un contenedor único definido en `index.html`
	- No contienen `<html>`, `<head>` ni `<body>`.

2. **Estilos.**

	- Los archivos CSS correspondiente a cada página está en su respectiva carpeta dentro de `src/pages`
	- Se importan dentro de `src/style.css`

3. **Lógica.**

Compuesta por:

1. Router (`router.js`)

Gestiona:

- Navegación por `history.pushState`
- Carga de vistas desde `src/pages`
- Importaciones dinámicas de módulos asociados a cada vista

2. Scripts de cada módulo

Ejemplos:

- `src/Scripts/products.js`
- `src/Scripts/login.js`

Cada uno expone un método `init()` que el router ejecuta al cargar la vista.

### Routing con Vite.

El router utiliza `fetch()` para poder cargar los HTML desde `src/pages`:

```js
const routes = {
	"/": { html: "src/pages/Home/home.html", init: null },
	"/productos": { html: "src/pages/Products/products.html",
				    init: "./Scripts/products.js" },
	"/carrito": { html: "src/pages/Cart/cart.html", init: "./Scripts/cart.js" },
	"login": { html: "src/pages/Login/login.html", init: "./Scripts/login.js" },
	"/register": { html: "src/pages/Register/register.html",
					init: "./Scripts/register.js" },
	"/empleados-productos": { html: "src/pages/EmployeeProducts/EProducts.html",                       init: "./Scripts/empleados-productos.js" },
	"/administrar-empleados": { html: "src/pages/AdminView/adminView.html", 
					init: "./Scripts/adminView.js" },
	
}
```

1. `navigateTo()`

```js
function navigateTo(url) {
  history.pushState(null, null, url);
  render();
}
```

2. Recarga dinámica de la vista.

```js
async function render() {
...

try {
    const res = await fetch(route.html);
    const html = await res.text();
    app.innerHTML = html;
    if (route.init) {
      const module = await import(route.init);
      module.init && module.init(role);
    }
  } catch (err) {
    app.innerHTML = `<p>Error cargando la vista: ${err.message}</p>`;
  }
}
```

### Manejo de sesiones.

### Seguridad.

Debido a que se está trabajando en un entorno sin frameworks ni librerías que aporten seguridad, se vio necesaria la implementación de medidas que permitirían el funcionamiento seguro de la aplicación.

1. **Sanitización de entradas.**

# Backend
---

El Backend del proyecto, fue desarrollado en el lenguaje de programación JavaScript Vanilla junto con Node.js, entorno para ejecución de JS fuera del navegador. 

Este lenguaje tiene varias aplicaciones en el desarrollo web tales como:

- Crear servidores web y APIs REST.
- Conectarse a bases de datos (relacionales y no relacionales).
- Manejar peticiones HTTP, autenticación y autorización.
- Procesar datos, archivos y lógica de negocio.
- Crear microservicios y aplicaciones escalables.

Además, JS cuenta con un ecosistema muy grande de librerías y módulos que permiten crear aplicaciones modernas.

Las librerías utilizadas en el backend del proyecto, se listan a continuación:

- **dotenv.**

Permite cargar variables de entorno desde un archivo `.env` al `process.env`. Se utiliza con el propósito de guardar datos sensibles de forma segura.

- **mongodb.**

Es la librería Driver oficial de mongoDB para Node.js. Permite conectarse a una base de datos de mongo, realizar operaciones CRUD sobre colecciones, crear colecciones, todo sin usar ORM/ODM.

- **bcrypt.**

Librería que permite encriptar contraseñas usando hashing seguro. Se utiliza para encriptar las contraseñas de los usuarios, además, permite comparar contraseñas en inicio de sesión sin necesidad de desencriptar la contraseña almacenada en la base de datos.

- **jsonwebtoken.**

Permite crear y verificar tokens JWT, los cuales se utilizan para autenticación, esto con el objetivo de proteger rutas en APIs, como es el caso del proyecto.

- **fs.**

fs es un módulo nativo de Node.js, permite leer, escribir, modificar y eliminar archivos en el sistema.

- **path.**

Otro módulo nativo de Node.js, facilita el manejo de rutas de archivos y carpetas, asegurando compatibilidad entre sistemas operativos.

### Base de datos.

La base de datos utilizada es **mongo DB.** Es del tipo de bases de datos no relacionales, la cual trabaja con colecciones como objetos JavaScript, lo cual permite acoplar de forma eficaz el manejo de la base de datos con el lenguaje utilizado, además, permite de igual forma, un mejor manejo de archivos JSON.

En cuanto a la configuración:

- Para este proyecto, se utilizó un contenedor de docker en modo desacoplado para crear un contenedor de mongo, el cual permitiera utilizar la base de datos. 

- Se expone el puerto 27017 del contenedor al puerto 27017 del host, lo que permite conectarse a la instancia de base de datos desde el exterior, en este caso, desde el backend.

- Se creó para la instancia de mongo un usuario que funge como administrador, para el cual de igual forma se le asignó una contraseña, siendo las credenciales para que dicho usuario pueda acceder a la terminal de mongo y manipular bases de datos.

- Además, se crea un volumen persistente para almacenar la base de datos de forma física fuera del contenedor, lo cual garantiza que los datos no se pierdan.

Finalmente, se utilizó la última versión disponible de la imagen oficial de mongoDB.

### Implementación de roles y autenticación.

En cuanto a la autenticación y autorización dentro del sistema, se definen cuatro roles:

- Rol de administrador.

El administrador es quién tiene poder sobre todo el sistema, con permisos de manipulación sobre usuarios, sobre empleados y sobre los productos dentro del sistema.

- Rol de empleado.

El empleado cumple el rol de administrar los productos en el sistema, tiene permisos sobre todas las operaciones de los mismos.

- Rol de usuario.

El usuario simplemente utiliza el sistema con el objetivo por el cuál fue creado, poder ver productos en venta y tener su lista de productos que desea comprar.

- Rol de usuario visitante (guest).

Es un usuario que únicamente tiene acceso a la lista completa de productos, es decir, puede observar todos los productos registrados en el sistema disponibles para comprar. Si este usuario desea poder realizar más acciones dentro del sistema, necesita registrarse.

Dentro del sistema, se tiene un middleware que permite autorizar el acceso o no a rutas de la API dependiendo del rol del usuario.

También, un middleware de autenticación. Para ello, en cada inicio de sesión de cualquiera de los tipos de usuario según su rol, se crea un token por medio de la librería *jsonwebtoken*, dicho token se envía hacia el cliente por medio de cookies, las cuales son almacenadas en el navegador, no permitiendo el acceso al token por medio de herramientas de desarrollador para el navegador.

Cada ruta que necesita ser protegida, cuando se consulta desde el cliente, la solicitud recibida en el backend debe pasar primero por ambos middlewares. El middleware de autenticación valida el token enviado desde el navegador, el cual trae codificados el rol del usuario, el id de mongo y su correo electrónico, al validarlo, se crea el objeto token en el objeto *request* y se pasa al middleware de autorización, el cual accede a dicho objeto y utiliza el rol decodificado para validar si el usuario que está intentando consultar dicha ruta, tiene permisos para accederla.

### CRUD implementados.

El CRUD implementado funciona para tres modelos:

- Usuario.
- Empleado (administrador y empleado normal).
- Producto.

Existen las 4 operaciones para cada uno de los modelos.

- **SELECT.**

Se realizan solicitudes GET para acceder a todos a los registros de un modelo. También, se utilizan solicitudes POST para acceder a un solo registro, para el caso del inicio de sesión de un usuario o empleado.

- **INSERT.**

Se realizan solicitudes POST para el registro de usuarios y empleados, así como para agregar nuevos registros de productos dentro de la base de datos.

- **UPDATE.**

Se realizan solicitudes PUT para actualizar las credenciales de un empleado, ya sea que el empleado mismo desee cambiar sus credenciales o que un administrador cambie las credenciales de un empleado. De igual forma, se puede actualizar los campos del producto, así como activar o desactivar cuentas de empleados o, activar o desactivar productos.

- **DELETE.**

Se realizan solicitudes DELETE para eliminar empleados, usuarios o registros de productos de la base de datos.

### Validaciones del servidor.

El servidor realiza varias validaciones a lo largo de su ejecución para todas las solicitudes que puede recibir.

Para realizar dichas validaciones, se construyó un middleware de validación, el cual incluye:

- Validador de correo electrónico.

- Validador de contraseñas robustas y seguras.

- Sanitizadores de parámetros en URL, de queries y de body en solicitudes HTTP.

- Validador de límite de intentos de inicio de sesión.

Los sanitizadores se ejecutan a penas la solicitud HTTP es recibida, precisamente, en el servidor creado en `server.js`, esto con el objetivo de que a los controladores les llegue entradas limpias y seguras.

Posteriormente, dependiendo de la solicitud, pueden ocurrir los validadores de límite de intentos, como para el caso de la ruta para inicio de sesión, validadores de correo electrónico y de contraseña segura para las rutas de registro de usuarios o empleados.

Si alguno de los validadores detecta falta de requerimientos o datos extraños en la solicitud, provocan que el servidor responda con un mensaje de error que es manejado mediante el control de excepciones al cliente.

De igual forma, en la capa de servicios se encuentran más validaciones, para cada una de las rutas para cada modelo, se realizan las validaciones necesarias, tales como validación de correo y contraseña, de id de mongo proveniente de parámetros en URL, así como validaciones propias que realiza mongo, como que las entradas cumplan con el modelo planteado, que los que son parámetros únicos se asegure que no se repiten.

De igual forma, cuando se detecta datos que no cumplen con las validaciones se lanzan errores personalizados que finalmente el controlador determinado responde al cliente.

### Manejo de errores.

El manejo de errores se da a través del uso de errores personalizados construidos por medio de clases, las cuales heredan de la clase nativa `Error`.

Cada clase de error, redefine el mensaje mediante un constructor y el uso de `super`. Se define igualmente el campo `name` de la clase.

Dichos errores personalizados, son instanciados cuando ocurre un error referente a su planteamiento. Por lo general, se instancian en los servicios, dado que es la capa en donde ocurren validaciones no controladas por middlewares, por lo que si hay fallo, el servidor responderá con un error que devuelve un servicio, o puede ser también, un repositorio si es la base de datos la que falla, o puede ser, un enrutador si una ruta solicitada no es encontrada.

Todos los controladores se encuentran adaptados para manejar cualquier excepción lanzada por un servicio y responder al cliente con el error que haya sido instanciado.

### Hashing de contraseñas.

La encriptación de contraseñas mantiene la integridad del sistema, dado que se asegura que ningún usuario con altos permisos pueda utilizar datos sensibles de usuarios, a los cuales puede tener acceso por sus permisos, y así vulnerar cuentas de usuarios.

Este sistema, no permite que eso pueda ocurrir dado que las contraseñas son encriptadas previo a su almacenamiento en la base de datos, por lo que ningún administrador podrá tener acceso a sus credenciales verdaderas, aún pudiendo observar su información mediante manipulación de la base de datos, dado que la encriptación no permite observar los valores reales de los campos, en este caso, de la contraseña.

Para la encriptación se utiliza la librería *bcrypt*, la cual permite igualmente que en los inicios de sesión la contraseña ingresada pueda ser comparada con la contraseña almacenada sin necesidad de desencriptarla.

### Organización del código.

### Uso de funciones y módulos.

# Informe de seguridad.
---
### Hardening aplicado al servidor.

### Configuración del firewall.

### Gestión de permisos mínimos.

### Protección contra SQL Injection.

### Protección contra XSS.

# Despliegue.
---
### Estructura del proyecto.

### Sistema operativo y configuración de máquina virtual.

### Despliegue del proyecto.

### Inicio de la aplicación.

### Configuración de base de datos.

### Puerto.

### Funcionamiento.


