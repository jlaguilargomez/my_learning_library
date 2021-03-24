## Arquitectura de aplicación

Tengo que comenzar a prestar mucha más atención a la arquitectura de las aplicaciones. Es fundamental entender el flujo de comunicación existente entre los diferentes componentes de esta y cómo interfiere en el crecimiento futuro de la app.

Al principio de la introducción de frameworks para JS, estos se basaban en un desarrollo **imperativo**:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/57e68a9c-448e-4ea4-ada1-28cf4ff22b21/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/57e68a9c-448e-4ea4-ada1-28cf4ff22b21/Untitled.png)

La modificación de ciertos elementos implicaba el cambio de estado de muchos  otros, y todo de forma directa en el DOM. Esto empezaba a ser bastante complicado de gestionar en grandes aplicaciones. Ahí fue cuando el equipo de Facebook, con React, dió con la idea adecuada en el momento adecuado (**declarative**), estableciendo una serie de conceptos que luego serían "copiados" por Angular (sin JS) y Vue, entre otros muchos.

La idea fundamental, explicada de una forma "burda" es:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/77578d9c-4125-487b-99d1-0509a7e835fa/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/77578d9c-4125-487b-99d1-0509a7e835fa/Untitled.png)

## Virtual DOM

**VirtualDOM**: "dime qué cuál quieres que sea el nuevo estado de la aplicación y los cambios que quieres que ocurran, que yo me encargo de buscar la forma más óptima de llevar a cabo dichos cambios en conjunto, ¡pero tú no toques nada directamente! "

**En React, los componentes no dejan de ser funciones, que reciben un "input" y devuelven un estado concreto de dicho componente.**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/63a34e58-4347-490a-a554-b0aefd90b18c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/63a34e58-4347-490a-a554-b0aefd90b18c/Untitled.png)

## Conceptos fundamentales de la librería REACT

Los conceptos principales que hacen de React la librería que es, son los siguientes:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e90514c0-8bc7-4695-8efa-eefcbcca1e7a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e90514c0-8bc7-4695-8efa-eefcbcca1e7a/Untitled.png)

Salvo el último, coinciden con frameworks como Angular

 

El precepto de permitir que el flujo de comunicación sólo se establezca "aguas abajo", mejora el mantenimiento del código ya que hace más facil la depuración de este. Podemos conocer de donde "vienen" los errores.

**React se encarga principalmente de UI, la visualización de componentes dependiendo de su estado. Para el resto de cosas se hace necesaria la integración de librerías externas.**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/87503a97-85c8-4d7f-8b5b-53d968d64832/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/87503a97-85c8-4d7f-8b5b-53d968d64832/Untitled.png)

React sería los "robots" destacados. Para el resto de integraciones necesitaríamos recursos diferencias. Esto es lo que hace que sea una librería tan "flexible"

**Los dos "robots" señalados tienen relación con las dos librerías que "importamos" al crear un nuevo componente en React: `React` y `ReactDOM`**

Debes tener claras **tres ideas** siempre que trabajes con React:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/47e50919-49d4-4fc5-999f-a93db44f7334/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/47e50919-49d4-4fc5-999f-a93db44f7334/Untitled.png)
