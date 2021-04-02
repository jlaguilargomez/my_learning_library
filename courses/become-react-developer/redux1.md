---

## Section overview

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ad09324f-191f-411f-a5f1-6e83309cd2a8/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ad09324f-191f-411f-a5f1-6e83309cd2a8/Untitled.png)

Tengamos en cuenta algo que hemos mencionado antes, **REACT**, es una librería de UI, por lo que según la aplicación va creciendo, manejar el estado se vuelve cada vez más complejo.

Usaremos **REDUX** para manejar los estados de una forma global y más sencilla (ya que es una librería creada explícitamente para este fin).

Nos vamos a centrar principalmente en este concepto:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fbab052e-0f52-4c15-b3ec-785cd2107b96/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fbab052e-0f52-4c15-b3ec-785cd2107b96/Untitled.png)

## Redux introduction

Partimos de la idea base, una aplicación de REACT se compone de una serie de componentes que renderizan un contenido al usuario. Estos componentes pueden tener o no estado propio.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/07a5c30d-3ac6-4c3b-a25a-8d6f1ea35697/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/07a5c30d-3ac6-4c3b-a25a-8d6f1ea35697/Untitled.png)

Cuando la aplicación empieza a tener una cierta entidad, llegamos a estructuras como la siguiente:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9ead2072-3260-4d24-8bae-51d8be1166ef/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9ead2072-3260-4d24-8bae-51d8be1166ef/Untitled.png)

Los círculos rojos son los componentes con estado, los AZULES cambian el estado de un padre.

Manejar todo esto puede ser una locura, por lo que **REDUX** llega para hacer que los componentes sean todos funcionales (reciben **PROPS**) y su estado se almacene en una "**STORE**" (un objeto masivo que maneja todos los estados de la aplicación). 

El esquema anterior se convierte en:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/773ea872-8150-41dc-8969-c622bdc5ff2f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/773ea872-8150-41dc-8969-c622bdc5ff2f/Untitled.png)

**REDUX es una librería no exclusiva de REACT, pero su integración con esta es óptima. Se inspira en el diseño de las bases de datos.**

## Redux concepts

¿Por qué utilizar REDUX?

- Óptimo para gestionar estados cada vez más complejos
- Útil para compartir datos entre "componentes"
- Gestión del estado basada en 3 principios fundamentales:
    1. *Single source of truth*
    2. *State is read only*
    3. *Changes using pure functions*

### Redux flow

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/28a10ba5-cdd4-4f14-91fb-b61e98729003/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/28a10ba5-cdd4-4f14-91fb-b61e98729003/Untitled.png)

Redux utiliza un patrón de arquitectura denominado "FLUX PATTERN" 

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/13785da3-049e-4c72-a3b9-ab15c2b98e7b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/13785da3-049e-4c72-a3b9-ab15c2b98e7b/Untitled.png)

Unidirectional data flow

**Arquitectura en software es crear un patrón para resolver problemas con sentido lógico de forma organizada**

Aunque no es del todo excluyente (veremos casos concretos), podemos decir que:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1555f72c-35b9-4d99-a8be-d23943780fa5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1555f72c-35b9-4d99-a8be-d23943780fa5/Untitled.png)

## Redux in our application

Uno de los principales problemas que hicieron necesario la gestión del estado de los componentes de una forma "diferente" es lo que se conoce como *prop-drilling*, esto es, tener que pasar un PROP a través de varios componentes hasta llegar al que realmente lo va a utilizar:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f0c9a163-b84c-4421-aefb-0cc2d0120278/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f0c9a163-b84c-4421-aefb-0cc2d0120278/Untitled.png)

Y un problema más... ¿qué ocurre si cada uno de los `Cart Component`tiene un `currentUser` con un estado diferente? 😲

### Redux diagram

Para prevenir esto, implementamos **REDUX** en nuestra aplicación (recuerda su arquitectura, **FLUX**), que sigue el siguiente esquema:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/48ec0f37-c930-4531-ae07-1a461dfbcbb5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/48ec0f37-c930-4531-ae07-1a461dfbcbb5/Untitled.png)

**El diagrama superior es fundamental, ya que explica con bastante exactitud cómo funciona REDUX**

### ¿What are "REDUCERS"?

Los **REDUCERS** son objetos que tienen propiedades relacionadas con el ámbito sobre el que actúan.

Según el esquema, en el `Home Reducer` estará todo lo relacionado con la **HOME** (...)

Todo en su conjunto componen el `Root Reducer`

El esquema sería el siguiente:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/93a529c8-10da-4890-bace-c9f4cd3f6070/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/93a529c8-10da-4890-bace-c9f4cd3f6070/Untitled.png)

### ¿What about "ACTIONS"?

Al lanzar una "acción" de actualización del state, esta cuenta con dos propiedades: `type` y `payload`, con la primera determinamos el tipo de **REDUCER** sobre el que actuar, y con la segunda llevamos a cabo el cambio.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dd524fe8-b508-482a-a4c5-7543ada20b9b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dd524fe8-b508-482a-a4c5-7543ada20b9b/Untitled.png)

***Notice that redux doing similar things to this.setState()***

### Reducer code example

```jsx
const userReducer = (currentState, action) => {
	switch (action.type) {
		case 'SET_CURRENT_USER':
			return {
				...currentState,
				currentUser:action.payload
			}
		default:
			return currentState
	}
}; // => {currentUser: {...}}
```

**Devolvemos un nuevo OBJETO siempre que ejecutamos este REDUCER para que se renderice nuevamente el componente objeto con los nuevos cambios (los PROPS del componente han variado y el "virtual DOM" es consciente de ello). Si únicamente modificaramos las propiedades internas del mismo, este no sería consciente del cambio llevado a cabo y no pasaría nada**

Esto sería un ejemplo de cómo NO funcionaría (modificando la propiedad seleccionada):

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8904a2bc-1f88-4d35-9565-5adb7e403b82/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8904a2bc-1f88-4d35-9565-5adb7e403b82/Untitled.png)

Ojo, si se da el caso en el que se ejecuta el `default`, como devolvemos el mismo objeto, el componente ni se entera de la ejecución del `reducer`, ¡no ha pasado nah!

## Setting up redux

Vamos ahora a configurar nuestro proyecto "*ecommerce-project"* con **REDUX**.

Volvemos al esquema estructural:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/54d23d14-c639-4b25-945f-dc3fcadcb36d/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/54d23d14-c639-4b25-945f-dc3fcadcb36d/Untitled.png)

Podemos insertar "middlewares" que "muten" las acciones antes de pasarlas por el **REDUCER**. Un ejemplo de una de las que vamos a instalar es la que se encarga de mostar en consola (log) todo lo que vamos ejecutando.

### Instalando librerías

Instalamos las siguientes librerías:

```powershell
npm install redux redux-logger react-redux
```

### Configurando REDUX

La configuración principal la llevaremos a cabo dentro del componente `index.js`

Importamos el componente `Provider` de `react-redux`, y "wrapeamos" todo el contenido que se va a renderizar en el DOM, dentro de esta etiqueta.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/23e54fc5-5928-4bed-9ac4-a4e8248109d1/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/23e54fc5-5928-4bed-9ac4-a4e8248109d1/Untitled.png)

### Creando el primer reducer

La estructura de archivos y carpetas que usamos para crear los reducer es la siguiente:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d18a8a5e-87f8-4097-8960-0f714bb9eb68/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d18a8a5e-87f8-4097-8960-0f714bb9eb68/Untitled.png)

Una carpeta `/redux` que contiene un fichero `root-reducer.js`, que se encarga de combinar todos los reducer individuales de la aplicación, que estarán almacenados, cada uno de ellos, en su propia carpeta (como vemos con user).

Cada reducer tomará una estructura similar a la siguiente, ya vista anteriormente en la definición de los **REDUCER**:

```jsx
const INITIAL_STATE = {
  currentUser: null,
} // Nos sirve para pasarle este parámetro como "default", en caso de que no llegue el estado inicial

const userReducer = (state= INITIAL_STATE, action) => {
  switch (action.type) {
    case 'SET_CURRENT_USER':
      return {
        ...state,
        currentUser:action.payload
      }  
    default:
      return state;
  }
}

export default userReducer;
```

Todos estos serán combinados en el fichero `root-reducer.js`, mediante la función `combineReducers` de la librería `'redux'`:

```jsx
import { combineReducers } from 'redux';
import userReducer from './user/user.reducer';

export default combineReducers({
  user:userReducer
})
```

### Creando la "store"

El siguiente paso es almacenar los estados en la store, que básicamente es el sitio del que está pendiente el DOM virtual para inducir cambios a la aplicación cuando este cambia.

Creamos la estructura básica de la store, teniendo en cuenta la posible aplicación de "middlewares" (como el logger) y haciéndola escalable (para poder añadir más sin mucha dificultad.

**Escalabilidad, un concepto clave que ya conoces pero debes tener mucho más en cuenta: haz que las aplicaciones sean fácilmente "mejorables" e "incrementables"**

Quedando el contenido del archivo `store.js` de la siguiente forma:

```jsx
import { createStore, applyMiddleware } from 'redux';
import logger from 'redux-logger';

import rootReducer from './root-reducer';

const middlewares = [logger];

const store = createStore(rootReducer, applyMiddleware(...middlewares));

export default store;
```

Es el momento de aplicarlo a la etiqueta `<Provider>` en `index.js`

```html
import store from './redux/store';

ReactDOM.render(
  <Provider store={store}>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </Provider>,
  document.getElementById('root')
);
```

### Creando "actions"

Nos queda crear la acción que lleve a cabo el cambio de usuario:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b1dde8d6-49ec-44c4-8867-54a2447717d3/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b1dde8d6-49ec-44c4-8867-54a2447717d3/Untitled.png)

Se nos propone seguir un esquema por carpetas con `/reducer` y `/actions` en cada una de las "áreas de actuación" que llevemos a cabo (en este caso /user) 

Las actions siempre son funciones que devuelven un objeto (con **type** y **payload**):

```jsx
export const setCurrentUser = user => ({
  type: 'SET_CURRENT_USER',
  payload: user
})
```

En teoría con esto hemos terminado de configurar **REDUX** para poder empezar a utilizarlo (mediante los "**dispacher**" que ejecutan las acciones). Conviene leer la **documentación oficial de REDUX** para más info o ver algún video formativo sobre la materia. Dejo la info:

[Read Me](https://es.redux.js.org/)

[Conoce Redux en 19 minutos](https://www.youtube.com/watch?v=Ko7avuco-Gw)

Dejo alguna de las diapositivas del video de Nicolás (muy top):

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bc77ec0a-7c28-4329-9203-c9d8aa2d0c55/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bc77ec0a-7c28-4329-9203-c9d8aa2d0c55/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e9efb947-c8c3-4000-8c67-c218aef91a88/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e9efb947-c8c3-4000-8c67-c218aef91a88/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8f31aaba-0091-4e33-9bc6-b9f7eef5a940/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8f31aaba-0091-4e33-9bc6-b9f7eef5a940/Untitled.png)

## connect() and mapStateToProps

Ya tenemos el userReducer configuado, con la acción para "setear" el usuario, así que vamos a lanzarlo desde el HeaderComponent

A este, le hemos suprimido el prop que tenía y, en su lugar, le hemos pasado el reducer internamente:

```jsx
const mapStateToProps = (state) => ({
  currentUser: state.user.currentUser
});

export default connect(mapStateToProps)(Header);
```

Hemos importado previamente la "higher order function" connect():

```jsx
import {connect} from 'react-redux'; 
```

Le pasamos como argumento primero (admite 2), la función que hemos creado, `mapStateToProps(state)` que se encarga de conectar con rootReducer, y traer los datos de `currentUser`:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ffb4baba-70e8-4ced-9694-22fa464da706/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ffb4baba-70e8-4ced-9694-22fa464da706/Untitled.png)

**Haremos esto, siempre que en un componente necesitemos traer PROPERTIES de nuestro REDUCER**

## mapDispatchToProps

La función `connect()` acepta 2 argumentos, el primero es para setear el estado actual, el segundo para lanzar los cambios (dispatch).

Trabajaremos en el componente `App.js` , que no requiere ser consciente de ningún estado (ya que se le parasará a los componentes hijos. 

En este caso, pasaremos dos argumentos a la función `connect(null, mapDispatchToProps)`

```jsx
const mapDispatchToProps = dispatch => ({
  setCurrentUser:user =>dispatch(setCurrentUser(user))
})
```

Con esto, quedaría ligada la acción de actualizar el usuario al componente `App.js`

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8ed0e49c-35f5-462d-9d74-7fd83f060f2f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8ed0e49c-35f5-462d-9d74-7fd83f060f2f/Untitled.png)

Y podemos utilizarla para actualizar los datos de usuario:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/19bbc189-cb57-4600-b1c4-719ff31a2b1a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/19bbc189-cb57-4600-b1c4-719ff31a2b1a/Untitled.png)

Si lo hemos hecho todo bien, veremos ahora en consola como se actualiza el **STATE** tras cada acción realizada (en este caso el login), gracias al "middleware" que hemos incluido para "loguear" los cambios:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aa9c9b90-fe51-42c0-a3f0-93afd710eece/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aa9c9b90-fe51-42c0-a3f0-93afd710eece/Untitled.png)

Con esta configuración, vemos como funciona **REDUX**, pues el **HeaderComponent** es consciente de los cambios llevados a cabo en `App.js` sin recibir los PROPS directamente de él.

**Componentes individualizados y aislados, sólo conscientes de lo que nosostros queremos expresamente que sean conscientes, y de forma directa.**

## User redirect and User action type

### Redirección de usuarios autenticados

Queremos aplicar una nueva funcionalidad, si el usuario está autenticado no tiene por qué estar en la página de Login.

Pare ello, necesitamos comprobar el estado del USER desde `App.js`, ya sabemos como hacerlo...

```jsx
const mapStateToProps = ({user}) => ({
  currentUser: user.currentUser
});

const mapDispatchToProps = dispatch => ({
  setCurrentUser:user =>dispatch(setCurrentUser(user))
})

export default connect(mapStateToProps, mapDispatchToProps)(App);
```

Vamos a añadir una redirección nueva:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c87678c1-9001-40fb-9c90-ba8d34877e81/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c87678c1-9001-40fb-9c90-ba8d34877e81/Untitled.png)

Le estamos diciendo que, si está en la ruta `/signin` y está autenticado, que lo redireccione a la página principal `/`

### Creando "enums" para las acciones

Tanto en las `actions` como en `reducer`, estamos usando un STRING como variable. ¿Y si la cagamos al escribir?

Una buena práctica es usar "types" o `enums` para estos casos:

```jsx
export const UserActionTypes = {
  SET_CURRENT_USER: 'SET_CURRENT_USER'
}
```

Y luego llamar a esta variable, siempre, de la forma siguiente:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/25beab71-39c0-42c5-890d-6e3a2bd234f2/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/25beab71-39c0-42c5-890d-6e3a2bd234f2/Untitled.png)

## Estructura de carpetas en REDUX

Presta mucha atención en la forma "lean" y estandarizada que tiene de ir creando las carpetas:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f9333848-9789-4a0b-9b60-41412ab021be/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f9333848-9789-4a0b-9b60-41412ab021be/Untitled.png)

## Cart Component

Vamos a crear ahora el componente "CART", que no es más que el típico carrito de compra similar al que usamos en Amazon.

Cuando añadimos cualquier elemento al carro, tanto el icono superior derecho como propiamente el carro de compra, deben actualizarse con los últimos elementos añadidos. Dinámicamente. Es un caso de manual para aplicar REDUX, almacenando el estado del carro en la ***Store*** y haciendo que tanto el icono como la página del carrito sean conscientes de este y se actualicen con él.

El icono del carrito viene dado por el curso.

Creamos un nuevo componente `CartIcon` que se va a encargar de renderizar el estado del carrito:

```jsx
import { ReactComponent as ShoppingIcon } from '../../assets/shopping-bag.svg';

import './cart-icon.styles.scss';

const CartIcon = () => (
  <div className='cart-icon'>
    <ShoppingIcon className='shopping-icon' />
    <span className='item-count'>0</span>
  </div>
);

export default CartIcon;
```

Con esto tenemos creada la maquetación básica del carrito de compra:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1df3e345-6aa2-4a97-b863-c48b143b573d/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1df3e345-6aa2-4a97-b863-c48b143b573d/Untitled.png)

En la siguiente clase veremos cómo crear el dropdown y darle la funcionalidad necesaria para que maneje su estado.

## Cart Dropdown Component

El siguiente paso es crear el dropdown que aparecerá al clicar en el carrito y que nos va a mostrar el listado de elementos que tenemos en el mismo.

Empezamos como siempre por la maquetación básica, para habilitar el mismo:

```jsx
import CustomButton from '../custom-button/custom-button.component';
import './cart-dropdown.styles.scss';

const CartDropdown = () => (
  <div className='cart-dropdown'>
    <div className='cart-items'></div>
    <CustomButton>GO TO CHECKOUT</CustomButton>
  </div>
);

export default CartDropdown;
```

```css
.cart-dropdown {
  position: absolute;
  top: 90px;
  right: 40px;
  z-index: 5;
  display: flex;
  flex-direction: column;
  width: 240px;
  height: 340px;
  padding: 20px;
  border: 1px solid black;
  background-color: white;

  .cart-items {
    display: flex;
    flex-direction: column;
    height: 240px;
    // overflow: scroll;
  }

  button {
    margin-top: auto;
  }
}
```

Quedando el componente de la siguiente forma (todavía sin lógica aplicada):

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2b98cae6-be42-40de-b55b-692811c1ace6/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2b98cae6-be42-40de-b55b-692811c1ace6/Untitled.png)

## Implementing Redux in Cart

Ahora que ya tenemos el `CartDropdown` y el `CartIcon` con una funcionalidad básica, vamos a crear la forma de mostrar/ocultar el primero en función de si el usuario ha clicado o no en el segundo.

Ambos se encuentran en el componente `Header` , lo lógico entonces sería incluir en este un estado `showDropdown` o similar. Pero ...  ¿qué pasa si queremos llevar este `CartDropdown` a otro sitio?. Dependeríamos de su estado en `Header` ... es por ello por lo que vamos a implementar su estado en REDUX.

Como en el caso del REDUCER para USERS, creamos un nuevo conjunto de carpetas diferenciado: 

`cart.types.js`

```jsx
export const CartActionTypes = {
  TOGGLE_CART_DROPDOWN: 'TOGGLE_CART_DROPDOWN'
};
```

`cart.actions.js`

```jsx
import { CartActionTypes } from './cart.types';

export const toggleCartDropdown = () => ({
  type: CartActionTypes.TOGGLE_CART_DROPDOWN
// No es necesario incluir el PAYLOAD, ya que como vemos en el reducer.js, sólo cambiamos su estado actual
});
```

`cart.reducer.js`

```jsx
import { CartActionTypes } from './cart.types';

const INITIAL_STATE = {
  hidden: true
};

const cartReducer = (state = INITIAL_STATE, action) => {
  switch (action.type) {
    case CartActionTypes.TOGGLE_CART_DROPDOWN:
      return {
        ...state,
        hidden: !state.hidden
      };

    default:
      return state;
  }
};

export default cartReducer;
```

## Add to cart styling

En esta clase trabajamos con los estilos de los items de la tienda:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4009b5bc-e9ac-4432-9371-ea90a4580206/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4009b5bc-e9ac-4432-9371-ea90a4580206/Untitled.png)

Reconfiguramos el componente `CustomButton` para poder invertir los colores existentes:

```jsx
const CustomButton = ({ children, isGoogleSignIn, inverted, ...otherProps }) => (
  <button className={`${inverted ? 'inverted' : ''} ${isGoogleSignIn ? 'google-sign-in' : ''} custom-button`} {...otherProps}>
    {children}
  </button>
);
```

Y dentro del componente que renderiza la lista de elementos a comprar, reconfiguramos el Hoover de cada "carta" y el estilo tanto de esta como del botón interior (el customizado):

```css
.custom-button {
  display: none;
  width: 80%;
  opacity: 0.7;
  position: absolute;
  top: 250px;
}

(...)

&:hover {
  & .image {
    opacity: 0.8;
  }

  & .custom-button {
    display: flex;
    opacity: 1;
  }
}
```

## Cart item reducer

Nos encargaremos ahora de implementar la lógica que permita que, cada vez que cliquemos sobre un elemento que queremos comprar, este cambie el estado del CartStore y la aplicación sea consciente de que hemos añadido un nuevo elemento al carrito de compra.

Empezamos por lo básico, nos vamos al `CartReducer` y añadimos un nuevo estado inicial: 

```jsx
const INITIAL_STATE = {
  hidden: true,
  cartItems: []
};
```

Ahora tenemos que desarrollar la funcionalidad para añadir o eliminar elementos del carrito de la compra.

Una vez creado un nuevo tipo en `CartTypes` (recuerda que es necesario para no cometer errores), añadimos el caso al "cartReducer":

```jsx
const cartReducer = (state = INITIAL_STATE, action) => {
  switch (action.type) {
    case CartActionTypes.TOGGLE_CART_DROPDOWN:
      return {
        ...state,
        hidden: !state.hidden
      };

    **case CartActionTypes.ADD_ITEM:
      return {
        ...state,
        cartItems: [...state.cartItems, action.payload]
      };**

    default:
      return state;
  }
};
```

El siguiente paso es crear una nueva acción para poder lanzar el "dispatch" en el componente:

`cart.actions.js`

```jsx
export const addItem = (item) => ({
  type: CartActionTypes.ADD_ITEM,
  payload: item
});
```

Y lo conectamos a nuestro componente `CollectionItem`:

```jsx
const CollectionItem = ({ id, name, price, imageUrl, addItem }) => {
  return (
    <div className='collection-item'>
      <div className='image' style={{ backgroundImage: `url(${imageUrl})` }}></div>
      <div className='collection-footer'>
        <span className='name'>{name}</span>
        <span className='price'>{price}</span>
      </div>
      <CustomButton inverted>Add to cart</CustomButton>
    </div>
  );
};

const mapDispatchToProps = (dispatch) => ({
  addItem: (item) => dispatch(addItem(item))
});

export default connect(null, mapDispatchToProps)(CollectionItem);
```

Ojo a los PROPS que recibe la función, en este caso en el que estamos pasando el "DISPATCH" como PROP a la par que el resto de elementos, debemos diferenciar claramente cuáles vienen dados por el componente PADRE y cuál es el que le llega mediante `connect()` (mejor revisar el código para entenderlo)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a6e0b463-8b95-4d2a-adce-1b60fce8e079/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a6e0b463-8b95-4d2a-adce-1b60fce8e079/Untitled.png)

`collection-item.component.jsx`

```jsx
const CollectionItem = ({ item, addItem }) => {
  const { name, price, imageUrl } = item;
  return (
    <div className='collection-item'>
      <div className='image' style={{ backgroundImage: `url(${imageUrl})` }}></div>
      <div className='collection-footer'>
        <span className='name'>{name}</span>
        <span className='price'>{price}</span>
      </div>
      <CustomButton onClick={() => addItem(item)} inverted>
        Add to cart
      </CustomButton>
    </div>
  );
};
```

