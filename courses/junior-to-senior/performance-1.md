# Performance (part 1)
---

[***Notion***](https://www.notion.so/jlaguilargomezdevelop/Performance-part-1-82a639a0783d44779bdeceda8cca264e)

---
*El **objetivo** de esta lección es aprender a mejorar la "calidad y velocidad" de la web que tiene en funcionamiento la empresa a la que hemos llegado.*

Se debe tener muy en cuenta el rendimiento de carga de las webs, ya que cualquier tiempo adicional en la carga o petición de datos, imágenes o cualquier fichero extra supone un incremento en el tiempo de carga.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/29df6366-84cd-4b7d-80b2-2def03efbfad/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/29df6366-84cd-4b7d-80b2-2def03efbfad/Untitled.png)

Podemos considerar 3 **"zonas" en las que focalizarnos para mejorar el rendimiento** de las páginas web: Frontend, Backend o la conexión entre ambas.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6aeefae1-1074-4f8e-bc42-7b2fe2d5de89/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6aeefae1-1074-4f8e-bc42-7b2fe2d5de89/Untitled.png)

## Network performance

Tengamos en cuenta que cada carga inicial o posterior en una página web significa una petición de datos de ida y vuelta al servidor. 

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a7f1425d-a1e8-4865-a070-81d4aa99c5c1/Captura_de_pantalla_2020-07-13_a_las_6.27.23.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a7f1425d-a1e8-4865-a070-81d4aa99c5c1/Captura_de_pantalla_2020-07-13_a_las_6.27.23.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e99ae3c0-8699-4fe3-a8b4-5f41b2be8a64/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e99ae3c0-8699-4fe3-a8b4-5f41b2be8a64/Untitled.png)

Una de las claves es reducir el tamaño de los ficheros de texto y de las imágenes.

Para los ficheros de texto (.css, .html, .js ...) tenemos los **"uglify"** que se encargan de cargarse el espacio en blanco y las identaciones del archivo y reducir así considerablemente el tamaño:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ffadaf3d-2b5a-43ce-aa5a-08d0d2b71585/Captura_de_pantalla_2020-07-13_a_las_6.29.23.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ffadaf3d-2b5a-43ce-aa5a-08d0d2b71585/Captura_de_pantalla_2020-07-13_a_las_6.29.23.png)

Evidentemente no lo haremos en esta plataforma, como ya sabes, utilizaremos las librerías necesarias con webpack (como ya has hecho más de una vez).

## Image file format

Una de las claves principales para reducir el tamaño de las imágenes es cambiar el tipo de archivo a un formato comprimido.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bb404a3a-d986-4f3c-8a3d-c780423bb083/Captura_de_pantalla_2020-07-13_a_las_6.31.35.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bb404a3a-d986-4f3c-8a3d-c780423bb083/Captura_de_pantalla_2020-07-13_a_las_6.31.35.png)

Estos que vemos son los formatos clásicos para imágenes dependiendo de las necesidades que tengamos para con elllos: vectorial, logo, animación, calidad ...

Hoy en día existen muchos más formatos y algunos de ellos teóricamente creados para optimizar su carga en navegadores, pero no están soportados 100% por todos los navegadores, por lo que no los tendremos en cuenta de momento.

### Resources: Image File Formats

Want to learn more about Image file types? I recommend you check out these resources:

