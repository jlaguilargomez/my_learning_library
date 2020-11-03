# Call, apply, bind

En las funciones, al crear un contexto de ejecucion, se crean los objetos **variable environment y outer environment** , que se representan gracias a la palabra clave THIS

**THIS** apunta en memoria a la referencia del objeto del contexto actual.

Un ejemplo:

```jsx
const myObject = {
	name: 'Bruce Lee',
	foo: function() {
		this.name = 'Jackie Chan',ç
		console.log(this);
	}
};

myObject.foo() // {name: 'Jackie Chan', foo: [function:foo]}
```

Podemos cambiar su contexto de ejecución!!

## bind()

Lo usaremos para cambiar localmente el contexto de la función, sin ejecutarla:

```jsx
const printBinded = print.bind(person);
printBinded('hello','loquesea');
```

## call()

En este caso, además de cambiar el contexto, ejecutamos la función.

Recibe como parámetro la referencia a la cual debería enlazar o apuntar el THIS, dentro de la función que se ejecuta:

```jsx
print.call(person, 'hello', 'loquesea')
```

## apply()

Usada como **CALL** cuando tenemos una gran cantidad de argumentos. Permite pasarlos como ARRAY

```jsx
print.apply(person, ['hello','loquesea'])
```

---

Permite manipular el THIS de una función.

Tengamos en cuenta lo siguiente:

```jsx
foo() === foo.call(this)
```

Un ejemplo cambiando el THIS de una función:

```jsx
const wizard = {
	name: 'Merlin',
	health: 50,
	heal() {
		return this.health =100
	}
};

const archer = {
	name: 'Hood',
	health: 70
}
```

Podemos ejecutar el método del WIZARD para "curar" al archer:

```jsx
wizard.heal.call(archer);
```

Como hemos visto, **BIND()** devuelve una nueva función, sin ejecutar, con el contexto seleccionado:

```jsx
wizard.heal.bind(archer)()
```
