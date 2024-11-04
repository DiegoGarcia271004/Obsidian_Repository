---
tags:
  - ProgramaciónWeb
---
# Introducción a react
## Historia de React

React es una librería de js creado por Jordan Walke, trabajador de facebook, desarrollado para mantener la dinámica de facebook y una UI más compleja.
Conforme ha pasado el tiempo, react ha evolucionado para ser una de las librerias de front-end más populares.

---

## React vs otros frameworks

React se centra únicamente en la capa del UI, contrario a Angular o Vue que proporciona frameworks más completos.
Una fortaleza de react radica en es una arquitectura basada en componentes y el Virtual DOM, haciendo más eficiente para trabajar con contenido dinámico.

---


> [!NOTE] Investigar
> investigar como se trabaja un virtual dom en javascript vanilla
> 

## Conceptos clave en React

1. **Componentes:** Los bloques de construcción de una aplicación de react.
2. **Estado:** Manejo de datos internos de un componentes, O como su nombre lo indica, los estados que pueden tener un componente.
3. **Props (Propiedades):** Propiedades compartidas entre los componentes para compartir información.
---

## ReactDom y Virtual DOM (Completar)

**ReactDOM** Integra react al DOM del buscador


---

### Componentes

Importante mencionar que al momento de trabajar con react, es imperativo que los componentes sean reutilizables, de lo contrario, no se está trabajando con tal.
Cada uno de los componentes representan parte de la UI.



#### ¿Cómo se crea un componente?

```js
function Greeting() {
	return <h1> Hello, World!</h1>;
}

export default Greeting;
```
Los componentes funcionales son establecidos por predeterminados.
Con la introducción de los Hooks, se podrán manejar estados y métodos de ciclos de vida.

#### Componentes de clase (Completar)

``` js
import React { Components } from 'react';

class Greeting extends Component {
	render(){
	
	}
}
```

---


## Estados en React

State se usa para manejar la información interna a un componente y puede cambiar con el tiempo.

```js
import { useState } from 'react';

function COunter() {
	const [count, setCount] = useState(0);

	return (
		<div>
			<p>You clicked {count} times</p>
			<button onClick={ () => setCount(count + 1))}>
				Click me
			</button>
		</div>
	);
}
```

En el ejemplo, "useState" inicializa el estado (count) y provee una función (setCount) para actualizarlo.

---

### Props en React

Las propiedades se usa para pasar información de padre a componentes hijos.

```js
function Welcome(props) {
	return <h1>Hello, {props.name}</h1>;
}

function App() {
	return <Welcome name="Alice"/>;
}
```

En este ejemplo, el componente "Welcome" recibe la prop "name" de su componente "App".
Cabe mencionar que los props, son solo de lectura, no pueden modificar el estado de su padre.


# Qué es Vite? (Completar)

Vite es una herramienta de construcción moderna que provee una experiencia de desarrollo ...


---

## Porque Vite es rápido? (Completar)

1. ****



# React con Vite


> [!important] Tarea
> Instalar NodeJs


1. Se instala Vite usando npm
```bash
npm create vite@latest 
```

2. Se navega en el folder del proyecto y se instalan las dependencias
```bash
cd my-react-app
npm install
```

3. Se empieza el desarrollo del servidor
```bash
npm run dev
```