[https://99designs.com/blog/tips/image-file-types/](https://99designs.com/blog/tips/image-file-types/)

[https://pageweight.imgix.com/](https://pageweight.imgix.com/)

[https://www.sitepoint.com/gif-png-jpg-which-one-to-use/](https://www.sitepoint.com/gif-png-jpg-which-one-to-use/)

## Image optimization

Aquí unas claves para tener MUY en cuenta a la hora de optimizar imagenes: 

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1fe696ac-8f59-43b8-8ba3-4e489c2d7d2d/Captura_de_pantalla_2020-07-13_a_las_6.40.28.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1fe696ac-8f59-43b8-8ba3-4e489c2d7d2d/Captura_de_pantalla_2020-07-13_a_las_6.40.28.png)

**Para reducir imágenes en formato JPG y PNG:**

 **JPG:** 

[JPEG Optimizer - Compress and Resize Your Digital Photos](http://jpeg-optimizer.com/)

**PNG:**

[TinyPNG - Compress PNG images while preserving transparency](https://tinypng.com/)

**Una de las cosas que tenemos que tener más en cuenta es que si vamos a utilizar una imagen que tenga un tamaño máximo de 500 px, no hace falta almacenar esa imagen con un tamaño de 1000 px, por ejemplo. Y esto es clave**

## Media queries

El uso de las media queries es la principal herramienta para controlar qué imágenes cargar en cada dispositivo dependiendo de su tamaño. **Debo tenerlo MUY en cuenta.**

Las imágenes solo se cargarán (comprobado) en el tamaño de pantalla en el que sean solicitadas, por lo que si añadimos una ***media querie*** para dispositivos de < 500 px sólo se descargarán del servidor y mostrarán aquellas imágenes que correspondan con este tamaño, omitiendo la carga de las siguientes hasta que, por el tamaño de la pantalla, sean requeridas.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a38a6aa0-49f8-4b27-8346-65ce67d44e4d/Captura_de_pantalla_2020-07-13_a_las_7.05.07.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a38a6aa0-49f8-4b27-8346-65ce67d44e4d/Captura_de_pantalla_2020-07-13_a_las_7.05.07.png)

**CDN: "Content Delivery Network"**

Otra solución para la optimización de imágenes es el uso de plataformas como **imgIX,**  que se encargan de guardar y optimizar las imágenes en cada petición realizada:

[Image processing and optimization API - Image CDN * imgix](https://www.imgix.com/)

Con esta otra aplicación, podemos eliminar los metadatos de las imágenes:

[View Exif data online, remove Exif online](https://www.verexif.com/en/)

## Delivery optimizations

Otro de los aspectos fundamentales que tenemos que tener en cuenta a la hora de mejorar el rendimiento es el de **reducir la frecuencia de descarga de archivos y el reducir el contenido innecesario.**

Pongamos por caso *JQuery*. ¿Sería necesario descargar toda la librería para unas simples funciones que ya están incorporadas en JS nativo? NO.

Al igual que en muchos casos tampoco es necesario el uso de *Bootstrap*.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/76977495-cde3-4958-b019-85b88c911469/Captura_de_pantalla_2020-07-14_a_las_6.52.14.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/76977495-cde3-4958-b019-85b88c911469/Captura_de_pantalla_2020-07-14_a_las_6.52.14.png)

Imaginemos al "*Delivery man",* que se encarga de transportar dichos archivos.

Pues tiene un máximo de archivos que puede llevar, un peso máximo de los mismos y sólo puede llevar a cabo 1 tarea al tiempo. Es importante saber esto.

Ese "*Delivery man"* es el **HTTP request.**

### Resources: Delivery optimizations

Max parallel http connections in a browser

[Max parallel http connections in a browser?](https://stackoverflow.com/questions/985431/max-parallel-http-connections-in-a-browser)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bb793cd0-77e5-4ca1-83ea-2e8c50702aa8/Captura_de_pantalla_2020-07-14_a_las_6.54.26.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bb793cd0-77e5-4ca1-83ea-2e8c50702aa8/Captura_de_pantalla_2020-07-14_a_las_6.54.26.png)

## #Exercise: improve download speed of a page

Evaluación inicial del tiempo de carga de la página mediante **"lighthouse":**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b5575323-8abc-4e63-9980-45ea3507ea6a/Captura_de_pantalla_2020-07-14_a_las_7.07.40.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b5575323-8abc-4e63-9980-45ea3507ea6a/Captura_de_pantalla_2020-07-14_a_las_7.07.40.png)

1. Minifico JS con la herramienta: 

[JavaScript Minifier](https://javascript-minifier.com/)

2. Reduzco el tamaño de las imágenes con las herramientas indicadas arriba

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d72df91f-d93c-44e1-8ce1-77876e927272/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d72df91f-d93c-44e1-8ce1-77876e927272/Untitled.png)

**Sólo con esto, se ha incrementado la puntuación de la página sustancialmente*

**Cuando hagas auditorias, hazlas en modo incógnito, ya que los plugins reducen notablemente el rendimiento**

**BUNDLING: reducir cantidad de archivos a descargar, uniendo aquellos cuyo código tenga una finalidad similar**

## Critical render path

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5627942f-418c-434e-87d9-a0dd7341c38c/Captura_de_pantalla_2020-07-15_a_las_6.23.37.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5627942f-418c-434e-87d9-a0dd7341c38c/Captura_de_pantalla_2020-07-15_a_las_6.23.37.png)

En el esquema vemos el flujo de trabajo que sigue el navegador desde que inicia la petición GET a la URL indicada hasta que renderiza la página al completo.

### Improve HTML download

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/96cf5253-d28d-4c12-a8a7-42d6319da3e6/Captura_de_pantalla_2020-07-15_a_las_6.29.48.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/96cf5253-d28d-4c12-a8a7-42d6319da3e6/Captura_de_pantalla_2020-07-15_a_las_6.29.48.png)

Comprobamos que **la descarga del SCRIPT de JS en el Header, bloquea la descarga del resto de ficheros**, como el CSS. Es por ello por lo que el SCRIPT como norma debe ir al final del Body.

Exceptuando aquellos casos en los que sea necesario cargarlo desde un inicio porque la renderización de la página depende de este (por ejemplo con Google Analytics)

### Improve CSS download

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7e8cc585-41f9-4040-a44c-5b764b16efa7/Captura_de_pantalla_2020-07-15_a_las_6.34.03.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7e8cc585-41f9-4040-a44c-5b764b16efa7/Captura_de_pantalla_2020-07-15_a_las_6.34.03.png)

En el ejercicio del curso, creamos un script que se encargue de cargar el archivo CSS secundario sólo cuando la página haya terminado de cargarse por completo:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1d32b726-2763-4c63-9918-7f7856f3c6a3/Captura_de_pantalla_2020-07-15_a_las_6.46.03.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1d32b726-2763-4c63-9918-7f7856f3c6a3/Captura_de_pantalla_2020-07-15_a_las_6.46.03.png)

