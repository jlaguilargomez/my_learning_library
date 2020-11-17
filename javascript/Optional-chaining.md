# Optional chaining (?.)

Empecemos por la base, vamos a partir de un objeto como el siguiente:

```jsx
const player = {
	name: 'Pepe',
	role: 'wizard',
	equipment: {
		weapon: 'wizard stick',
		armor: 'colorful tunic',
		amulet: 'magic ring'
	}
}
```

Si queremos acceder al arma del personaje, deberíamos llegar mediante `player.equipment.wapon`, pero ¿qué ocurre si, por lo que sea, el objeto `equipment` no existe en este personaje?

<code >TypeError: Cannot read property 'weapon' of undefined</code>



Para evitar este problema existe el "optional chaining":

[Optional chaining '?.'](https://javascript.info/optional-chaining)

Nos permite asegurarnos de que la propiedad exista antes de acceder a una propiedad propia de esta:

```jsx
player.equipment?.weapon;
```

Ahora bien, cuidado porque NO todos los navegadores incorporan esta "novedad" de ES2020. Si vamos sobre seguro y para evitar el problema del error que hemos visto antes, también podemos hacerlo de la siguiente forma: 

```jsx
(player.equipment || {} ).weapon;
```

Así nos aseguramos de que, en caso de que la propiedad no exista, no nos va a saltar el error bloqueante.

También nos permite acceder a funciones en el caso de que estén definidas:

```jsx
player.doSomething?.();
```