Si hemos realizado la configuración correctamente, al hacer click en cada uno de los elementos de la lista, se lanzará el evento de "ADD_ITEM", y se añadirá el nuevo elemento a la lista del carrito:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9b1817a8-2fc2-4a1b-8ef0-1614e6450a15/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9b1817a8-2fc2-4a1b-8ef0-1614e6450a15/Untitled.png)

## Adding multiple items to cart

Ahora mismo si pulsamos X veces el primer elemento, se añadirá ese elemento X veces al array de datos del CART. 

No queremos eso.

Buscamos que, si se clica sobre un elemento existente, se añada un +1 a este elemento.

**Ojo, que no vale sólo con incrementar ese contador en caso de ser una propiedad del ITEM, debemos volver a crear el objeto con ese contador +1 para que REACT sea consciente del cambio y pueda reflejarlo en el DOM**

Creamos un nuevo archivo `cart.utils.js` para implementar esta funcionalidad. Tal y como se hace referencia en el curso:

> *Utility functions allow us to keep our files clean and organize functions that we may need in multiple files in one location*

## Cart item component

Creamos el componente que mostrará el producto elegido, su precio y cantidad en el dropdown del carrito.

`cart-item.component`

```jsx
const CartItem = ({ item: { imageUrl, price, name, quantity } }) => (
  <div className='cart-item'>
    <img src={imageUrl} alt='item' />
    <div className='item-details'>
      <span className='name'>{name}</span>
      <span className='price'>
        {quantity} x ${price}
      </span>
    </div>
  </div>
);
```

Una vez creado lo utilizamos en el `CartDrodown`, pero claro, para que renderice contenido necesitaremos pasarle el ITEM, ¿verdad?.

Es por ello por lo que vamos a conectar (`connect()`) el STATE del CART al componente `CartDropdown`

```jsx
const CartDropdown = ({ cartItems }) => (
  <div className='cart-dropdown'>
    <div className='cart-items'>
      {cartItems.map((cartItem) => (
        <CartItem key={cartItem.id} item={cartItem}></CartItem>
      ))}
    </div>
    <CustomButton>GO TO CHECKOUT</CustomButton>
  </div>
);

// Conectamos el STATE a los PROPS que recibirá el CartItem para renderizar los ITEMS
const mapStateToProps = ({ cart: { cartItems } }) => ({
  cartItems
});

export default connect(mapStateToProps)(CartDropdown);
```

Et voilá, hemos añadido los diferentes elementos al carrito:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dc6a8f01-5340-49cf-8316-99b8362b0ee4/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dc6a8f01-5340-49cf-8316-99b8362b0ee4/Untitled.png)

Vemos nuevamente como REDUX se comporta de forma unidireccional y su uso, una vez configurado correctamente, es bastante intuitivo. Mucho más que andar con Input() y Output() como en Angular.

## Selectors in Redux

Queremos ahora que se muestre el número total de elementos que tenemos en el carrito, en el propio icono del carrito.

En el componente que renderiza el icono del carrito, `CartIcon`, necesitamos el STATE del carro de compra.

Pero ojo, no necesitamos todo el estado, tan sólo la cantidad acumulada de elementos, es por esto por lo que en este caso, se considera que estamos trabajando o añadiendo u "SELECTOR":

```jsx
const CartIcon = ({ toggleCartDropdown, itemCount }) => {
  console.log('cartItems: ', itemCount);
  return (
    <div className='cart-icon' onClick={toggleCartDropdown}>
      <ShoppingIcon className='shopping-icon' />
      <span className='item-count'>{itemCount}</span>
    </div>
  );
};

const mapDispatchToProps = (dispatch) => ({
  toggleCartDropdown: () => dispatch(toggleCartDropdown())
});

**const mapStateToProps = ({ cart: { cartItems } }) => ({
  itemCount: cartItems.reduce((acc, cartItem) => (acc += cartItem.quantity), 0)
});**

export default connect(mapStateToProps, mapDispatchToProps)(CartIcon);
```

Si dejamos esto así, vamos a ejecturar dicho `mapStateToProps`, como todos, cada vez que se modifique el contenido del STATE de la aplicación. 

Wanna see it?

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5e7f31ac-dc7e-4e3e-9051-2e75b989419e/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5e7f31ac-dc7e-4e3e-9051-2e75b989419e/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0cf74a68-4139-425f-97fd-66ccddb50257/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0cf74a68-4139-425f-97fd-66ccddb50257/Untitled.png)

Y eso sólo abriendo y cerrando el Dropdown. Imaginemos para miles de conectores al State de la APP.

Si es el mismo valor, no deberíamos volver a pasarlo como PROP al componente para que no se renderice de nuevo. Vamos a usar el concepto "Memoization" y una librería para tal fin 

Si quieres repasar el concepto...

[Memoization](https://www.notion.so/Memoization-dab6a10c300543b8864617962db802b8)

## Reselect library

Utilizaremos la librería "Reselect", que va a incrementar la ya de por sí potente (en cuanto a funcionalidad) librería de Redux:

[reselect](https://www.npmjs.com/package/reselect)

Para poder reutilizar los "Selectores":

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/795fbe31-e12c-4165-94f2-0e65f292de70/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/795fbe31-e12c-4165-94f2-0e65f292de70/Untitled.png)

Vamos a cambiar la estructura de carpetas que tenemos, y creamos el archivo `cart.selectors.js`

```jsx
import { createSelector } from 'reselect';

// 2 tipos de selectores que podemos crear: Input / Alpha
const selectCart = (state) => state.cart;

export const selectCartItems = createSelector([selectCart], (cart) => cart.cartItems);

export const selectCartItemsCount = createSelector([selectCartItems], (cartItems) => cartItems.reduce((acc, cartItem) => (acc += cartItem.quantity), 0));
```

Que vamos a utilizar en nuestro componente para poder renderizar el contador de elementos en el carrito, utilizando Memoization para ello (así no se refresca el componente continuamente):

From ...

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/15070023-fb2e-4136-a670-1e23b3382f63/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/15070023-fb2e-4136-a670-1e23b3382f63/Untitled.png)

