# The complete Junior to Senior Roadmap

# Intro

Dos artículos interesantes a tener en cuenta:

[Don't be a Junior Developer | Zero To Mastery](https://zerotomastery.io/blog/dont-be-a-junior-developer/)

[Don't be a Junior Developer: The Roadmap | Zero To Mastery](https://zerotomastery.io/blog/dont-be-a-junior-developer-the-roadmap/)

---

# 1. Introduction to SSH

*El **objetivo** de esta lección es establecer una conexión SSH a nuestro perfil de GitHub*

**SSH (Security Shell)** es un protocolo como pueden ser HTTP, HTTPS, FTP ...

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7fd8ba64-e2b5-464f-97c1-96588ad00626/Captura_de_pantalla_2020-07-09_a_las_21.22.20.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7fd8ba64-e2b5-464f-97c1-96588ad00626/Captura_de_pantalla_2020-07-09_a_las_21.22.20.png)

**SSH** permite la comunicación directa entre ordenadores y la posibilidad de modificar ficheros pertenecientes a otro dispositivo. Encriptado.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/44224a66-5e90-4684-b531-495220d109a2/Captura_de_pantalla_2020-07-09_a_las_21.24.16.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/44224a66-5e90-4684-b531-495220d109a2/Captura_de_pantalla_2020-07-09_a_las_21.24.16.png)

Como se ha comentado, es una comunicación ENCRIPTADA, lo que hace que pueda permanecer ocultas a "miradas" indiscretas. Seguridad++

En el curso se realiza una **emulación de una conexión mediante SSH a un servidor remoto** gestionado a través de Digital Ocean:

[Welcome to the developer cloud](https://try.digitalocean.com/developerbrand/?_dkitrig=Cloud)

```jsx
ssh root@167.99.146.57
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a87afefb-6d8a-4cc4-bc4b-825f8a6919b4/Captura_de_pantalla_2020-07-09_a_las_21.33.46.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a87afefb-6d8a-4cc4-bc4b-825f8a6919b4/Captura_de_pantalla_2020-07-09_a_las_21.33.46.png)

En la consola de Linux es facil establecer esta conexión, pero en Windows.... debemos usar "**Putty**"

Mediante este sencillo comando, establecemos una conexión remota con cualquier ordenador del mundo que esté preparado para este tipo de conexiones....

**Como conexiones SSH, ¿qué tal la comunicación con GitHub?: cuando estableces una conexión con el servidor, probablemente lo configures mediante SSH. El resto de comunicaciones también se hacen mediante este método, salvo que uses el protocolo HTTPS**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6a7153f2-d6dd-40e5-9e57-56417e931a15/Captura_de_pantalla_2020-07-09_a_las_21.40.53.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6a7153f2-d6dd-40e5-9e57-56417e931a15/Captura_de_pantalla_2020-07-09_a_las_21.40.53.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4b7a9a59-2f5c-40c7-bbd0-37ca4f1a4318/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4b7a9a59-2f5c-40c7-bbd0-37ca4f1a4318/Untitled.png)

### Recursos: SHH comandos

**Windows:**

Use PuTTY:

[https://mediatemple.net/community/products/dv/204404604/using-ssh-in-putty-](https://mediatemple.net/community/products/dv/204404604/using-ssh-in-putty-)

**Windows 10:**

[https://www.howtogeek.com/336775/how-to-enable-and-use-windows-10s-built-in-ssh-commands/](https://www.howtogeek.com/336775/how-to-enable-and-use-windows-10s-built-in-ssh-commands/)

Extra:

1.

[https://www.ssh.com/ssh/putty/windows/](https://www.ssh.com/ssh/putty/windows/)

2.

[https://www.memset.com/docs/server-security/secure-communication-ssh/using-ssh-windows/](https://www.memset.com/docs/server-security/secure-communication-ssh/using-ssh-windows/)

**Linux:**

You should be able to use the

```
ssh
```

command already, but in case you can't:

[https://www.makeuseof.com/tag/beginners-guide-setting-ssh-linux-testing-setup/](https://www.makeuseof.com/tag/beginners-guide-setting-ssh-linux-testing-setup/)

Also, if you have any issues with this set up, please reach out to our chat room so that one of us can help you out :)

## Instalando un repo en un ordenador remoto

Vamos a comenzar una prueba en la que se nos pide que reinstalemos una página web caida en un servidor externo.

El primer paso para ello es instalar GIT mediante:

```jsx
sudo apt-get install git
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3ac73c7e-a829-4f1b-8856-0077ec3fb5f2/Captura_de_pantalla_2020-07-10_a_las_6.31.51.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3ac73c7e-a829-4f1b-8856-0077ec3fb5f2/Captura_de_pantalla_2020-07-10_a_las_6.31.51.png)

