# Promises

## Ideas fundamentales ...

- **Una ASYNC function es una función que devuelve UNA PROMESA**
- **Es impresdindible el manejo de posibles errores con el bloque `try{} catch(err){}`**
- **Siempre que usamos AWAIT dentro de una función ASYNC, paralizamos esa línea hasta obtener una respuesta.**
- **Presta atención al bloque FOR AWAIT OF ....**
- **Cada vez que tenga que resolver un conjunto de promesas, es buen ejercicio el plantear el orden adecuado para su resolución. Recuerda: *"parallel, sequence, race"***
- **Deberías investigar algo más sobre "paralelismo" en JS ...**

---

### Código en replIt:

[(AdvanceJS)_Asynchronous JS](https://repl.it/@jlaguilargomez/AdvanceJSAsynchronous-JS#index.js)

---

# Async-Await

Una **"Async function"** es una función que devuelve una promesa.

Veamos como una promesa realizada mediante el método habitual, puede resolverse con ASYNC/AWAIT

```jsx
fetch(url)
	.then(resp => resp.json());
	.then(console.log)
```

Podría transformarse en:

```jsx
async function fetchUsers(){
	const response = await fetch(url);
	const data = await response.json();
	console.log(data);
}
```

Cada línea de código escrita con AWAIT, espera a ser ejecutada antes del paso a la siguiente, **dentro de una función con ASYNC**

**NOTA: Ten en cuenta que, con ASYNC-AWAIT, no tenemos un ".catch()" en la promesa, por lo que para la gestión de errores tendremos que usar:**

```jsx
try{...} catch(err) {...}
```

---

# Finally

"***finally***" es un método incluido dentro de las "***Promises***", que nos permite ejecutar una acción cuando la promesa se ha resuelto (esté en estado Ok o rejected):

```jsx
const urls = [
	'https://swapi.dev/api/people/1',
	'https://swapi.dev/api/people/2',
	'https://swapi.dev/api/people/3',
	'https://swapi.dev/api/people/4',
];

Promise.all(urls.map(url => {
	return fetch(url).then(people => people.json())
}))
.then(arr => {
	console.log('1', arr[0])
	console.log('2', arr[1])
	console.log('3', arr[2])
	console.log('4', arr[3])
})
.catch(err => console.log('ugghhh fix it!', err))
.finally(() => console.log('extra'))
```

Sea como sea el resultado de la promesa, se ejecutará la función definida dentro de "***.finally()***", al terminar esta.

---

# For await of ...

Nos permite recorrer una array de promesas (?) Mejor lo vemos en código:

Recuerda que "***for..of..."*** nos permite recorrer cada elemento de un array:

```jsx
const loopThroughtUrl = url => {
	for(let url of urls){
		console.log(url)
	}
}

loopThroughtUrl();
```

De la misma forma, podemos usar la herramienta indicada para recorrer el Array de promesas:

```jsx
const getData2 = async function() {
	const arrayOfPromises = urls.map(url => fetch(url));
	for await(let request of arrayOfPromises){
		const data = await request.json();
		console.log(data)
	}
}

getData2()
```

*Recuerda que siempre que usamos AWAIT dentro de una función ASYNC, paralizamos esa línea hasta obtener una respuesta. Lo mismo está pasando dentro del **for await(...)***

---

# Job Queue

Recordemos unos conceptos básicos sobre el funcionamiento de JS:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/69efaf60-9604-4f5f-a186-fe0aa567a1a0/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/69efaf60-9604-4f5f-a186-fe0aa567a1a0/Untitled.png)

En ECMAScript6, con la creación de **PROMESAS** (no eran nativas de JS), se tuvo que crear una nueva "*cola*" que las procesara, de forma independiente a la "*callback queue*":

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dbdeef26-15ad-464d-afe8-2a93b671c77f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dbdeef26-15ad-464d-afe8-2a93b671c77f/Untitled.png)

Es por eso por lo que, si tenemos el siguiente código:

