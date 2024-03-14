---
tags:
  - "#Programacion"
---
#### ¿Qué es un objeto?

En resumidas cuentas aquello que posea características y pueda realizar acciones (o diversas cosas) es considerado un objeto.

### Paradigma estructurado

En la programación estructurada, ésta se encuentra adentro de funciones, lo cual para el resto del código resulta desconocido, siendo así que estas ya mencionadas funciones reciben datos de entrada, y se entrega una salida, sin conocimiento del resto del programa.

Algunas de las características que posee el paradigma estructurado son las siguientes:
1. Los datos están centralizados.
2. Hay una función/procedimiento para cada tarea.
3. Las funciones acceden en datos centrales.

### Paradigma Orientado a Objetos

En este tipo de paradigma se mantiene todo en oculto para cualquier agente externo, siendo así, una forma más segura de trabajar entre varios participantes.

Algunas características del paradigma orientado a objetos:
1. **Toda** la comunicación es a través de las acciones/operaciones.
2. Estas acciones reciben el nombre de **métodos**.

#### Ahora sí, ¿Qué es un objeto?

Es una entidad que encapsula tanto **datos** como **comportamientos**.
Un objeto es una forma de representar cosas o conceptos dentro del contexto de un programa, el cuál posee características (atributos), y acciones (métodos).

Los objetos son los cimientos de un programa orientado a objetos. Un programa que está basado en este paradigma básicamente es una colección de objetos.

Dentro del mundo de los objetos (en programación), posee grandes ventajas en cuanto a privacidad se refiere con grandes características las cuales se mencionaran a continuación:

1. El hecho de que los datos estén encerrados, y protegidos, dentro de un objeto.
2. La consecuencia de brindar mayor seguridad a dicha información.
3. La acción de solo poder conocer esos datos a través de los métodos se le llama **encapsulamiento**.


## Clases y objetos

Ya que durante el proceso de programación los objetos se utilizan en varios momentos, estos tienden a repetir mucho código, en el caso de que existan varios objetos con características o comportamientos, es recomendable que existan unas **plantillas**.
La **clases** son las plantillas de nuestros objetos, mientras que los objetos serán las **instancias** de clases.

## Métodos Setters y Getters

En programación orientada a objetos, los objetos son como capsulas, los cuales mantienen seguras ya sean atributos o métodos del objeto, debido a esto, es que necesitamos una forma de, que en caso de necesitarlo, extraer o alterar los datos de un objeto manteniendo la privacidad del objeto, sin comprometer la información almacenada en el.

Los setters son los métodos que permiten definir o reescribir un atributo que posee el objeto. Los cuales por la convención UML (Unified Modelliny Language), se escribe la palabra **set** concatenado al nombre del atributo que se esta haciendo referencia. Es importante mencionar que debido a que estos simplemente alteran el dato de un atributo, estos no devuelven ningún dato, siendo así que el dato de estos métodos serán **void**.

Los getters son los métodos que permite **obtener** la información resguardada en un objeto, su forma de escribirse es escribir la palabra **get** concatenado al nombre del atributo que se estará haciendo referencia, debido a que estamos pidiendo un dato, éstos métodos si tendrán un tipo de dato, el cuál dependerá del tipo de dato del atributo que se busca pedir.

