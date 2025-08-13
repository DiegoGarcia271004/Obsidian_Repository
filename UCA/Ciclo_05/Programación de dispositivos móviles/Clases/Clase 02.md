En kotlin se programa de una manera similar a java, con algunos cambios. 
Lo principal es la función ``main``:

``` kotlin
fun main() {
	var name: String? = null //Asignación de variables
	//El ? después de String es una propiedad de kotlin que permite una
	println("hola ${name.length?}") //Impresión de datos en consola
}
```

