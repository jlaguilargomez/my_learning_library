# Security
---

[***Notion***](https://www.notion.so/jlaguilargomezdevelop/Security-84b507c4f5b2435b8ba34a2f7ba516dc)

---
La seguridad de nuestras aplicaciones es importantísima. Y muchas veces no lo tenemos tan presente como debemos. Es por ello por lo que vamos a ver en el siguiente módulo del curradísimo curso este, algunos de los conceptos fundamentales que debemos tener en cuenta cuando hablamos de seguridad.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5cfe590f-4537-40dd-a156-a7ee9ebfa1bc/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5cfe590f-4537-40dd-a156-a7ee9ebfa1bc/Untitled.png)

---

## Injections

Es uno de los ataques más comunes que podemos sufrir en cualquier aplicación.

Se basa en la inyección de código "problemático" en las peticiones de nuestra aplicación, desde una tercera fuente.

Una de las más conocidas es la "SQL Injection"

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c1504760-ef92-4e3b-a874-435431b9fb21/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c1504760-ef92-4e3b-a874-435431b9fb21/Untitled.png)

Con el segundo caso, según el ejemplo del video que realiza con [http://www.psequel.com/](http://www.psequel.com/) , utiliza la orden de crear un nuevo valor en la base de datos, para "cargarse" la BBDD entera.

Mediante el segundo, podemos "pasar" alguna contraseña al decirle que acepte el valor `''` o `1=1 (true)`.

La clase 249 es una puta maravilla. Nos pone un ejemplo de una inyección de código en un formulario. ¿Qué hace?, le pasa un `<script>` al input para que se ejecute, camuflado en el error de una etiqueta de imagen:

```jsx
<img src="/" onerror="alert('something')">
```

Es por eso por lo que insertar `innerHTML` directamente en el DOM no es buena idea:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/41d04e5c-c6a3-447e-863a-84d3b2e8213f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/41d04e5c-c6a3-447e-863a-84d3b2e8213f/Untitled.png)

En el caso de pasarle una etiqueta `script` no se ejecuta en primera instancia como medida de seguridad por seguridad (y porque huele mal eso de que se vuelva a ejecutar una vez que el DOM está cargado). 

Peeero, si hacemos lo del segundo caso, al pasarle un `onerror` este se va a lanzar como alternativa al fallo de la carga de la imagen.

Para solucionar este problema, utilizaremos, en lugar del `innerHTML`:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0f339956-f873-4061-bf1d-406d91892b2a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0f339956-f873-4061-bf1d-406d91892b2a/Untitled.png)

Para prevenir problemas de inyección de código, tenemos las siguientes herramientas:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/584fdfe1-374b-41e4-b111-7b64eb2e88d4/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/584fdfe1-374b-41e4-b111-7b64eb2e88d4/Untitled.png)

1. **Sanitize input**: evitar, mediante JS, que el usuario introduzca los elementos que quiera en los inputs
2. **Parametrize queries**: evitar "SQL injections", una vez más, controlar lo que el usuario introduzca en los inputs.
3. **Knext.js or other ORMS:** son librerías que nos ayudan con los manejos de datos de las tablas SQL

**Debemos siempre "purgar" los datos que el usuario pueda mandar al servidor. Ya que mediante los inputs, por ejemplo, puede insertar lo que le venga en gana en nuestras tablas si no lo controlamos adecuadamente.**

---

## 3rd Party Libraries

En estos casos estamos usando código de terceros, que es necesario, pero puede no ser completamente seguro.

Quizá estemos resolviendo un determinado problema, pero a cambio estamos exponiendo información al creador de la librería.

Cada vez que usamos librerías de terceros, es muy recomendable leer reseñas sobre esta, ver la nota que le ponen los usuarios ....

**También, es recomendable ejecutar los siguientes comandos cuando vayamos a usarlas:**

```powershell
npm install -g nsp
nsp check # audit package.json

npm install -g snyk
snyk test # audit node_modules directory
```

Cuando lanzamos el comando NSP, obtenemos:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/69f215f8-1618-4236-b131-df028007f0f5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/69f215f8-1618-4236-b131-df028007f0f5/Untitled.png)

**A día de hoy, con las versiones >6 de NPM, esto ya viene incorporado y podemos ejecutarlo mediante el comando** `npm audit` **o, para solucionar lo que podamos solucionar:** `npm audit --fix`

Al lanzar SNYK (que requiere autenticación con GitHub), se va a revisar todos los ficheros de `node_modules` y nos devuelve un resultado del examen:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/eb7f3473-71b5-4959-9335-23d9121c7a7d/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/eb7f3473-71b5-4959-9335-23d9121c7a7d/Untitled.png)

Ojo al problema, puede que las dependencias que requieren de actualización sean necesarias en dicha versión para otra dependencia, y actualizarlas implique "joderlas":

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fc161e38-bb3e-4421-9a39-672b3177da4f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fc161e38-bb3e-4421-9a39-672b3177da4f/Untitled.png)

