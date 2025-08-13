
> [!NOTE] Tarea
> Se debe revisar la forma en la que funcionan los permisos para hacerlos mas granulares con granulares se refiere a que cada acción tenga su permiso por ejemplo actualmente esta que para eliminar y editar se usa el mismo permiso, la idea es que para eliminar y para editar sea un permiso diferente y así con cada acción a realizarse


**Objetivo:** Granular Permissions.

# Archivos principales

`Permissions.entity.js`

Es el archivo donde, como su nombre lo dice se establece el esquema de mongo sobre los permisos, incluye lo siguientes atributos:
- `value`:
	- `_id`: No hay mucho que explicar
	- `value`: 