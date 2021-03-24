Vamos a crear la página de "shopping", que tendrá el siguiente aspecto:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3e89fc38-84fe-4870-83f2-943a3865ff6a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3e89fc38-84fe-4870-83f2-943a3865ff6a/Untitled.png)

Una vez creados los componentes de la galería, creamos el HEADER.

Este se incrustará en la aplicación con una estructura similar al `app.component.ts` de Angular:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68963281-a858-4c51-ab81-2d4669692366/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68963281-a858-4c51-ab81-2d4669692366/Untitled.png)

Imaginemos que el `switch` es el `router-outlet`

## Importing SVG in React

*In the previous lesson, you may have seen the strange syntax: **`import** { ReactComponent **as** Logo }`*

*This is a new special syntax when importing SVG in React. The `ReactComponent` import name is special and tells Create React App that you want a React component that renders an SVG, rather than its filename. You can read more about it here, but keep in mind that this is a React library special syntax:*

[*https://facebook.github.io/create-react-app/docs/adding-images-fonts-and-files*](https://facebook.github.io/create-react-app/docs/adding-images-fonts-and-files)

## Forms in React

Uno de los componentes más comunes en cualquier página son los formularios. En este caso vamos a crear formularios de registro y de "loggin" en la aplicación.

Debemos crear la lógica necesaria para poder dar de alta a nuevos usuarios en el servidor, así como permitir que los usuarios ya registrados puedan acceder a la página.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6c2a277b-0fea-4d75-9366-f84863230ab5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6c2a277b-0fea-4d75-9366-f84863230ab5/Untitled.png)

Utilizaremos FIREBASE para gestionar las autorizaciones de usuarios.

Como es lógico, trataremos de generar tantos componentes reutilizables como se posible en nuestros formularios.

El caso mas obvio es el de los inputs `FormInput` y el de los botones `CustomButton` en los que, como vemos en la imagen adjunta, podremos configurar a través de sus PROPS y decidir los eventos que se lanzarán en cada caso.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8a310db1-82e4-4752-b720-9b177423032d/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8a310db1-82e4-4752-b720-9b177423032d/Untitled.png)

## Estado del formulario

Otra CUESTIÓN muy importante que debes tener en cuenta... ¿dónde albergaremos el estado de los formularios?

Imaginemos la siguiente composición:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/307fb400-2066-4629-b131-de5f65516674/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/307fb400-2066-4629-b131-de5f65516674/Untitled.png)

En la que la página `/signIn` es el componente 7 y cada uno de los formularios viven en 8 y 3...

¿Dónde albergamos el estado de estos, en 7 o quizá en el componente más "arriba" de la aplicación, en este caso 0?

*[🧙🏿‍♂️ si estuvieramos trabajando con REDUX lo tendríamos bastante clarinete, ¿no?]*

**¡SORPRESA!, cada uno de los formularios tendrá su propio estado. ¿Por qué?, porque si lo trasladamos a 7 o 0, cada vez que cambiemos 8, 3 renderizará todo el arbol dependiente del componente del estado, lo que implica cálculos extra que no nos interesan. Además... el estado de 8 no influye en 3 y viceversa.**

Siempre, siempre, ten en cuenta estos 3 epígrafes:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bfced32d-4537-4523-87bf-f8f4b3e763fa/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bfced32d-4537-4523-87bf-f8f4b3e763fa/Untitled.png)

## Cambiar valores del formulario dinámicamente y de forma reutilizable

Ojo al método que utiliza para hacer esto de una forma cómoda, usando el `name` del input como declaración.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7fe2f2d3-ae98-441d-be93-96d3e8cced15/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7fe2f2d3-ae98-441d-be93-96d3e8cced15/Untitled.png)

## Configurando FormInputComponent y estilando con variables y mixin

Creamos una configuración dinámica de cada campo INPUT para poder reutilizarlos en los diferentes formularios:

```jsx
const FormInput = ({ handleChange, label, ...otherProps }) => (
  <div className='group'>
    <input className='form-input' type='text' onChange={handleChange} {...otherProps} />
    {label ? <label className={`${otherProps.value.length ? 'shrink' : ''} form-input-label`}>{label}</label> : null}
  </div>
);
```

En el estilo del componente, hemos utilizado variables de SASS, así como `@mixin`:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/26afcf80-df75-445b-96a2-2b79df2c4031/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/26afcf80-df75-445b-96a2-2b79df2c4031/Untitled.png)

### Configurando CustomButtomComponent con "otherProps" y props.children

Crearemos un componente reutilizable nuevamente ("presentational component"), para que sea lo suficientemente flexible para poder ser utilizado en múltiples sitios

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a7dd065b-4a0f-4093-93c1-dd54ccc6446f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a7dd065b-4a0f-4093-93c1-dd54ccc6446f/Untitled.png)

Vemos un tema importante ...

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f8917c5c-c706-4d2f-ab07-a8d504931347/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f8917c5c-c706-4d2f-ab07-a8d504931347/Untitled.png)

Para configurar el botón, le añadimos como atributo `otherProps`, para que estos, se adhieran al componente `<button>` tal cuál, es decir, como `type="submit" value="Submit"`

Diferente es el caso de `props.children`, este es un PROP particular que se basa en recoger como PROP lo que la etiqueta del componente contenga entre su contenido. Se explica mejor