Ten muy presente lo que vas a actualizar y las consecuencias que puede tener.

---

## Loggin

Tomar información del sistema para saber qué está pasando.

Usaremos las siguientes librerías:

```powershell
npm install winston
npm install morgan
```

### Morgan

Nos permite monitorizar las peticiones que hacemos al servidor por consola (recuerda instalar CORS como librería del proyecto y ponerla en funcionamiento: `app.use(cors())`)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b611a43a-b7de-4fbc-befc-c066f52c37a9/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b611a43a-b7de-4fbc-befc-c066f52c37a9/Untitled.png)

### Winston

Podríamos simplificarlo muchísimo diciendo que es como un `console.log()` pero con habilidades extras para nuestro servidor:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/21886a0a-f281-4d6c-b57a-1b7e9b69afb7/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/21886a0a-f281-4d6c-b57a-1b7e9b69afb7/Untitled.png)

**Con estas librerías, podemos monitorizar lo que ocurre o ha ocurrido durante la ejecución de la aplicación en determinados momentos, lo que nos ayuda a solventar posibles errores.**

---

## Https Everywhere

SSL/TLS Certificates. 

Si enviamos información en una conexión sin HTTPS, estamos enviándola como texto plano, cualquiera que pueda intereceptar dicha información puede leerla sin problema, ya que no está encriptada.

Las comunicaciones entre cliente y servidor se establecen a través de un "*tunel de encriptación*"

[Getting Started](https://letsencrypt.org/getting-started/)

Contiene la documentación necesaria para establecer protocolos de comunicación seguros en nuestra web.

En el curso también se menciona como recomendación:

[Cloudflare - The Web Performance & Security Company | Cloudflare](https://www.cloudflare.com/es-es/)

---

## (Cross-site scripting) XSS + (Cross-site request forgery) CSRF

***XSS**: puede permitir a una tercera persona inyectar en páginas web visitadas por el usuario código JavaScript o en otro lenguaje similar.*

***CSRF**: el CSRF (del inglés Cross-site request forgery o falsificación de petición en sitios cruzados) es un tipo de exploit malicioso de un sitio web en el que comandos no autorizados son transmitidos por un usuario en el cual el sitio web confía.*

Un ejemplo que se nos muestra en el curso del primer tipo de amenaza, es ejecutar mediante un SCRIPT introducido en la página, el siguiente comando:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/94ea668a-9c7c-4eb6-adcd-185f7190fe67/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/94ea668a-9c7c-4eb6-adcd-185f7190fe67/Untitled.png)

Redirigimos al usuario a la web "hackeada" de nuestra propiedad, y obtenemos la configuración de sus cookies de la web en la que estaba.

Una vez más, la clave para evitar esto es **"SANITIZE INPUTS"** 

Hablemos ahora de CSRF

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/eb5b8f4e-2ad9-49a0-9bbe-6b7f6f2a4999/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/eb5b8f4e-2ad9-49a0-9bbe-6b7f6f2a4999/Untitled.png)

Obligamos o engañamos al cliente para autorizar una petición a un sitio de 3º a través de una supuesta página de confianza (los típicos correos o mensajes haciéndose pasar por el banco)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/330088f1-d243-4cdd-9f97-ae2f99c4ca50/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/330088f1-d243-4cdd-9f97-ae2f99c4ca50/Untitled.png)

El ejemplo es una "burda" simulación de una orden dada directamente a través de los query params

Vamos a realizar un intento de enviar los datos de usuario desde Twitter a una página web de terceros:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5bd38476-884f-434c-9656-da1bfd027d7e/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5bd38476-884f-434c-9656-da1bfd027d7e/Untitled.png)

Twitter, como era de esperar, controla estos problemas

En la siguiente parte, configuramos los HEADERS de las request para que apliquen las restricciones de `Content-Security-Policy`, como hemos visto en Twitter:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/af350bb8-df76-4de5-93d1-d32b668e6011/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/af350bb8-df76-4de5-93d1-d32b668e6011/Untitled.png)

Le estamos indicando desde dónde permitimos que se ejecuten los SCRIPTS (?)

También aplicamos una configuración base de seguridad para las COOKIES:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9953fbae-7a13-4260-ab88-790cb4da9118/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9953fbae-7a13-4260-ab88-790cb4da9118/Untitled.png)

Si nos vamos al navegador y chequeamos el contenido de la configuración de las peticiones:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f7e2b02b-6189-417b-a5f2-68ea3424dbd0/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f7e2b02b-6189-417b-a5f2-68ea3424dbd0/Untitled.png)

*[🧙🏿‍♂️ Esta parte no la he seguido tan bien, necesito darle una vuelta con el contenido que acompaña el módulo]*

Un par de ejercicios para probar esto:

[https://www.hacksplaining.com/exercises/xss-stored](https://www.hacksplaining.com/exercises/xss-stored)

[https://www.hacksplaining.com/exercises/csrf](https://www.hacksplaining.com/exercises/csrf)

### Resources: XSS + CSRF

[Content Security Policy (CSP)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)

[Cross-site scripting for dummies](https://medium.com/hackernoon/cross-site-scripting-for-dummies-be30f76fad09)

[https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)

---

## Code Secret

En algunos casos (erroneos) podemos tener acceso a claves que se han almacenado en variables de entorno globales. Como la API de google. Esto las expone a cualquier usuario que navegue a la página.

Es para esto para lo que utilizamos archivos tipo `environment` (`.env` en REACT) para guardar las variables con código o claves privadas que no queremos mostrar al usuario.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8518e565-2859-497d-97ea-75027ef00933/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8518e565-2859-497d-97ea-75027ef00933/Untitled.png)

Accederíamos a este de la siguiente forma: 

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dc8d16d8-e7f7-4d09-8495-ae2cc05dd9f5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dc8d16d8-e7f7-4d09-8495-ae2cc05dd9f5/Untitled.png)

REACT utiliza la siguiente librería: 

[dotenv](https://www.npmjs.com/package/dotenv)

Que podemos usar igualmente en caso de no encontrarnos en un proyecto con REACT

---

## Secure headers

`npm install helmet`

[helmet](https://www.npmjs.com/package/helmet)

HELMET es otro "middleware" que nos ayuda a establecer cabeceras seguras a la hora de relizar peticiones HTTP

```jsx
const helmet = require('helmet');
(...)

const app = express();

app.use(helmet());
(...)
```

HELMET se encarga de realizar las acciones que hemos llevado a cabo en apartados anteriores, de forma automática

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9c132793-b39f-4031-8161-934728d964b5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9c132793-b39f-4031-8161-934728d964b5/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d03bfb16-fbee-4fa0-85d3-6dbd404bd0ba/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d03bfb16-fbee-4fa0-85d3-6dbd404bd0ba/Untitled.png)

**Consulta la librería para ver cuáles son las "medidas de seguridad" que inyecta por defecto y cuáles otras hay que configurar a mano.**

### Resources: Secure Headers

1. If you are new to HTTP:

[https://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177](https://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177)

2. To learn a little bit more about HTTP Headers:

[https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)

3. HTTP Header Fields:

[https://www.tutorialspoint.com/http/http_header_fields.htm](https://www.tutorialspoint.com/http/http_header_fields.htm)

4. Helmet package documentation:

[https://github.com/helmetjs/helmet](https://github.com/helmetjs/helmet)

---

## Access Control

Una vez que el usuario está autenticado. ¿A qué recursos le dejamos acceder y cuales están "chapados" para su nivel de usuario?

> *Principal of least privilege*

Mediante CORS, establecemos quiénes tienen derecho a hacer uso de nuestro servidor. Podemos configurar la librería ...

[cors](https://www.npmjs.com/package/cors)

Y crear una lista de páginas desde las que permitimos el acceso.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/88ccfb0e-8e0a-4046-8885-bff471397eaf/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/88ccfb0e-8e0a-4046-8885-bff471397eaf/Untitled.png)

---

## Data management

Encriptación de datos, para que las comunicaciones se establezcan con la menor cantidad de datos "públicos".

Veremos dos casos: encriptación de contraseñas y encriptación de datos de la BBDD.

Mediante la librería

`npm i bcrypt`

[bcrypt](https://www.npmjs.com/package/bcrypt)

Podemos gestionar contraseñas (validación, comparación... ):

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cc72e09c-179c-4254-945c-e06e67895229/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cc72e09c-179c-4254-945c-e06e67895229/Untitled.png)

---

## Don't Trust Anyone

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3e4f8de0-e0da-47ef-9a8e-7bcec51bcb65/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3e4f8de0-e0da-47ef-9a8e-7bcec51bcb65/Untitled.png)

Puede resultar paranoico, pero NO lo es. No se debe confiar en ninguna de las partes implicadas en la gestión / uso de nuestra aplicación, ya que en cualquier punto puede existir una vulnerabilidad de seguridad que exponga datos.

Cada vez que establezcamos una comunicación "hacia afuera", o que aceptemos cualquier INPUT de usuario, tengamos muy en cuenta las brechas que estamos abriendo al mundo.

---

## Authentication

Autentificación es el medio mediante el cual aceptamos o sabemos que la persona que está al otro lado, es realmente quien dice ser.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dc1b3b47-c7dd-4634-a226-022361590b26/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dc1b3b47-c7dd-4634-a226-022361590b26/Untitled.png)

Lo veremos más al detalle en la parte de Autenticación

---

## Extra resources

Si quieres saber más sobre temas de seguridad, en esta web se pueden observar y entender las diferentes vulnerabilidades de seguridad que podemos encontrar:

[Pick a Vulnerability to Learn About](https://www.hacksplaining.com/lessons)

Otra buena fuente de información sobre actualizaciones de seguridad es:

[OWASP Foundation | Open Source Foundation for Application Security](https://owasp.org/)