Además de trabajar con los comandos de Git, instalar Node y NPM, copiamos una carpeta que tenemos en local en ordenador remoto:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2c89933c-929a-4c43-b3e3-f63c20a299b4/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2c89933c-929a-4c43-b3e3-f63c20a299b4/Untitled.png)

> Opcional: se ofrece un crédito de $100 para registrar un servidor en Digital Ocean mediante este enlace: [https://m.do.co/c/ef8add492554](https://m.do.co/c/ef8add492554)

## Crear un servidor virtual para almacenar y poder renderizar una web mediante SSH

[How To Set Up Apache Virtual Hosts on Ubuntu 16.04 | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-16-04)

## ¿Cómo funciona SSH?

SSH utiliza tres técnicas:

- *Symmetrical Encryption*
- *Asymmetrical Encryption*
- *Hashing*

También son técnicas que debemos tener en cuenta cuando trabajamos con HTTPS, blockchain ...

### Symmetrical Encryption

**Encriptar es una forma de transformar un texto de una forma que es imposible para una tercera parte leerlo sin desencriptarlo**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/adf3cfc2-8d4e-4c69-8d9d-64c73e29601d/Captura_de_pantalla_2020-07-10_a_las_6.48.43.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/adf3cfc2-8d4e-4c69-8d9d-64c73e29601d/Captura_de_pantalla_2020-07-10_a_las_6.48.43.png)

Mediante ***"symmetrical encription"* utilizamos la misma "llave" para encriptar el texto mandado como para desencriptarlo**. Con el problema evidente que puede verse a simple vista: quien poseea dicha "llave", puede leer nuestro texto sin problema.

Pero ese código que permite la desencriptación no es transmitido directamente, sino que se calcula a través de un algoritmo de encriptación que poseen cada una de las partes

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d60d2235-119d-4fed-9fbd-f4e7883c812a/Captura_de_pantalla_2020-07-10_a_las_6.52.28.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d60d2235-119d-4fed-9fbd-f4e7883c812a/Captura_de_pantalla_2020-07-10_a_las_6.52.28.png)

### Asymmetrical Encryption

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/04ebeefc-c931-48f4-b3bf-96f4c169c7a2/Captura_de_pantalla_2020-07-10_a_las_6.55.23.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/04ebeefc-c931-48f4-b3bf-96f4c169c7a2/Captura_de_pantalla_2020-07-10_a_las_6.55.23.png)

**En este tipo de encriptación, ambos dispositivos generan unas claves temporales y comparten con el que estén conectados la clave "pública"**

Se puede decir que **tenemos una clave "pública" y otra "privada" en cada uno de los dispositivos.** Ambas necesarias para desencriptar el código y dependientes una de la otra. 

La pública se puede compartir sin problema, ya que su funcionalidad completa es dependiente de la segunda.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/238df3e1-302d-49c4-a698-4b6ec82796b7/Captura_de_pantalla_2020-07-10_a_las_6.59.04.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/238df3e1-302d-49c4-a698-4b6ec82796b7/Captura_de_pantalla_2020-07-10_a_las_6.59.04.png)

El proceso "funciona" como se ve en la imagen superior, una vez que se ha enviado el mensaje encriptado y asegurado con la clave pública azul, la única forma de poder desencriptarlo es mediante la clave privada correspondiente (azul). 

Así nos aseguramos que terceras partes no pueden acceder al elemento.

**Mucha gente cree que el protocolo SSH utiliza siempre una "encriptación asimétrica", pero no es así. Este tipo de encriptación se utiliza de forma paralela a la "encriptación simétrica" para poder descifrar la "key" que nos permite acceder al recurso (llave amarilla)**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/18ab7775-571d-4b87-8de5-19796b2f711b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/18ab7775-571d-4b87-8de5-19796b2f711b/Untitled.png)

Mediante este método podemos compartir la "llave amarilla" que será desencriptada en cada ordenador en el momento necesario mediante la "llave privada"

> Puedes buscar este concepto mediante el término: *"Diffie Hellman key"*

### **Resources: Asymmetric Encryption**

Want to learn more about Asymmetric Encryption? 

Check out these extra videos :

[https://www.youtube.com/watch?v=NmM9HA2MQGI](https://www.youtube.com/watch?v=NmM9HA2MQGI)

[https://www.youtube.com/watch?v=Yjrfm_oRO0w](https://www.youtube.com/watch?v=Yjrfm_oRO0w)

[https://www.youtube.com/watch?v=vsXMMT2CqqE&t=](https://www.youtube.com/watch?v=vsXMMT2CqqE&t=)

[https://www.youtube.com/watch?v=NF1pwjL9-DE](https://www.youtube.com/watch?v=NF1pwjL9-DE)

### Hashing

Esto me cuesta un poco más verlo, digamos que es un nivel adicional de encriptación en origen y en final mediante una "Hash function", sólo desencriptable mediante una clave privada contendia en la key que se envía.

¿Se envía de forma paralela y se confirma si es igual o no a la clave original?

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d99334dd-de78-4e95-8d99-2336d2e38c5b/Captura_de_pantalla_2020-07-10_a_las_7.55.19.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d99334dd-de78-4e95-8d99-2336d2e38c5b/Captura_de_pantalla_2020-07-10_a_las_7.55.19.png)

### Password or SSH?

En una conexión SSH, lo habitual es que el HOST nos pida un password de usuario para verificar nuestra identidad y validar la conexión.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/744d0137-979e-4a2e-8990-594c9790f23f/Captura_de_pantalla_2020-07-10_a_las_7.58.28.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/744d0137-979e-4a2e-8990-594c9790f23f/Captura_de_pantalla_2020-07-10_a_las_7.58.28.png)

El problema de esto es que es vulnerable a ataques de fuerza bruta. Es decir, podemos tener un script continuo comprobando contraseñas y quizá podamos terminar por acceder si no es esta demasiado segura.

Tenemos otra forma de autenticarnos en una conexión SSH (la que utiliza GitHub, por ejemplo...)

**Usaremos RSA que permite verificar la identidad del usuario que se conecta sin el uso de Password**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/543915fd-75f0-449e-aa36-5d23f8fe0156/Captura_de_pantalla_2020-07-11_a_las_12.15.17.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/543915fd-75f0-449e-aa36-5d23f8fe0156/Captura_de_pantalla_2020-07-11_a_las_12.15.17.png)

De las dos claves que se crean, la primera es **INTRASFERIBLE**, ya que es la clave privada, mientras que la segunda (.pub) es la clave pública.

Con la clave pública que hemos generado, vamos al HOST de Digital Ocean, buscamos la carpeta /.ssh y copiamos su contenido en el fichero **authorized_keys.**

De esta forma hemos **transferido la clave pública al Host** remoto.

**El comando para copiar el contenido de un fichero en terminal de mac es:**

```jsx
pbcopy < *rootToFile*
```

Este sería el contenido tipo de un archivo [SSH.pub](http://ssh.pub) creado:

```jsx
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC+wKBtER2akB7qkR4//qY4j/c/giOINOhnZCzx9lmNxJO5fUefF9jluk1T58s6ckiY1T2EkZEVmhuCeqRMY4oUDv3aARjA+qvXBV+aNJqofzTLGq0Nay0yyQkWjSg88ap+3+OX/CQ0glhnYUwXeZkmAp2Nbfh7SF5ipQYDEO6L5UGxOp5lhiQ+krwguxXT3cetMLCMMYUeb4UiMEYJpVXbOLZz/FJMa5JXK4c1ckJoAGMBOPfYSvDzjHsvQKbzAej8k5QJ3a9KZuX0FAgdBqWTiqq0N+w6mtiTdZuwiFNfrd5v6OnDZcPuz+1KnVyy+6EWkY2kF8g9xopp965hvR0+vkGLZ5+gTzg2HeGSUTuiHqFxXUYBi2ifvvwyKe+B0JHWKyNgLN0kv1xU+sdSUFQ8d5lOVii2jZVEWievsm09/p4PoleP2kkowz4w4PHLx8wBPSQNwFxRuKRN6sq0Y0FD9Z2AlLqvWestuib78DyNsOwqcOHvYIaOlXLEqpoBUIM= jlaguilar@MacBook-Air-de-Jose-2.local
```

[Quick Note: SSH Into A Server](https://www.notion.so/Quick-Note-SSH-Into-A-Server-0355b73ebac04ff4823f206d307e303f)

[Resources: SSH Into A Server](https://www.notion.so/Resources-SSH-Into-A-Server-a15904ef40a249078bf2c8d6bb674ec6)

## #Exercise: Set Up SSH on GitHub

El hecho de establecer la conexión a GitHub mediante SSH es conveniente para no tener que estar realizando la verificación mediante User+Pass cada vez que queremos hacer algún cambio en un repo.

[](https://github.com/antonykidis/Setup-ssh-for-github/blob/master/Setup-ssh-on-github.pdf)

**El caracter "~" equivale a "/Users/your-user-name/"**

Si tienes problemas con los permisos de las carpetas en el Mac:

[https://superuser.com/questions/1256286/mac-os-x-high-sierra-missing-ssh-folder](https://superuser.com/questions/1256286/mac-os-x-high-sierra-missing-ssh-folder)

Después de solucionar el problema con los permisos, creamos la carpeta /.ssh en la root (User/jlaguilar) y generamos un nuevo par de claves ssh con el comando recomendado por GitHub:

```jsx
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

Copiamos la clave pública con **pbcopy**, la añadimos a la SSH Key de GitHub en "settings" **** y, en nuestra terminal, decimos que queremos utilizar actualmente la clave privada generada:

```jsx
ssh-add ~/.ssh/id_rsa
```

**Con el comando *"ssh-add -l"*  puedo chequear todas las claves SSH que tengo disponibles, mediante *"ssh-add -D"*  puedo borrarlas todas**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1c6591ce-82b0-4ed3-9481-5aa2d5012609/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1c6591ce-82b0-4ed3-9481-5aa2d5012609/Untitled.png)

Pruebo la conexión mediante un *"git clone"* de un repo y funciona correctamente (con un error puntual pero funciona).

Si ahora vuelvo a mi perfil de GitHub y chequeo la clave, aparecerá en verde:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/93e6b39f-f7c3-469e-81fa-ed00090c3ffc/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/93e6b39f-f7c3-469e-81fa-ed00090c3ffc/Untitled.png)

Esto es que ha sido correctamente usada.

Como curiosidad, para ir pasando de un HOST a otro a través de una conexión en "tunel" por ellos, podría hacer algo similar a lo siguiente: 

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c7cf557d-100d-4b69-ae34-fed3545859ba/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c7cf557d-100d-4b69-ae34-fed3545859ba/Untitled.png)

¡Lección finalizada!

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/249e3193-26fa-4f57-a9a2-923e28dd6f37/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/249e3193-26fa-4f57-a9a2-923e28dd6f37/Untitled.png)

---

# 2. Performance Part 1

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

## Resources: Performance Tools

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

---

# 3. React + Redux + Module Bundling

*El **objetivo** de este módulo es integrar REDUX en la aplicación realizada con REACT que tiene la compañía. Así mismo se nos pide optimizar y revisar la aplicación.*

La incremental complejidad de las páginas webs y aplicaciones, ha hecho que el código JS crezca de una forma exponencial. Para posibilitar el mantenimiento a largo plazo así como la reducción de bugs y/o detección y eliminación de los mismos, nacen los **"frameworks"** y las **"librerías".**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/82f0c19d-a04c-491b-b96b-c497fee0abd3/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/82f0c19d-a04c-491b-b96b-c497fee0abd3/Untitled.png)

Debemos valorar **PROS y CONTRAS de cada framework** / librería a la hora de llevar a cabo una aplicación. Ninguna es mejor o peor y es el mercado y las necesidades de producto las que deben determinar su uso.

En el curso se pone un ejemplo de Angular como una cocina con todas las herramientas disponibles, se considera a React como una herramienta muy flexible y con gran facilidad de adaptación y a Vue una herramienta inicial perfecta (ten en cuenta que el video es de JUL 17, las cosas han cambiado mucho desde entonces)

Pensemos por un momento en la gestión de componentes por parte de React y comparemoslo con la bilogía molecular de los seres vivos.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/240cb3c9-edda-4a65-a6a5-972d097bb550/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/240cb3c9-edda-4a65-a6a5-972d097bb550/Untitled.png)

Hay que recordar también que el flujo de datos en React va siempre "aguas abajo", es decir, sólo los componentes hijos son conscientes de cambios en el componente padre, no a la inversa, como vemos en el dibujo siguiente:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c530bc33-044f-4f73-b1d2-2ad53ead5c6c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c530bc33-044f-4f73-b1d2-2ad53ead5c6c/Untitled.png)

Otra de las características más importantes de React es el manejo del **DOM virtual**. Ya no somos nosotros el "pintor" que manipula el DOM (cuanto menos manipulación directa, mejor para el rendimiento), ahora es una especie de "bot" de React el que recibe la estructura y composición del DOM mediante un objeto de JS y se encarga de introducir y realizar los cambios de la forma más óptima posible.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b0adaade-3ee6-4fa0-84ba-d025d1025a65/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b0adaade-3ee6-4fa0-84ba-d025d1025a65/Untitled.png)

## Create React App

Son 3 los vídeos que nos introducen a este tema en el curso, pero es el 3 el que nos importa, ya que es el más actualizado. 

Ya no es necesario instalar la dependencia global "create-react-app", ya que podemos inicializar la aplicación directamente mediante NPX con el comando: 

```jsx
npx create-react-app APPNAME
```

Se instalan los "package" y las librerías necesarias:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b7995238-7bce-4d8b-a180-d5af894b7765/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b7995238-7bce-4d8b-a180-d5af894b7765/Untitled.png)

### # Configurar proyecto de React con Linter y Prettier

[How to configure ESLint and Prettier in React](https://www.imaginarycloud.com/blog/how-to-configure-eslint-prettier-in-react/)

---

Utilizamos como librería de CSS 'Tachyons'. No tengo ni idea de cómo es ni reseñas de la misma. Vamos a probarla ...

[tachyons-css/tachyons](https://github.com/tachyons-css/tachyons)

### Props

Recuerda la utilizad de los props en React:

```jsx
	ReactDom.render(<Hello greeting ="{'Hello Peeedro}"/>, document.getElementById('root'));
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c36af6fe-f609-47fb-ad34-16a617f48a19/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c36af6fe-f609-47fb-ad34-16a617f48a19/Untitled.png)

Si utilizamos la notación de funciones en lugar de la de clases, podemos pasarle los **"props"** como argumentos de la función: 

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f20d424f-4a77-40f7-b44f-ade54d1396a5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f20d424f-4a77-40f7-b44f-ade54d1396a5/Untitled.png)

## Comenzamos con el ejercicio de la "robot-app"

Utilizamos como referencia para las imagenes la API siguiente, que nos permite generar imagenes aleatorias de robots:

[RoboHash](https://robohash.org/)

Usamos **'destructuring'**  para transformar las propiedades del objeto "props" en las variables que queremos, así es más "accesible":

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/98db432c-f6a5-4aa1-ad1b-8f38259be5f1/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/98db432c-f6a5-4aa1-ad1b-8f38259be5f1/Untitled.png)

Como se trata de un array de datos (la lista de robots), vamos a iterar en la misma para crear una **<Card>** por cada elemento de dicho array.

Creamos un nuevo componente (**CardList)**  e iteramos en el mismo mediante el método "map":

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/75a64576-6d71-4d7f-8c24-b431b25afcb1/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/75a64576-6d71-4d7f-8c24-b431b25afcb1/Untitled.png)

**OJO: Cuando generamos un listado de elementos para ser renderizado en el DOM, React exige (con razón), que demos una ID única a cada uno de dichos elementos para poder identificarlos en caso necesario. En este caso lo hacemos mediante key={robot.id}  que sabemos que es un identificador único.**

---

## Extra resources

Course:

[](https://indra.udemy.com/course/the-complete-junior-to-senior-web-developer-roadmap/learn/lecture/10285818?start=30#overview)
