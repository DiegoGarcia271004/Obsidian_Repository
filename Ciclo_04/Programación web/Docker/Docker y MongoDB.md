Al trabajar con mongo, al ser una base de datos no relacional, los datos se guardan en colecciones que tienen el formato BJSON.

### Algunos comandos

Lo que sería el equivalente a un SELECT de una base de datos relacional, se da con el find:
```js
db.find({});
```

En caso de que se quiera hacer un WHERE, entonces se debe especificar el dato que se necesita:
```js
fb.find({name:"Diego"})
```

# Docker desde 0

Crear un container con imagen en mongo:
```powershell
docker run --name some-mongo -d mongo
```

Eliminar un container:
```powershell
docker container rm <container-name>
```

> [!todo] Instalar
> MongoDB compass

Detener un container:
```powershell
docker container stop <container-name>
```

:IbEye:
