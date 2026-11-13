
# Resumen de modelos

A continuación de listarán los distintos modelos dentro del sistema, estos ayudará a tener un mayor entendimiento del rol que cumple cada uno de ellos. Además de mencionar observaciones sobre los modelos y si se han planteado cambios sobre estos.

1. **User:** El usuario general del sistema, este puede tener distintos roles (usuario regular, administrador, etc).
2. **Bill:** Representan las facturas dentro de la empresa, estas *pueden ser tanto de entrada como de salida*.
3. **Business:** Es el modelo de las empresas que guarda la información proporcionada (preferiblemente por el dueño de esta).
	- Se planteó agregar una relación uno a muchos con store (debido a que un negocio puede tener múltiples tiendas).
4. **Category:** Maneja las diferentes categorías/segmentos en los que un negocio/empresa ofrece en su catálogo de productos
5. **Cost:** Representa un costo de necesidades para la operación del negocio.
6. **Country:** Es la información del país donde se encuentra tanto el negocio como las tiendas (no necesariamente tiene que ser el mismo, puede tener distintas sucursales).
7. **Image:** Modelo dedicado a guardar la información de guardado de las imágenes que se suben al sistema.
8. **lotProduct:** Permite llevar registro sobre la disponibilidad de productos que posee el negocio, permitiendo mantener la trazabilidad sobre estos.
9. **Measurement:** Guarda la medida sobre las unidades de venta de distintos productos.
10. **Product:** Es la información de (como su nombre lo indica) los productos que se encuentran en las distintas tiendas de los negocios.
11. **Provider:** Contiene la información de los proveedores.
12. **RoleTyping:** Contiene los nombres y la descripción de los roles.
13. **RoleBusiness:** Relaciona *roleTyping* con *business*.
14. **RoleStore:** Relaciona *roleTyping* con *store*.
15. **Sale:** Son las ordenes/ventas que se realizan en las tiendas.
16. **Stock:** Lleva el registro del inventario de los distintos productos de las tiendas.
17. **StockToProduct:** Relaciona *stock* con *product*.
18. **Store:** Son las distintas tiendas sucursales de un negocio, estas se encargan de vender los distintos productos.
19. **Tax:** ...

# Flujo

## Observaciones

El flujo de cuentas por cobrar (cxc) y cuentas por pagar (cxp) busca implementar una forma tanto de guardar la información de las cuentas del negocio, como consultarlas.
El modelo principal que se encuentra involucrado, es el de **Bill**, que posee la siguiente estructura:

Agregar dos modelos
1. BillPayment
	- product code
	- ammount
	- relations
	- extra data (json)
2. BillMethod
	- paymentMethod

Agregar dos campos al modelo de Bill
1. StatusPayment: Saber si ya esta pagado
2. IsPending: Saber si esta pendiente


# Ajustes de lógica de negocios

Pendiente/slope:
$$
m=\frac{y_{2}-y_{1}}{x_{2}-x_{1}}
$$

Ecuación de una recta:
$$
\begin{align*}
y-y_{0}&=m(x-x_{0})\\
y&=m(x-x_{0})+y_{0}
\end{align*}
$$
---
$$
\begin{gather*}
\text{slope:}\, m=\frac{1}{3}\qquad \text{y-intercept}=-1\qquad\text{point:}(0,-1)\\
y=\frac{1}{3}(x-0)+(-1)\\
y=\frac{1}{3}x-0-1\\
y=\frac{1}{3}x-1
\end{gather*}
$$


---


$$
\begin{gather*}

\end{gather*}
$$
1.17,10.94
5.68,6.89