# Manejo de errores en Angular

Son diversos los tipos de errores que pueden darse en una aplicación, destacando:

1. Errores de servidor
2. Errores de desarrollo
3. Falta de pruebas (!)

La forma general de manejar errores (controlar) es mediante:

```jsx
try {} catch (err) {}
```

Pero sería insostenible estar haciendo esto en toda la aplicación, por lo que debemos buscar una forma GLOBAL de controlarlos.

El comportamiento por defecto del `ErrorHandler` es mostrar los errores en consola, pero podemos generar una clase que herede de esta y gestione los errores de una forma diferente:

```jsx
import { ErrorHandler } from '@angular/core';

@Injectable()
export class GlobalErrorHandler implements ErrorHandler {
	handleError(error) {
		// do something with the error
	}
}
```

Y lo "proveemos" al módulo donde vayamos a usarlo:

```jsx
@NgModule({
	providers: [{ provide: ErrorHandler, useClass: GlobalError }]
});
```

Aunque también podemos usarlo de forma "global"

(...)

Recuerda los 2 tipos de errores más habituales:

- 40... : el cliente hizo algo inesperado
- 50... : culpa del servidor

De forma similar a lo anterior, podemos crear un servicio que nos ayude en el **manejo de errores**:

```jsx
export class ErrorService {
	getClientMessage(error: Error) : string {
		// do something
	}

	getServerMessage (error: HttpErrorResponse) : string {
		// do something
	}
}
```

---

# HTTP Interceptors

Interceptamos las peticiones y trabajamos con ellas. Podemos **REINTENTAR** o **CAPTURAR ERRORES**

Podemos también utilizar la gestión de errores para mostrar notificaciones (vease snackbar de Angular-Material)

---

## Recursos

[Expecting the Unexpected - Best practices for Error handling in Angular](https://medium.com/angular-in-depth/expecting-the-unexpected-best-practices-for-error-handling-in-angular-21c3662ef9e4)

[Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)
