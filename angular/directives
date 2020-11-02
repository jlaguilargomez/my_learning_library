# Directives

Podemos encontrar 2 tipos de diretivas:

- Attribute directives: look like a normal HTML attribute (could use databinding or event binding). Only affect/change element they are added to `[ngClass] ...`
- Structural directives: affect a whole area in the DOM (elements get added/reordered ...) `[ngFor] ...`

Para crear una nueva directiva de forma manual creamos un archivo `name.directive.ts` en la carpeta correspondiente.

La estructura de este fichero será: 

```jsx
import { Directive } from '@angular/core';

@Directive({
	selector: '[directiveName]'
})
export class nameDirective {
	constructor (private elementRef: ElementRef) {}
}
```

**Mediante `elementRef` estamos "recogiendo" en la directiva el elemento sobre el que se está aplicando**

**Se debe introducir la nueva directiva en `app.module` dentro de `DECLARATIONS` para poder utilizarla en el resto de componentes de la app**

Para ponerla en "acción", usamos:

```html
<p directiveName></p>
```

También se pueden crear directivas de forma automática mediante el comando de **Angular CLI:**

```powershell
ng g d NameOfDirective
```

**Es aconsejable tener en cuenta la estructura de carpetas a la hora de escoger dónde guardar las carpetas. ¿Todas en la misma? ¿Agrupadas por tipo? ....**

Una mejor forma de trabajar con los elementos sobre los que se usa la directiva sin necesidad de acceder directamente mediante el DOM (?) es implementar:

```jsx
(...)

export class NameDirective implements OnInit {
	constructor(private elRef: ElementRef, private render:Render2){}
}

ngOnInit(){
	this.renderer.setStyle(
		// revisar interface para saber los valores que se aceptan en este método
		this.elRef.nativeElement, "background-color", "red"
	)
}
```

**Leo que es una buena práctica el usar `Render` para acceder al DOM y sus métodos para manejar propiedades.**
