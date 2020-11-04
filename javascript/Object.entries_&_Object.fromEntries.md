# Object.entries() & Object.fromEntries() 

`Object.entries()` permite transformar un objeto de datos en un ARRAY agrupando CLAVE-VALOR y `Object.fromEntries()` al contrario

¿Y para qué?

Para poder realizar transformaciones con los métodos de los ARRAYS como **filter, map, reduce ...**

Así podemos transformar los datos con el flujo:

OBJECT - ARRAY - OBJECT

```jsx
Object.fromEntries(Object.entries(**object**).filter(() => {
	// do something
}))
```

---

## Recursos

[Object.entries()](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Object/entries)

[Object.fromEntries()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/fromEntries)
