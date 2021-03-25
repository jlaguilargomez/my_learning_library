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
