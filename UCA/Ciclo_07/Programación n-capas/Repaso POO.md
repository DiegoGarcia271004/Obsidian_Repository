## Pilares de la programación orientada a objetos

1. **Encapsulación**
2. **Abstracción**
3. **Herencia**
4. **Polimorfismo**

## Principios SOLID

1. **S**ingle responsability principle: Una clase debe tener únicamente una responsabilidad. Si hace más de una cosa, está mal.
2. **O**pen-closed principle: El código actual no debe de modificarse para poder agregar una funcionalidad nueva, solo debe extenderse. (Si se quiere agregar alguna funcionalidad, se debe crear una nueva clase, no alterar la original)
3. **L**iskov's substitution principle: Las subclases deben poder reemplazar a las clases padre sin problema. (Si una subclase necesita desabilitar algún método de la clase padre, algo está mal hecho)
4. **I**nterface segregation principle: Ninguna clase debe depender de métodos que no utiliza. (Divide las interfaces según los clientes que las usan, no según lo que es conveniente agrupar)
5. **D**ependency inversion principle: Depender de abstracciones, no de implementaciones concretas. (La lógica de negocio no debe saber cómo se guarda un dato, solo que es posible guardarlo)