De esa forma conseguimos renderizar todo el contenido y una vez este esté al completo, dar estilo a las partes secundarias de la página.

Podemos introducir también "media queries" en las etiquetas <link> de descarga del CSS, para que sólo se muestren en un determinado tamaño de pantalla (ojo que a pesar de ello se descargan al inicio también).

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/21d22aaa-a90a-4238-8503-0d2468676a08/Captura_de_pantalla_2020-07-15_a_las_6.44.31.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/21d22aaa-a90a-4238-8503-0d2468676a08/Captura_de_pantalla_2020-07-15_a_las_6.44.31.png)

Debemos tener muy en cuenta la especificidad, ya que cuanto mayor sea, más tiempo pasa el DOM buscando el elemento a seleccionar y esto implica un menor rendimiento de la página:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/196891c2-dc48-4c14-b53b-5362c3efbe7c/Captura_de_pantalla_2020-07-15_a_las_6.48.11.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/196891c2-dc48-4c14-b53b-5362c3efbe7c/Captura_de_pantalla_2020-07-15_a_las_6.48.11.png)

Los estilos en linea o dentro de la etiqueta <style> del HTML mejoran sustancialmente el rendimiento, ya que no es necesaria la descarga de un fichero externo para dar estilo. ¿El problema?. Que en cada página se deberían repetir los mismos estilos una y otra vez.

Y eso sí que es un problema a la hora de generar el código.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ab02139c-cf99-4d43-867f-855d8449c640/Captura_de_pantalla_2020-07-15_a_las_6.51.20.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ab02139c-cf99-4d43-867f-855d8449c640/Captura_de_pantalla_2020-07-15_a_las_6.51.20.png)

### Improve JS download

En cuanto el DOM se encuentra con la etiqueta <script>, paraliza la renderización de la página y se pone manos a la obra con la descarga y procesamiento de este fichero.

Tengamos en cuenta además que el archivo de JS puede manipular tanto el DOM como el CSSOM

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b9f56c29-bbf0-4863-8e56-ad3674aeff90/Captura_de_pantalla_2020-07-15_a_las_6.56.13.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b9f56c29-bbf0-4863-8e56-ad3674aeff90/Captura_de_pantalla_2020-07-15_a_las_6.56.13.png)

Estas son las formas de las que disponemos para la "descarga" del SCRIPT: 

- **Normal:** descarga de SCRIPTs críticos que necesitemos desde el inicio de la construcción de la página.
- **Asíncrona**: es como si le dijeramos a otro "delivery man" que se encargara de ir descargando nuestro archivo JS a la par que el principal continúa con el procesamiento del DOM. El problema de este sistema es que el archivo JS se procesará en cuanto este se haya descargado. Si tuvieramos scripts para manejar o modificar elementos del DOM, puede que estos aún no estuvieran renderizados y nos fuera imposible "capturarlos". **Es por esto por lo que esta descarga asíncrona sólo debe usarse para SCRIPTS que no interactúen con el DOM (por ejemplo Google Analytics o "tracking scripts")**
- **Diferida:** SCRIPTs que van a interactuar con el DOM, iremos descargándolo de forma paralela pero no lo ejecutaremos hasta la finalización del "HTML parsing"

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7d02dc95-a819-41bc-ae62-537a0c618f95/Captura_de_pantalla_2020-07-15_a_las_6.56.48.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7d02dc95-a819-41bc-ae62-537a0c618f95/Captura_de_pantalla_2020-07-15_a_las_6.56.48.png)

