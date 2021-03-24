## Section overview

Hemos creado los formularios pero... ¿qué pasa con la funcionalidad?

Utilizaremos FIREBASE para manejar esto. Evidentemente NO vamos a memorizar ni a aprender cómo usar esta herramienta al detalle, ¡para eso tenemos la documentación!

[firebase](https://www.npmjs.com/package/firebase)

## Firebase Introduction

Utilizaremos FIREBASE como servidor para nuestra aplicación.

Podemos simplificar muchísimo lo que es un BACKEND para nuestra aplicación mediante el siguiente esquema:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68207dcc-512d-4775-83e5-14f6670bc518/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68207dcc-512d-4775-83e5-14f6670bc518/Untitled.png)

Gracias a FIREBASE podemos gestionar estas 3 patas que necesitaremos en nuestra app sin complicarnos mucho la vida con el backend.

## Note about Firebase version

*Hello everyone!*

*A crucial thing to note is that for the project we are building, the package version we just installed should be firebase 6.0.2. Since the creation of this course, firebase's javascript SDK library has updated and changed how a few of the objects look in the console. Have no worry, the concepts and patterns that you'll learn have not changed, but things may not look the same in the course when you `console.log`  the objects when using a newer version.*

***I highly advise you to use the latest version of firebase! An older version like 6.0.2 may cause issues with newer versions of other packages we are using.** Everything about the api is the same as what you'll see throughout the course, it's just that newer versions of firebase have added extra properties on the objects, so what you'll see in your console.log versus what you'll see in the course will be different, but the properties you see in the course are indeed on the objects so everything will work exactly the same in the course! all the patterns you'll learn throughout this course will work the same!*

## Adding a project to Firebase

Creamos un nuevo proyecto en FB con el nombre de **"crown-db"**

Utilizaremos FB en su versión gratuita, suficiente para lo que queremos llevar a cabo con la aplicación.

Creamos una nueva aplicación web:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2e2cc4da-d54f-4849-8ecb-5474b587458a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2e2cc4da-d54f-4849-8ecb-5474b587458a/Untitled.png)

Y nos quedamos con lo que nos interesa, la SDK de configuración:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aa3d7505-87e1-4f77-9535-fb302672489c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aa3d7505-87e1-4f77-9535-fb302672489c/Untitled.png)

E, imprescindible, instalamos la librería de FIREBASE:

[firebase](https://www.npmjs.com/package/firebase)

## Note about Github

*In the upcoming lessons, we will be adding firebase to our React application. One thing to note is that we will be adding a config object that we get from firebase into our files, and in that config object is an API key. Typically it is good practice not to expose your API key publicly, but in the case of firebase, we have to do so because this is how firebase knows the application is ours! This is perfectly safe, and the intended purpose of this public API key. If you commit your code to Github, you may get a warning from GitGuardian having caught a google key, but GitGuardian has acknowledged that this is not an issue [here](https://twitter.com/search?q=firebase%20api%20key%20gitguardian&src=typd)!*

*How we secure our data is actually done with security rules in the firebase dashboard, but we will cover that in a later lesson! So please continue the course without worry :)*

## Google Sign In Authentication

Una vez instalada la librería de FIREBASE en el proyecto, vamos a configurarla

### Firebase base config

Creamos un fichero `firebase/firebase.utils.js` en el que insertaremos las credenciales dadas al iniciar la aplicación en FIREBASE y configuraremos los módulos que necesitamos:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5184a217-e87a-457e-b26f-752a134dae6b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5184a217-e87a-457e-b26f-752a134dae6b/Untitled.png)

### Configuración módulos

Terminamos de configurar el archivo con la configuración que vamos a utilizar (principalmente el de *autenticación* y *firestone* [almacenamiento]):

```jsx
import firebase from 'firebase/app';
import 'firebase/firestore';
import 'firebase/auth';

const config = {
  apiKey: 'XXX',
  authDomain: 'XXX',
  projectId: 'XXX',
  storageBucket: 'XXX',
  messagingSenderId: 'XXX',
  appId: 'XXX',
  measurementId: 'XXX'
};

firebase.initializeApp(config);

export const auth = firebase.auth();
export const firestore = firebase.firestore();

const provider = new firebase.auth.GoogleAuthProvider();
provider.setCustomParameters({ prompt: 'select_account' });
export const signInWithGoogle = () => auth.signInWithPopup(provider);

export default firebase;
```

### Autenticación google

Vamos al panel de control de FIREBASE y habilitamos el loggin mediante google en nuestra aplicación:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aaeeeac4-ba0a-4c2d-a453-969397fcd7bf/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aaeeeac4-ba0a-4c2d-a453-969397fcd7bf/Untitled.png)

El correo de soporte es habitualmente el mismo que el de la cuenta de FIREBASE

Quedará entonces habilitado:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0ea8bfb9-2c6f-449d-ab3a-85a9fa553a5d/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0ea8bfb9-2c6f-449d-ab3a-85a9fa553a5d/Untitled.png)

Podemos ahora pues hacer la prueba dentro de la aplicación, dotando a uno de nuestros botones de la funcionalidad que al hacer click, abra la modal de autenticación de google:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3871686c-418f-4f5a-a8db-cf2b7634d79e/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3871686c-418f-4f5a-a8db-cf2b7634d79e/Untitled.png)

### Manejo de usuarios autenticados

Ya podemos autenticar a los usuarios. De hecho en el panel de contro de FIREBASE podemos ver aquellos que han aceptado el login a través de la modal pero... 

***¿cómo hacemos que la aplicación sepa quién está y quién no está autenticado y le dé acceso acorde a este?***

Utilizaremos el módulo `auth` que hemos exportado previamente en el archivo `firebase.utils.js`:

```jsx
export const auth = firebase.auth();
```