```jsx
// --- JOB QUEUE ---
// Callback queue - Task queue
setTimeout(() => console.log('1'),0);
setTimeout(() => console.log('2'),0);

// Job Queue - Microtask Queue
Promise.resolve('hi').then(data => console.log('3 ', data));

// Call Stack
console.log('4')
```

*//→ 4; 3 hi, 1, 2*

El ***EVENT LOOP,*** que se encargaba de pasar las tareas finalizadas del ***Callback Queue*** al ***"Call Stack"*** cuando este está vacío, ahora mira primero al "***Job Queue"***

---

# Parallel, Sequence and Race

Imaginemos que tenemos 3 promesas que resolver, vamos a analizar los diferentes modos que tenemos para proceder:

- ***Parrallel***: los 3 de formas paralela, obtendremos el resultado una vez que todos se resuelvan
- ***Sequencial***: quizá la forma en la que queremos que se resuelvan es:  primero el 1, si es OK resuelve el 2 y si este es OK resuelve 3 (son dependientes unos de otros).
- ***Race***: nos vale el resultado del primero que se resuelva de los 3, el resto lo desechamos (?)

Veamos esto en código:

```jsx
// CREAMOS LA FUNCIÓN QUE NOS GENERARÁ LAS PROMESAS
const promisify = (item, delay) =>{
	return new Promise((resolve)=>{
		setTimeout(()=>{
			resolve(item)
		}, delay);
	})
}

const a = () => promisify('a', 100);
const b = () => promisify('b', 5000);
const c = () => promisify('c', 3000);
```

De la siguiente forma (como ya es conocido con `Promise.all()`), obtenemos la **resolución de las promesas de forma paralela**:

```jsx
async function parallel() {
	const promises = [a(),b(),c()];
	const [output1, output2,output3] = await Promise.all(promises);

	return `parallel is done: ${output1}, ${output2}, ${output3}`
}

parallel().then(console.log)
```

Veamos ahora el método `Promise.race(*arrayOfPromises*)`, para **obtener la promesa que primero se resuelve**:

```jsx
async function race() {
	const promises = [a(),b(),c()];
	const output = await Promise.race(promises);
	return `race is done: ${output}`
}

race().then(console.log)
```

Y por último, la **forma secuencial** (necesario cuando datos de una promesa son necesarios para la siguiente, por ejemplo):

```jsx
async function sequence(){
	const output1 = await a();
	const output2 = await b();
	const output3 = await c();

	return `sequence is done: ${output1}, ${output2}, ${output3}`
}

sequence().then(console.log)
```

*Recuerda que la palabara `await` para la ejecución del código en esa línea hasta obtener un resultado...*

**IMPORTANTE: cada vez que tenga que resolver un conjunto de promesas, es buen ejercicio el plantear el orden adecuado para su resolución. Recuerda: *"parallel, sequence, race"***

---

# Threads, Concurrency and Parallelism

***¿¿Dónde van las tareas paralelas cuando se realizan tareas asíncronas??***

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5066ef9c-1bff-4cb7-a7cb-f12da12373c1/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5066ef9c-1bff-4cb7-a7cb-f12da12373c1/Untitled.png)

*El navegador tiene algo llamado "worked threads" que se encarga de gestionar este tipo de tareas, en paralelo a las tareas principales (síncronas).*

Quizá son como tareas "paralelas" de las que no tenemos que preocuparnos **(?)**:

```jsx
const worker = new Worker('worker.js');
worker.postMessage('hello');
```

Ya que se ejecutan de forma paralela, como bien he dicho antes.

Ojo al siguiente diagrama (interprétalo):

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4f91a0f4-9842-4a4b-97f7-947d824457f9/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4f91a0f4-9842-4a4b-97f7-947d824457f9/Untitled.png)

Como sabemos, **JavaScript es "single thread"**, como en el primer caso. Pero, como estamos viendo, hay una forma de hacer algunas tareas en paralelo ...

(son temas bastante avanzados, investigar con detenimiento si quieres saber más sobre este tema ...)
