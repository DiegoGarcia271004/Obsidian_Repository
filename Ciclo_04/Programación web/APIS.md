---
tags:
  - Física_II
---
Pasos para trabajar: 

> [!NOTE] Estudiar
> Revisar la documentación en expressjs
> Revisar la documentación en npm

1. Se abre la carpeta
2. Se inicia un proyecto con npm
```powershell
npm init -y
npm i express
```
3. Se crea un archivo js (preferiblemente index.js por default).

4. Se importa express en el archivo:
```js
//Se importa el framework
import express from 'express';

const app = express();
//Se declara variable de entorno
const PORT = process.env.PORT || 3000;
//Haciendo el listen
app.listen(PORT, () => {
	console.log(`Listen on http://localhost:${PORT}/`);
})
```
Ejecutar para comprobar.

5. Se debe alterar el JSON para que funcione el "start":
```json
"scripts":{
	"start": "node index.js"
}
"type": "module",
```

Se va a trabajar una API que trabaje con personas, en este caso como tenemos que trabajar.

Se crean paquetes donde se tendrán:
- Controllers
- Models
- Routes
- Services


---
Configuración de Insomnia

Manage enviroment

>Development
>Testing
>Production

Se copia y pega en todos los antreriores:
```json
{
	"url": "http://localhost:3000"
}
```


---

## Pasos para la creación de API (básica)

1. En la carpeta de Models, se crea el modelo del objeto dentro de un array de objetos:
```js
export const stands = [
    {id: 1, name: 'Star Platinum', range: 'D'}
]
```

2. En la carpeta de services, se crea el primer servicio para el modelo, en este caso se hace un getAllStands, además de retornar un objeto con las funciones:
```js
import { stands } from "../Models/stands.model";

const getAllStands = () => {
    return stands;
}

export default { getAllStands }; 
```

3. En la carpeta de Controller se hace el controlador para trabajar con la función creada en servicios:
```js
import standsServices from '../Services/stands.service.js';

const getAllStands = (req, res) => {
    res.json(standsServices.getAllStands());
};

return default { getAllStands };
```

4. En la carpeta de Routes se crea la ruta:
```js
import express from 'express';
import get from '../Controller/stands.controller.js';
const router = express.Router();

router.get('/', get.getAllStands());

export default router;
```

