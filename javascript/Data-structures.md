# Data Structures

## Ideas fundamentales ...

- Creación de un ARRAY en JS desde 0
- Tipos de estructuras de datos
- Hash tables: objetos. Map() y Set()
- Es muy frecuente el uso de ***HASH TABLES*** para la obtimización de ejercicios de búsquedas O(1)

### Codepen

[(AdvanceJS)_Data structures](https://repl.it/@jlaguilargomez/AdvanceJSData-structures)

# Intro data structures in JavaScript

**Data Structures + Algorithms = Programs**

Esta estructura se establece independientemente del lenguaje de programación, framework o librería utillizado.

Las empresas importantes suelen hacer entrevistas relacionadas con estos principios fundamentales antes que sobre lenguajes concretos.

Un ejemplo:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/36672c1c-c2a5-4e39-a92a-7912d79a3ad7/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/36672c1c-c2a5-4e39-a92a-7912d79a3ad7/Untitled.png)

Cada uno de estos "compartimentos" cumple con una función determinada. ¡No vamos a meter los calcetines en la nevera, no!?

Tipos de estructuras de datos:

[8 Common Data Structures every Programmer must know](https://towardsdatascience.com/8-common-data-structures-every-programmer-must-know-171acf6a1a42)

[List of data structures](https://en.wikipedia.org/wiki/List_of_data_structures)

Dos tipos de preguntas habituales en esta materia:

1. **How to build one**
2. **How to use it (suele ser más importante, ya que las estructuras en muchos casos ya han sido construidas y hay que usarlas)**

---

# How computers store data

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b9a14753-ea10-49ba-bfb0-0fa278750fbd/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b9a14753-ea10-49ba-bfb0-0fa278750fbd/Untitled.png)

Variables y conjuntos de datos básicos → RAM

Imagenes, archivos, vídeos → Storage

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4934f7e1-d8f8-47e6-9442-2811cdb28ed6/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4934f7e1-d8f8-47e6-9442-2811cdb28ed6/Untitled.png)

Podemos acceder desde la CPU a cualquier acceso de memoria del listado de la RAM. Ojo que es más sencillo acceder a los datos "más cercanos": acceder a 0 ó 1, será siempre más rápido que llegar a 100

Como sabemos, dichos bits de la RAM almacenan datos. Vemos un **ejemplo de almacenamiento de 2 variables en sistemas de 8 bits.**

Ahora ten en cuenta los siguientes sistemas y piensa sobre ello:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8e60f8a2-f0dd-4857-a9be-c8529545dcce/Captura_de_pantalla_2020-10-07_a_las_8.40.29.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8e60f8a2-f0dd-4857-a9be-c8529545dcce/Captura_de_pantalla_2020-10-07_a_las_8.40.29.png)

Un ejemplo con JAVASCRIPT, si intentamos almacenar un número que no puede almacenar por su estructura de 64 bits, nos devuelve un `infinity`

```jsx
Math.pow(5,10000) // Infinity
```

**El objetivo principal de la buena práctica de la gestión de estructuras de datos es minimizar el esfuerzo que hace el ordenador para leer y escribir datos en la memoria**

Las estructuras de datos más representativas y que más se suelen utilizar (conviene conocer), son las siguientes:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6cea39d4-1ab6-43df-a2b8-4532c6161b59/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6cea39d4-1ab6-43df-a2b8-4532c6161b59/Untitled.png)

**Algunos lenguajes de programación vienen con las estructuras de datos ya implementadas. En otros, como es el caso de JS, tenemos que crearlas**

# Operations in data structures

Las operaciones que podemos realizar más frecuentemente a la hora de manejar estructuras de datos son las siguientes:

- ***Insertion***: insertar nuevos datos
- ***Deletion***: borrar registros existentes
- ***Traversal***: acceder a la ubicación exacta de un registro (?)
- ***Searching***: buscar si cierto registro X existe en nuestra base de datos
- ***Sorting***: ordenar los registros de una estructura de datos
- ***Access***: ¿cómo accedemos a los datos?

En la siguiente tabla se muestra la complejidad de cada OPERACIÓN en cada tipo de estructura de datos:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f8e74642-4a9c-41dc-9e65-7b3023b0cc2b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f8e74642-4a9c-41dc-9e65-7b3023b0cc2b/Untitled.png)

# Arrays

Los "arrays" organizan los datos de forma secuencial (0,1,2,3, ....). Uno detrás de otro.

Es la estructura de datos más "simple" y más veces utilizada.

Vamos a ver algunos ejemplos de complejidad (BIG-O) de algunos métodos sobre ARRAY's:

```jsx
const strings = ['a','b','c','d'];

// 4*4 = 16 bytes of storage

// push
strings.push('e') // 0(1)

// pop
strings.pop();

// unshift
strings.unshift('x') // O(n) - Tenemos que añadir un elemento al inicio del array 
// y cabiar la posición de TODOS los demás elementos

// splice
strings.splice(2,0,'alien'); // O(n)
```

## Static vs Dynamic Arrays

