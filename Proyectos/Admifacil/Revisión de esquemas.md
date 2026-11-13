
## Flujo de compra 
Se genera una compra:
1. Al comprar el inventario aumenta.
2. La caja baja (Si se paga en el momento)
3. Aumenta el crédito (Si se compra con crédito)
4. Generación de factura (información de producto, cantidad, etc)
5. Verificación de tipo de compra (OCR o manual).

Si hay sucursales, la casa matriz se encarga de el reabastecimiento de estas.
Si no tiene, el único local se convierte en casa matríz, por lo que se sigue encargando de las compras y restock.

4. Si hay bodega matríz
	1. Se carga en la bodega matríz
	2. Afecta el inventario (disminuye) de la bodega matríz
	3. Se aumenta el inventario en la sucursal


---

## Alertas de reabastecimiento

---

## Flujo de ventas

Las ventas afectan el inventario
El inventario disminuye y la caja aumenta
	- Verificar si queda debiendo
	- O se paga en el momento
Generación de facturas
Verificación de tipo de compra (OCR o manual).

>Consultar como sería el proceso de ventas "informales" (sin factura, venta en mostrador, etc)


---

## Pago de gastos generales
Afecta a la caja
Pago arriendo
Pago empleados
	Bonos
	Aguinaldo
	Salario
	Seguro Social
	AFP
Pago impuesto
Pago luz
Pago agua

---

## Flujo de reembolsos

Verificar los productos reentrantes
Verificar tipo de reembolso
	cambio de producto
	reembolso de dinero
Toma de medidas respecto al producto
	Reembolso por parte del proveedor
	Cambio por parte del proveedor
	Perdida

---

## Agregar nueva sucursal

Establecer datos iniciales (localización, inventario inicial, etc)
Establecer datos de empleados
