Te deja elegir si quieres usar Routing o no y qué librería var a incluir para ello.

Utilizaremos **React Routing**:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1ccffeaf-8a5c-4e9d-89e7-30676b7d49dc/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1ccffeaf-8a5c-4e9d-89e7-30676b7d49dc/Untitled.png)

[React Router: Declarative Routing for React](https://reactrouter.com/)

Esta librería maneja internamente la API del navegador que se encarga de guardar y crear rutas de navegación (para poder navegar a través de ellas).

## Routing: configuración de index.js y App.js

Para el uso de rutas, configuramos en primera instancia el componente base `index.js`

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';

import { BrowserRouter } from 'react-router-dom';

ReactDOM.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>,
  document.getElementById('root')
);
```

Y nos vamos al que va a ser la raíz de las rutas: `App.js`

```jsx
import React from 'react';
import HomePage from './pages/homepage/homepage.component';
import { Switch, Route } from 'react-router-dom';

import './App.scss';

const HatsPage = () => (
  <h1>HATS PAGE</h1>
)
function App() {
  return (
    <div>
      <Switch>
        <Route exact path='/' component={HomePage}></Route>
        <Route path='/hats' component={HatsPage}></Route>
      </Switch>
    </div>
  );
}
```

Presta atención a la importancia del atributo `exact` que hace que la ruta deba ser estrictamente `'/'` para poder renderizar lo indicado.

## Navegación por componentes

Cualquier componente renderizado mediante `ReactRouting` recibe lo siguientes PROPS al crearse: *history*, *location*, *match*

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e7f3e1b1-f4ff-47ec-9d2d-ef0bb3c77eb5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e7f3e1b1-f4ff-47ec-9d2d-ef0bb3c77eb5/Untitled.png)

Esto facilita el acceso a determinados valores internos de la ruta en los componentes. Un ejemplo:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b96393ff-763f-48b3-aba7-f8e5ab2a1f12/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b96393ff-763f-48b3-aba7-f8e5ab2a1f12/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/625578fd-2b10-4610-81b5-4a8c5866a538/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/625578fd-2b10-4610-81b5-4a8c5866a538/Untitled.png)

Date cuenta que al navegar entre páginas en una SPA, la navegación es virtual. Y más en React con el DOM virtual (no estamos navegando realmente, sino que se está produciendo un cambio de elementos del DOM).

Es por esto por lo que se hace necesario también modificar el "historial" de navegación de forma "simulada".

Para ello tenemos un método propio de la librería, `Link` o un método propio del API de navegación del navegador:

## Link component

**Ojo que `link` lo importamos de `'react-router-dom'`**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e154568c-437d-4781-a3a5-2fe010a54d8e/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e154568c-437d-4781-a3a5-2fe010a54d8e/Untitled.png)

Método usado habitualmente con la librería

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/36546f03-0b84-40b8-ae0f-dd10fa8b5eff/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/36546f03-0b84-40b8-ae0f-dd10fa8b5eff/Untitled.png)

Navegación dinámica y cambio del historial de navegación

## Modificando "history"

Para que un componente "child" pueda acceder al `history` del navegador, podemos pasarlo como PROPS a través de los sucesivos padres o podemos hacerlo bien, con la Factory Function `withRouter()` de la librería:

```jsx
const MenuItem = ({ title, imageUrl, size, history, linkUrl }) => (
  <div
    className={`${size} menu-item`}
    onClick={() => {
      history.push(linkUrl);
    }}>
    <div
      className='background-image'
      style={{
        backgroundImage: `url(${imageUrl})`
      }}
    />
    <div className='content'>
      <h1 className='title'>{title.toUpperCase()}</h1>
      <span className='subtitle'>SHOP NOW</span>
    </div>
  </div>
);

// Nos permite poder acceder al "history"
export default withRouter(MenuItem);
```

**Muy importante lo que vamos a ver a continuación, usando el SPREAD OPERATOR para no tener que ir pasando los parámetros individualmente como PROPS**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/09738083-6a37-44fa-ba26-6d6a4811aa80/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/09738083-6a37-44fa-ba26-6d6a4811aa80/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5a057571-84f1-49e0-a990-7b1990e4f010/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5a057571-84f1-49e0-a990-7b1990e4f010/Untitled.png)