To ...

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f658d240-337b-4e35-86f4-1f352eff0341/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f658d240-337b-4e35-86f4-1f352eff0341/Untitled.png)

## Quick correction on CartIcon re-rendering

*Hello everyone!*

*I made one mistake in explaining our `CartIcon` component and the `itemCount`! Due to `itemCount` being a primitive (integer), redux will do a shallow equality check under the hood between state changes in `mapStateToProps`. In this case having a selector does not save us on any re-renders of the CartIcon component. If our overall state changes but the itemCount value stays the same between these changes,  redux's shallow equality check will see that `itemCount` is the same value as last time and save us a re-render. It's still valuable to keep the logic for the reduce in a selector though because we do still want to memoize the calculation of `itemCount` (our reduce logic), and without a selector our reduce logic would still be running on every state change regardless of the final calculated value of `itemCount`.*

*The take away here is that redux's `mapStateToProps` has a shallow equality check for every value in the object; it won't replace values if they pass a shallow equality check which means it won't needlessly re-render, but if we have transformation logic it's still valuable to memoize it with a selector to save us running duplicate logic to get the same output.*

*Thank you to student Bruce Liu for pointing this out to me!*

*Happy coding everyone!*

## User selector

Vamos a realizar la misma operación de configurar los "selectors" con el "componente" de REDUX `users`

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7c1c40c9-9b88-46cb-bb72-44a06f2ae319/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7c1c40c9-9b88-46cb-bb72-44a06f2ae319/Untitled.png)

Una vez creados los selectors que utilizaremos en el componente `Header` (y allí donde corresponda), vamos a reconfigurar este:

`header.component.jsx`

```jsx
// configuración previa
const mapStateToProps = ({ user: { currentUser }, cart: { hidden } }) => ({
  currentUser,
  hidden
});

// configuración base
const mapStateToProps = (state) => ({
  currentUser: selectCurrentUser(state),
  hidden: selectCartHidden(state)
});

// ahora imagina que tienes que hacer esto 50 veces, no resulta práctico, para ello utilizamos otra de las funciones de la librería "reselect": createStructuredSelector
import { createStructuredSelector } from 'reselect';

const mapStateToProps = createStructuredSelector({
  currentUser: selectCurrentUser,
  hidden: selectCartHidden
});
```

Comprobamos que el componente sigue funcionando sin ningún problema:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/69eb5d1c-3bbc-4f66-a6fa-26e31348d919/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/69eb5d1c-3bbc-4f66-a6fa-26e31348d919/Untitled.png)

Buscamos el resto de componentes que utilicen la función `mapStateToProps` para modificarlos con la nueva lógica que acabamos de incorporar de la librería `reselect`

Aunque sólo utilizemos un selector en el componente, como es el caso de `App.js`, es conveniente utilizar `createStructuredSelector` para permitir en un futuro la posibilidad de añadir nuevos "selectors" sin modificar mucho el código

Continuamos aplicando el mismo patrón en todos los componentes que utilizan un `mapStateToProps`:

Ejemplo en `cart-icon.component.js`

```jsx
const mapStateToProps = createStructuredSelector({
  itemCount: selectCartItemsCount
});
```

Es muy común que usemos esta librería (`reselect`) cada vez que implementamos REDUX, para utilizar la técnica de `memoization` en nuestra APP

## Checkout page

Vamos a completar el carrito de la compra: mostraremos un mensaje cuando no haya productos en el mismo y habilitaremos el botón para poder ir a la página de compra en la que se confirman los productos.

Una vez creado el mensaje que se mostrará en el carrito si no hay elementos:

```jsx
const CartDropdown = ({ cartItems }) => (
  <div className='cart-dropdown'>
    <div className='cart-items'>
      {cartItems.length ? cartItems.map((cartItem) => <CartItem key={cartItem.id} item={cartItem}></CartItem>) : <span className='empty-message'>Your cart is empty</span>}
    </div>
    <CustomButton>GO TO CHECKOUT</CustomButton>
  </div>
);
```

Pasamos a trabajar con el nuevo componente (page), `CheckoutPage`:

```jsx
import './checkout.styles.scss';

const CheckoutPage = () => <div>Checkout page</div>;

export default CheckoutPage;
```

Una vez creado este, para permitir la navegación desde el `cart-dropdown.component.jsx`, debemos utilizar `withRouter` de la librería `react-router-dom`:

```jsx
import { connect } from 'react-redux';
import { createStructuredSelector } from 'reselect';
**import { withRouter } from 'react-router-dom';**

import { selectCartItems } from '../../redux/cart/cart.selectors';
import CustomButton from '../custom-button/custom-button.component';
import CartItem from '../cart-item/cart-item.component';

import './cart-dropdown.styles.scss';

const CartDropdown = ({ cartItems, history }) => (
  <div className='cart-dropdown'>
    <div className='cart-items'>
      {cartItems.length ? cartItems.map((cartItem) => <CartItem key={cartItem.id} item={cartItem}></CartItem>) : <span className='empty-message'>Your cart is empty</span>}
    </div>
    <CustomButton **onClick={() => history.push('/checkout')}**>GO TO CHECKOUT</CustomButton>
  </div>
);

// Conectamos el STATE a los PROPS que recibirá el CartItem para renderizar los ITEMS
const mapStateToProps = createStructuredSelector({
  cartItems: selectCartItems
});

**export default withRouter(connect(mapStateToProps)(CartDropdown));**
```

**Presta atención a como la función `withRouter()` recibe como parámetro el propio componente, para permitir que este obtenga el parámetro `history`en sus PROPS. Al igual que hicimos antes mediante `connect()` para poder trabajar con `cartItems`**

