# Factory functions

Las "factory functions" son una forma simplificada mediante la cual podemos crear una función con un comportamiento "similar" al que tiene un objeto (...). Mejor lo vemos con un ejemplo.

Creamos una clase DOG:

```jsx
class Dog {
	constructor(){
		this.sound = 'woof';
	}

	bark(){
		console.log(this.sound);
	}
}
```

Y una instancia de la misma: 

```jsx
const toby = new Dog();

toby.bark()  // woof
```

Vamos a realizar ahora el mismo ejemplo mediante una "factory function":

```jsx
const dog = () => {
	const sound = 'woof';

	return {
		bark: () =>{
			console.log(sound);
		};
	}
}

const fox = dog();
fox.bark(); // woof
```
