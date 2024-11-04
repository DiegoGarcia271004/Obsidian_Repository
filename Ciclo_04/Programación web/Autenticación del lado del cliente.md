---
tags:
  - ProgramaciónWeb
---
Se debe realizar un wrapper de un contexto en app, para que todo el código dentro de app pueda acceder a este:
```js
function App() {
	return (
		<AuthContextProvider>
			<Router>
				<Routes>
					<Route path="/" element={<HomePage/>}/>
					<Route path="/login" element={</>}/>
					<Route path="/register" element={<Home page/>}/>
				</Routes>
			</Router>
		</AuthContextProvider>
	)
}
```

Primeramente se debe crear el contexto, es decir un archivo (tentativamente) llamado "AuthContext.jsx".

```js
import { createContext } from 'react';

export const AuthContext = createContext();
```

En AuthContextProvider crea el contexto:
```js
const AuthContextProvider = ({children}) => {
	const [user, setUser] = useState(null);
	const [token, setToken] = useState(localStorage.getItem('token') || '');

	useEffect(() => {
		if(token) {
			localStorage.setItem('token', token);
		}else {
			localStorage.removeItem('token');	
		}
	}, [token]);
	//Se verifica si el token cambia, si cambia, entonces lo verifica

	return (
		<AuthContext.Provider value=({user, token, login, register})/>;
		//Se exporta la configuración
	)
}
```


En HomePage se importan los contextos, el "AuthContext", Link de 'react-dom'