## Checkout page 2

Creamos un nuevo selector que nos permita obtener el precio total del carrito y lo conectamos al `checkout.component.jsx`:

```jsx
export const selectCartTotal = createSelector([selectCartItems], (cartItems) => cartItems.reduce((acc, cartItem) => (acc += cartItem.quantity * cartItem.price), 0));
```

Realizamos la implementación de esta nueva funcionalidad, de manera básica, para comprobar que funciona:

```jsx
import { connect } from 'react-redux';
import { createStructuredSelector } from 'reselect';

import { selectCartItems, selectCartTotal } from '../../redux/cart/cart.selectors';

import './checkout.styles.scss';

const CheckoutPage = ({ cartItems, total }) => {
  return (
    <div className='checkout-page'>
      <div className='checkout-header'>
        <div className='header-block'>
          <span>Product</span>
        </div>
        <div className='header-block'>
          <span>Description</span>
        </div>
        <div className='header-block'>
          <span>Quantity</span>
        </div>
        <div className='header-block'>
          <span>Price</span>
        </div>
        <div className='header-block'>
          <span>Remove</span>
        </div>
      </div>
      {cartItems.map((cartItem) => cartItem.name)}
      <div className='total'>
        <span>TOTAL: ${total}</span>
      </div>
    </div>
  );
};

const mapStateToProps = createStructuredSelector({
  cartItems: selectCartItems,
  total: selectCartTotal
});

export default connect(mapStateToProps)(CheckoutPage);
```

## Extensible code

> *"Everything is nice, small and simple"*

Es cierto, ninguno de los archivos que hemos creado durante esta parte del curso ocupan más de unas cuantas líneas, algunos de ellos muy pocas de hecho. Estamos modulando y haciendo un código bastante mantenible.

**Esta es la clave. La modulación o fragmentación del código en pequeños bloques sencillos de entender, implementar o mejorar en caso necesario.**

## Dispatch action shortland

Estamos trabajando ahora con `cart-dropdown`, vamos a dotar de una nueva funcionalidad al componente que permita que, una vez que hemos accedido a la página de resumen de compra, se cierre el dropdown (cambie el estado del `toggleCartDropdown` a false)

Habitualmente, o hasta ahora, hemos visto que la operativa para lanzar un "*dispatch*" dentro de un componente es mediante una función que creamos (`mapDispatchToProps` ) y la conectamos mediante `connect(...)` .

```jsx
const CartDropdown = ({ cartItems, history, toggleCartDropdown }) => (
  <div className='cart-dropdown'>
    <div className='cart-items'>
      {cartItems.length ? cartItems.map((cartItem) => <CartItem key={cartItem.id} item={cartItem}></CartItem>) : <span className='empty-message'>Your cart is empty</span>}
    </div>
    <CustomButton
      onClick={() => {
        history.push('/checkout');
        toggleCartDropdown();
      }}>
      GO TO CHECKOUT
    </CustomButton>
  </div>
);

// Conectamos el STATE a los PROPS que recibirá el CartItem para renderizar los ITEMS
const mapStateToProps = createStructuredSelector({
  cartItems: selectCartItems
});

const mapDispatchToProps = (dispatch) => ({
  toggleCartDropdown: () => dispatch(toggleCartDropdown())
});

export default withRouter(connect(mapStateToProps, mapDispatchToProps)(CartDropdown));
```

Pues realmente no es necesario, ya que al usar `connect(mapStateToProps)`, internamente estamos pasando también el "dispatch".... 

Vamos a verlo, hacemos lo que hemos dicho y vamos a ver qué tenemos dentro de `otherProps`:

```jsx
const CartDropdown = ({ cartItems, history, ...otherProps }) => {
  console.log('otherProps: ', otherProps);
  return (
    <div className='cart-dropdown'>
      <div className='cart-items'>
        {cartItems.length ? cartItems.map((cartItem) => <CartItem key={cartItem.id} item={cartItem}></CartItem>) : <span className='empty-message'>Your cart is empty</span>}
      </div>
      <CustomButton
        onClick={() => {
          history.push('/checkout');
          toggleCartDropdown();
        }}>
        GO TO CHECKOUT
      </CustomButton>
    </div>
  );
};

// Conectamos el STATE a los PROPS que recibirá el CartItem para renderizar los ITEMS
const mapStateToProps = createStructuredSelector({
  cartItems: selectCartItems
});

// const mapDispatchToProps = (dispatch) => ({
//   toggleCartDropdown: () => dispatch(toggleCartDropdown())
// });

export default withRouter(connect(mapStateToProps)(CartDropdown));
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a4806fdb-0c7f-47b3-af97-7f15a2bba27b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a4806fdb-0c7f-47b3-af97-7f15a2bba27b/Untitled.png)

Ojo al método `dispatch`, que se recibe como PROP y podemos utilizar dentro del propio componente.

```jsx
<CustomButton
    onClick={() => {
      history.push('/checkout');
      dispatch(toggleCartDropdown());
    }}>
    GO TO CHECKOUT
  </CustomButton>
```

## Checkout item component

Creamos ahora los elementos de la página del "checkout". 

Cada uno de ellos, evidentemente, es un componente propio que también vamos a crear ahora: `checkout-item.component`

Para crear la X de eliminar elemento, utilizamos los UTF-8 Dingbats, que son como "iconos" reconocibles por todos los navegadores:

[HTML Unicode UTF-8](https://www.w3schools.com/charsets/ref_utf_dingbats.asp)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b53cbae5-1eb7-4e4b-995a-68aec32df5cb/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b53cbae5-1eb7-4e4b-995a-68aec32df5cb/Untitled.png)

Por ejemplo, en nuestro caso queremos utilizar la X:

```jsx
<span className='remove-button'>&#10005;</span>
```

Trabajamos ahora en la maquetación básica (ya desarrollaremos luego la funcionalidad de manejar los componentes):

```jsx
import './checkout-item.styles.scss';