En el curso (clase 45) se hace un ejemplo de ejercicio de diferentes cargas de Scripts.

### Resources: Async + Defer

One thing that I didn't mention much in the previous video is that because of HTML parsing, the location of the script tags when you put `async` or `defer` attributes on them is important. This is a great resource that explains the importance of this: [https://stackoverflow.com/questions/10808109/script-tag-async-defer](https://stackoverflow.com/questions/10808109/script-tag-async-defer)

**Tener en cuenta que los navegadores están continuamente intentando mejorar su rendimiento. Actualmente por ejemplo, chrome está buscando una forma de parsear de forma paralela los archivos JS para no causar una merma en el rendimiento de carga.**

## #Exercise 3: Improve performance of Keiko Corp Website

Vamos a testear nuestras webs con 2 herramientas principales:

[PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/?hl=es)

[WebPageTest](https://www.webpagetest.org/)

Repo del proyecto:

[aneagoie/keiko-corp](https://github.com/aneagoie/keiko-corp)

Durante la ejecución de la mejora de rendimiento del proyecto debemos valorar los siguientes aspectos que ayudarían a mejorar la velocidad de carga de la página del ejercicio:

- Demasiados archivos CSS y scripts. Se pueden reducir y minificar sin duda. ¿Realmente necesitamos TODA la librería de "Animatios", "JQuery" o "Bootstrap"
- Los SCRIPTS se pueden (y deben) incluir al final del <body>, teniendo en cuenta los diferentes métodos de carga que podemos usar (async, defer)
- Mejorar la carga de imágenes (reduciendo su tamaño, usando media-queries...)
- Insisto NO usar JQuery (ver la página de "youMightDontNeedJQuery")

**Tener en cuenta que podemos tirarnos horas intentando mejorar el rendimiento de una web, pero llega un momento que más tiempo invertido no repercute en mejoras sustanciales. Por eso es mejor focalizarse en los grandes "lastres" de rendimiento y valorar desde ahí.**

## Optional: Resource Prefetching

There is another technique that can be beneficial when optimizing websites. It is easy to misuse, and different browsers have different performance metrics for them so I did not include it in the videos. However, if you are interested and would like to read more about it, this is (In my opinion) the best resource on the topic:

[https://css-tricks.com/prefetching-preloading-prebrowsing/](https://css-tricks.com/prefetching-preloading-prebrowsing/)

### Resources: Performance Tools

Here are some extra resources and guides if you want a little more practice:

**Exercise: Dev Tools:**

1. [View main thread activities in a table](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#activities) to sort activities based on which ones took up the most time.
2. [Analyze frames per second (FPS)](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#fps) to measure whether your animations truly run smoothly.
3. [Monitor CPU usage, JS heap size, DOM nodes, layouts per second, and more](https://developers.google.com/web/updates/2017/11/devtools-release-notes#perf-monitor) in real-time with the Performance Monitor.
4. [Capture screenshots while recording](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#screenshots) to play back exactly how the page looked while the page loaded, or an animation fired, and so on.
5. [View interactions](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#interactions) to quickly identify what happened on a page after a user interacted with it.
6. [Find scroll performance issues in real-time](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#scrolling-performance-issues) by highlighting the page whenever a potentially problematic listener fires.
7. [View paint events in real-time](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#paint-flashing) to identify costly paint events that may be harming the performance of your animations.[View main thread activity](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#main) to view every event that occurred on the main thread while you were recording.

**Other Resources:**

[http://optimizilla.com/](http://optimizilla.com/)

## HTTP2

El protocolo de comunicación HTTP2 nace con un objetivo principal: mejorar la latencia de las conexiones en red (comunicación entre el servidor y el cliente).

Todavía no está completamente generalizado pero se da por hecho que en un futuro no muy lejano lo estará.

Si queremos hacer una prueba, con NODE podemos crear un servidor con HTTP2:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c56ef0c0-7f9b-4116-9b8b-2dec0c6c1e6c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c56ef0c0-7f9b-4116-9b8b-2dec0c6c1e6c/Untitled.png)

## Resources: HTTP/2

Here is a great resource if you want to learn more about what will be coming up in the future with HTTP/2:

[https://developers.google.com/web/fundamentals/performance/http2/](https://developers.google.com/web/fundamentals/performance/http2/)

## HTTP/3

Although HTTP/3 is in very early development and we still have a long ways until it becomes commonplace, I wanted to let you know that the work is already starting on the latest protocol with some really interesting performance opportunities! You can **[read about the details here](https://blog.cloudflare.com/http3-the-past-present-and-future/)**.
