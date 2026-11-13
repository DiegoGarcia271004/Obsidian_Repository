- [Compras](##Compras)
	- [[#Compras#Contexto y propuestas de cambios|Contexto y propuestas de cambios]]
		- [[#Contexto y propuestas de cambios#Identificación de casa matriz|Identificación de casa matriz]]
		- [[#Contexto y propuestas de cambios#Entidad Purchase|Entidad Purchase]]
		- [[#Contexto y propuestas de cambios#Separación entre Bill de venta y Bill de compra|Separación entre Bill de venta y Bill de compra]]
	- [[#Compras#Flujo de la compra|Flujo de la compra]]
	- [[#Compras#Propuesta de request|Propuesta de request]]
- [[#Ventas|Ventas]]
	- [[#Ventas#Contexto y propuesta de cambios|Contexto y propuesta de cambios]]
		- [[#Contexto y propuesta de cambios#Entidad de la caja de la tienda|Entidad de la caja de la tienda]]
		- [[#Contexto y propuesta de cambios#Movimiento de caja|Movimiento de caja]]
	- [[#Ventas#Flujo de venta|Flujo de venta]]
	- [[#Ventas#Propuesta de request|Propuesta de request]]

## Compras

### Contexto y propuestas de cambios

Para las compras se plantea un flujo donde solamente la tienda que es la casa matriz del negocio sea capaz de realizarlas, debido a que el resto de las sucursales contarán con el reabastecimiento por parte de la casa matriz. 

#### Identificación de casa matriz
Con base a lo anterior, se propone un nuevo campo dentro de `store`, que sea un booleano que verifique si la tienda que realizará la compra es una casa matriz del negocio.

#### Entidad Purchase
A su vez, se propone de igual manera un nuevo modelo que permita llevar el registro de la compra y llevar datos clave dentro de esta:
```
Purchase {
	business: relation -> business
	store: relation -> store
	provider: relation -> provider
	items: component(reusable) //lista de productos comprada
	//para cada item
	items.product: relation -> product
	items.purchasePrice: decimal
	items.quantity: integer
	items.salePrice: decimal
	paymentMethod: enum //podrían ser CASH o CREDIT
	creditPending: decimal //0 si es pago al contado
	creditDueDate: date
	status: enum //podrían ser DRAFT, CONFIRMED, PAID
	notes: text
	purchasedAt: date
}
```

#### Separación entre Bill de venta y Bill de compra
Finalmente, se propone ya sea extender `Bill` para que incluya un campo de enums que diferencie entre una bill de venta o de compra; o en su defecto, generar una nueva entidad dedicada a `PurchaseBill`.

---
### Flujo de la compra

El flujo de compras contaría con tres fases: la validación de datos, el registro de la compra junto con la actualización de inventario y la generación de la factura.
Por lo que la propuesta del flujo queda de la siguiente manera:

![[Flujo de compra|center|500]]

---

### Propuesta de request

```JSON
{
	"data": {
		"store": store_id,
		"provider": provider_id,
		"paymentMethod": "credit", //o cash si es al contado
		"creditDueDate": "27-10-2025",
		"purchasedAt": "2025-05-26T10:00:00Z",
		"notes": "Pedido de insumos",
		"items": [
			{
				"product": id_producto1,
				"quantity": 35,
				"purchasePrice": 2.50,
				"salePrice": 4.00 
			},
			{
				"product": id_producto2,
				"quantity": 500,
				"purchasePrice": 1.50,
				"salePrice": 6.00 
			},
			{
				"product": id_producto3,
				"quantity": 90,
				"purchasePrice": 3.00,
				"salePrice": 5.00 
			}
		],
		"taxes":[id_tax1, id_tax2],
		"generateBill": true 
	}
}
```


## Ventas

### Contexto y propuesta de cambios

Para las ventas, se contempla que cada sucursal (incluyendo la misma casa matriz) gestionará las ventas con el stock que la tienda tiene. Al realizar una venta, el stock de la tienda disminuye y se registra el ingreso a la caja de la tienda.

#### Entidad de la caja de la tienda
Debido a que se debe de mantener el saldo actual de la tienda, se puede plantear una entidad que represente a la caja de la sucursal:
```
CashRegister {
	store: relation -> store
	balance: decimal
	openedAt: dateTime //apertura de turno
	closedAt: dateTime //cierre de turno
	status: enum //OPEN o CLOSED
}
```

#### Movimiento de caja
Para poder mantener la trazabilidad de las compras se propone la entidad `CashMovement`:
```
CashMovement {
	cashRegister: relation -> CashRegister
	type: enum //INCOME o EXPENSE dependiendo del movimiento
	ammoun: decimal
	origin: enum //SALE, COST, MANUAL, TRANSFER o lo que haya generado el movimiento
	sale: relation -> Sale //en el caso que venga de una venta
	cost: relation -> Cost //en el caso que venga de un costo operativo
	description: text
	movedAt: DateTime //fecha y hora del movimiento
}
```

---

### Flujo de venta

El flujo contaría con 3 fases, el registro, la verificación de stock (prescindible si se trabaja con alertas de stock y se asume que hay suficiente stock disponible) y gestión de inventario, caja y facturación.

![[Flujo de venta|center|500]]

---

### Propuesta de request

```JSON
{
	"data": {
		"store": store_id,
		"soldAt": "2025-05-26T10:00:00Z",
		"items": [
			{"product": id_product1, "quantity": 5, "unitPrice": 5.00},
			{"product": id_product2, "quantity": 3, "unitPrice": 3.99}
		],
		"taxes": [id_tax1, id_tax2],
		"generateBill": true,
		"notes": "Venta mostrador"
	}
}
```


## Pago de gastos operativos



