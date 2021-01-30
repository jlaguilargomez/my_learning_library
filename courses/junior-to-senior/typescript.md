# Typescript
---

[***Notion***](https://www.notion.so/jlaguilargomezdevelop/Typescript-course-1b53d454f6164bf9829388f043379f65)

---
## Intro y configuración

Typescript convierte JavaScript, que es un lenguaje de tipado dinámico, en uno de tipado estático.

Para acceder a la configuración de Typescript, una vz que lo hemos instalado en local, ejecutamos en la consola:

```jsx
tsc
```

Para no tener que estar lanzando continuamente el comando `tsc typescript.ts`, podemos configurar typescript para que se transpile de forma automática cuando estamos configurando el proyecto.

Para eso tenemos la opción

```jsx
tsc --init
```

Nos crea un archivo `tsconfig.json` que nos trae las opciones de configuración del proyecto:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a1a4d68e-1d38-4ca8-a56d-b756f2be2ac4/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a1a4d68e-1d38-4ca8-a56d-b756f2be2ac4/Untitled.png)

Ahora podemos ejecutar la compilación mediante `tsc typescript.ts --watch` que se realizará con la configuración que hayamos creado el el archivo previo.

[](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1d5b6545-e74d-4e76-82c4-74c5020808a6/TypeScript.ts)

## Types

### Tuple

Variables pueden tener varios tipados en el mismo elemento (...)

```jsx
let basket: [string, number];
basket = ['basketball', 12];
```

### Enum

Estructura de datos que nos pemite gestionar valores simples

```jsx
enum Size {
	Small = 1,
	Medium = 2,
	High = 3,
}
```

### Interface

Permite crear objetos con propiedades personalizadas

```jsx
interface RobotArmy {
	count: number;
	type: string;
	magin: string;
}

let fightRobotArmy = (robots: RobotArmy) => {
	console.log('fight');
}

```

*[🧙🏿‍♂️ a veces podemos encontrar que en lugar de `interface` se usa  `type` ]*

[Interface vs Type alias in TypeScript 2.7](https://medium.com/@martin_hotell/interface-vs-type-alias-in-typescript-2-7-2a8f1777af4c)

### Type assertions

Nos permite rectificar el tipo que le pasamos a un determinado valor, forzándolo (...)

```jsx
interface RobotArmy {
	count: number;
	type: string;
	magin: string;
}

let robot = {} as RobotArmy;
robot.count; // vacío, pero no nos devolverá un error
```

** Debes usar esto con cabeza y cuidado, ya que no es recomendable

[Type Assertion](https://basarat.gitbook.io/typescript/type-system/type-assertion)

## Definitely Typed

En aquellos proyectos que usemos librerías de terceros o frameworks que no "corran" de base Typescript, como sí sucede con Angular, tenemos que "hacer consciente" a **Typescript** de los tipos que vamos a utilizar para esta aplicación.

Es por eso por lo que se creó esta herramienta, que nos permite, por ejemplo, integrar los tipos de JQuery con Typescript:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4d139202-19e6-4f24-92c9-6ff6a75f345b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4d139202-19e6-4f24-92c9-6ff6a75f345b/Untitled.png)

Pongamos el ejemplo de que hemos recurrido a los "types" de React:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aa148f5d-04e7-4ac1-9980-9394d3404dc8/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aa148f5d-04e7-4ac1-9980-9394d3404dc8/Untitled.png)

*[🧙🏿‍♂️ recuerda que lo usaste para el tipado de la librería de Google en el proyecto de ISOS]*

## Typescript + React

Con las nuevas versiones de React, podemos iniciar un proyecto de React con Typescript:

```jsx
npx create-react-app my app --typescript
```

En cambio, si queremos añadir REACT a un proyecto existente, deberemos ejecutar los siguientes comandos:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/30dab448-20aa-4754-8faa-12ef943a0208/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/30dab448-20aa-4754-8faa-12ef943a0208/Untitled.png)

En ambos casos se habrá creado  el fichero `tsconfig.json` que nos habilita el uso de Typescript:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/be6f015d-ae5a-4cb5-b544-35936f6e35fb/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/be6f015d-ae5a-4cb5-b544-35936f6e35fb/Untitled.png)

## Typescript in robofriends

[aneagoie/robofriends-typescript-completed](https://github.com/aneagoie/robofriends-typescript-completed)