**Static Arrays en C++**

```cpp
int a[20]
```

Tenemos que **especificar el número de elementos que tendrá nuestro ARRAY,** para que prepare el espacio acorde en la memoria.

En lenguajes **DINÁMICOS** como JS y Python, el lenguaje se encarga automáticamente de asignar el espacio adecuado a cada array de forma dinámica. No tenemos que preocuparnos de las asignaciones de memoria. Evidentemente tiene sus puntos positivos y los negativos.

## Implementing an Array

En JS la forma más sencilla de crear un ARRAY es la siguiente:

```jsx
const a = [];
```

Pero vamos a ver cómo podemos CREAR un ARRAY desde cero (como una estructura de datos).

```jsx
class MyArray{
	constructor() {
		this.length = 0;
		this.data = {}
	}

	get(index){
		return this.data[index]
	}

	push(item){
		this.data[this.length] = item;
		this.length++;
		return this.length;
	}

	pop(){
		const lastItem = this.data[this.length-1];
		delete this.data[this.length-1];
		this.length--;
		return lastItem
	}

	delete(index){
		const item = this.data[index];
		this.shiftItems(index);
		return lastItem;
	}

	shiftItems(index){
		for(const i=index; i<this.length-1; i++){
			this.data[i] = this.data[i+1];
		}
		delete this.data[this.length-1];
		this.length--;
	}
}

const newArray = new MyArray();
newArray.push(1)
newArray.push('hey')
newArray.push('13')

newArray.delete(2)
```

**Presta atención al método de creación de un ARRAY desde su principio más básico: un OBJETO**

**Debemos considerar cualquier ejecicio sobre STRINGS como si se tratara de un ARRAY. Siempre convertir el STRING en un ARRAY y luego volver al origen**

## Arrays Review

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5f6a12ce-c614-4905-a1a9-9eda6561b88e/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5f6a12ce-c614-4905-a1a9-9eda6561b88e/Untitled.png)

---

# Hash Tables

"*Maps (JAVA), dictionaries (PYTHON), objects (JS), hashes (RUBY) ...."*

Para encriptar la información o las KEYS de los objetos, utilizamos el MD5 Hash Generator

[MD5 Hash Generator](https://www.md5hashgenerator.com/)

En muchos casos, las "hash tables" son más óptimas que los ARRAYS (chequea big O):

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aa9a7682-52a2-4d7a-9160-b7c6f40aeda1/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aa9a7682-52a2-4d7a-9160-b7c6f40aeda1/Untitled.png)

Vamos a ver ahora uno de los problemas que presentan:

## Hash collisions

A veces, cuando guardamos nuevos valores en el "hash table", este se intenta asignar en el mismo espacio de memoria, no puede y genera un link subsidiario de este. Esto dificulta el posterior acceso y filtrado de datos.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/96db129c-349e-437b-abb4-96a8e09cd24e/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/96db129c-349e-437b-abb4-96a8e09cd24e/Untitled.png)

Para verlo en "vivo":

[Open Hashing](https://www.cs.usfca.edu/~galles/visualization/OpenHash.html)

Por lo que la complejidad de la búsqueda  se convierte en `O(n)`

[Colisión (hash)](https://es.wikipedia.org/wiki/Colisi%C3%B3n_(hash))

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/983a8d10-07be-42a6-b658-d2ac7e293111/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/983a8d10-07be-42a6-b658-d2ac7e293111/Untitled.png)

## Hash tables in different languages

Con la llegada de ES6, aparecieron dos tipos de estructuras de datos más para JS, similares a los objetos (primas hermanas):

- `Map()`
- `Set()`

**MAP**

Posibilita la creación de objetos key-value, pudiendo ser la KEY algo diferente a un string.

¡Mantiene el orden de inserción! (mira el esquema de arriba)

**SET**

Sólo almacena las "keys", no los values. (?)

## Implementing a Hash Table

Mediante un ejemplo en el que creamos una "**hash table**" y almacenamos y recuperamos datos, vamos a entender en profundidad el concepto de este tipo de **estructuras de datos.**

[DataStructures: Hash Table exercise](https://repl.it/@jlaguilargomez/DataStructures-Hash-Table-exercise)

Presta atención a cómo se "encripta" cada palabra y se almacena según esta "key", mediante el método `_hash()`

## Hash tables VS Arrays

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/51e270af-5d34-43b7-95ae-19baafd2fd46/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/51e270af-5d34-43b7-95ae-19baafd2fd46/Untitled.png)

Las "**hash tables**" son buenas si queremos tener acceso inmediato a ciertos elementos de esta. En un ARRAY nos lleba más tiempo.

Por esto es por lo que se suele usar este tipo de estructuras de datos en las **BBDD.**

## Ejercicio tipo de optimización de estructuras de datos (Google)

[firstRecurringCharacter](https://repl.it/@jlaguilargomez/firstRecurringCharacter)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/57a29f98-3c9e-47ef-8e13-c3052c3062da/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/57a29f98-3c9e-47ef-8e13-c3052c3062da/Untitled.png)
