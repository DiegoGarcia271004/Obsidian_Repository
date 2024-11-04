---
tags:
  - ProgramaciónWeb
---

## Generalidades

Se realizó una muestra de como se podría ver una página web relacionada a la venta de productos. No se específica que tipo de producto, por lo cual se realiza un diseño que permite la flexibilidad ante cambios sobre la estructura de este, permitiendo cambiar la paleta de colores de la página web de una forma más sencilla gracias a la utilización de variables.

## Estructura general de la página web

Se trabaja con una estructura formada por secciones, las cuales toman el tamaño total de la pantalla del dispositivo que se esté utilizando gracias a la configuración de un tamaño relativo al tamaño de la pantalla. Con el fin de darle una estructura agradable a la vista se utilizan displays tanto flex, como grid para alinear los elementos dentro de la página.

Se comienza con una sección de presentación, junto al logo de la página se encuentra una etiqueta h1 que permite dar unas cortas palabras de bienvenida, además se agrega un párrafo en el caso que se quiera dar unas palabras acerca del negocio.

Como segunda sección, se presenta el apartado "About us" que proporciona información acerca del negocio.

Después se encuentra la sección de "Our products" cuyo layout se encuentra diseñado por el display grid, permitiendo agregar más espacios de productos de ser requeridos.

Finalmente se encuentra la sección de contacto, donde se muestra un formulario en caso de querer enviar un mensaje a la organización propietaria, junto a información general de contactos.

---
## Navegación en la página

La navegación en la página web se puede realizar de dos maneras, gracias a la scroll bar del navegador, o mediante el uso del menú de navegación, el cual se accede mediante la barra de navegación.

### Barra de navegación

Está se encuentra ubicada en dos lugares, tanto en la parte superior de la página (en la sección introductoria), como en la sección final (sección de contacto), la cual gracias a la propiedad "sticky" de la sección, permite que esta se mantenga en la sección correspondiente siempre. 

A su vez se encuentran 3 iconos que permite la redirección a redes sociales propias del negocio, además de mostrar un botón que permite el despliegue del menú, el cual mediante el uso de transitions y transforms, se oculta como estado predeterminado, y al seleccionar el icono correspondiente, muestra el menú el cuál contiene botones que permiten redirigir a las distintas secciones del documento de una forma más sencilla.

---

## Funcionalidades especiales

### Diseño de "hover" sobre los íconos de la barra de navegación

Se utilizan transitions junto con un pseudoelemento que permite que al momento de colocar el cursor sobre los íconos, estos suavemente, cambien de color.

### Diseño de "hover" sobre botones del menú de navegación

De igual manera que con lo íconos de la barra de navegación, estos se ayudan de transitions y pseudoelementos, con el cambio que la forma en la que estos se transforman es de una manera diferente, sin embargo el funcionamiento es, en esencia, similar. 

---

## Configuración responsive 

Se trabaja con dos diseños, tanto el de celulares como el de computadoras.
Gracias a la configuración establecida en computadoras, está permite que a su vez, funcione bien en vista de tableta.

En modelos de teléfono, se trabaja con un diseño más compacto con el fin de permitir el ajuste con la pantalla de los celulares más pequeños.

Mientras que en la configuración de tableta y computadora, se busca un diseño más espacioso, con menor sobrecarga de espacio en cada sección.