const CheckoutItem = ({ cartItem: { name, imageUrl, price, quantity } }) => (
  <div className='checkout-item'>
    <div className='image-container'>
      <img src={imageUrl} alt='item' />
    </div>
    <span className='name'>{name}</span>
    <span className='quantity'>{quantity}</span>
    <span className='price'>{price}</span>
    <span className='remove-button'>&#10005;</span>
  </div>
);

export default CheckoutItem;
```

Y renderizamos el componente desde el `checkout.component.jsx` pasándole como PROP el `cartItem`:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d78ba365-9da5-49c8-9b7d-aafa897761d6/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d78ba365-9da5-49c8-9b7d-aafa897761d6/Untitled.png)

## Remove items from cart

En la anterior clase hemos trabajado con el nuevo componente `checkout-item`, vamos ahora a dotar a este de la funcionalidad para eliminar y modificar la cantidad de elementos del carrito:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/90feff3c-630a-4ed2-aff5-98ddd1f5a775/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/90feff3c-630a-4ed2-aff5-98ddd1f5a775/Untitled.png)

Creamos una nueva "action" que nos permita eliminar objetos de la lista de productos. El procedimiento es el mismo que hemos seguido siempre:

1. Creamos un nuevo "type" en `cart.types.js`:

```jsx
export const CartActionTypes = {
  TOGGLE_CART_DROPDOWN: 'TOGGLE_CART_DROPDOWN',
  ADD_ITEM: 'ADD_ITEM',
  **REMOVE_ITEM: 'REMOVE_ITEM'**
};
```

2. Preparamos la acción en `cart.actions.js`:

```jsx
import { CartActionTypes } from './cart.types';

export const toggleCartDropdown = () => ({
  type: CartActionTypes.TOGGLE_CART_DROPDOWN
});

export const addItem = (item) => ({
  type: CartActionTypes.ADD_ITEM,
  payload: item
});

**export const removeItem = (item) => ({
  type: CartActionTypes.REMOVE_ITEM,
  payload: item
});**
```

3. Dotamos de un nuevo "case" al reducer en `cart.reducer.js`:

```jsx
import { CartActionTypes } from './cart.types';
import { addItemToCart, removeItemFromCart } from './cart.utils';

const INITIAL_STATE = {
  hidden: true,
  cartItems: []
};

const cartReducer = (state = INITIAL_STATE, action) => {
  switch (action.type) {
    case CartActionTypes.TOGGLE_CART_DROPDOWN:
      return {
        ...state,
        hidden: !state.hidden
      };

    case CartActionTypes.ADD_ITEM:
      return {
        ...state,
        cartItems: addItemToCart(state.cartItems, action.payload)
      };

    **case CartActionTypes.REMOVE_ITEM:
      return {
        ...state,
        cartItems: removeItemFromCart(state.cartItems, action.payload)
      };**

    default:
      return state;
  }
};

export default cartReducer;
```

Fijare que en lugar de implementar la funcionalidad directamente aquí, la he transferido al archivo `cart.utils.js`:

```jsx
export const addItemToCart = (cartItems, cartItemToAdd) => {
  const existingCartItem = cartItems.find((cartItem) => cartItem.id === cartItemToAdd.id);
  console.log('existingCartItem: ', existingCartItem);

  if (existingCartItem) {
    return cartItems.map((cartItem) => {
      return cartItem.id === cartItemToAdd.id ? { ...cartItem, quantity: cartItem.quantity + 1 } : cartItem;
    });
  }

  return [...cartItems, { ...cartItemToAdd, quantity: 1 }];
};

**export const removeItemFromCart = (cartItems, cartItemToRemove) => {
  return cartItems.filter((cartItem) => cartItem.id !== cartItemToRemove.id);
};**
```

4. Conectamos el componente al "dispatch" que acabamos de crear:

```jsx
import { createStructuredSelector } from 'reselect';
import { connect } from 'react-redux';

import { selectCartItems } from '../../redux/cart/cart.selectors';
import { removeItem } from '../../redux/cart/cart.actions';
import './checkout-item.styles.scss';

const CheckoutItem = ({ cartItem, removeItem }) => {
  return (
    <div className='checkout-item'>
      <div className='image-container'>
        <img src={cartItem.imageUrl} alt='item' />
      </div>
      <span className='name'>{cartItem.name}</span>
      <span className='quantity'>{cartItem.quantity}</span>
      <span className='price'>{cartItem.price}</span>
      <span className='remove-button' onClick={() => removeItem(cartItem)}>
        &#10005;
      </span>
    </div>
  );
};

const mapDispatchToProps = (dispatch) => ({
  removeItem: (item) => dispatch(removeItem(item))
});

export default connect(null, mapDispatchToProps)(CheckoutItem);
```

¡Hecho!, con esto ya podemos eliminar los objetos del carrito clicando en la X correspondiente.

## Remove items at checkout

Nos toca trabajar con el último item que queda para finalizar el carrito: los botones de incrementar y reducir la cantidad de elementos de dicho producto. 

Es una clase larga, pero el desarrollo es muy similar al que hemos hecho hasta ahora. Tan sólo ten en cuenta que, SIEMPRE, debes pasar una copia del objeto actual (state) para que el componente de REACT sea consciente y renderice nuevamente el cambio.

Una muestra de la función que utilizamos para esto dentro de `cart.utils.js`:

```jsx
export const removeItemFromCart = (cartItems, cartItemToRemove) => {
  const existingCartItem = cartItems.find((cartItem) => cartItem.id === cartItemToRemove.id);
  console.log('existingCartItem: ', existingCartItem);

  if (existingCartItem.quantity === 1) {
    return cartItems.filter((item) => item.id !== cartItemToRemove.id);
  }

  return cartItems.map((cartItem) => {
    return cartItem.id === cartItemToRemove.id ? { ...cartItem, quantity: cartItem.quantity - 1 } : cartItem;
  });
};
```

**Section finished!**
