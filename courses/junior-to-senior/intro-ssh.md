# Intro to SSH
---

[***Notion***](https://www.notion.so/jlaguilargomezdevelop/Intro-to-SSH-99e8e424751748a5a8e9d89975826b0b)


___
***El objetivo de esta lección es establecer una conexión SSH a nuestro perfil de GitHub***

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

**Extra:**

[https://www.ssh.com/ssh/putty/windows/](https://www.ssh.com/ssh/putty/windows/)

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

Opcional: se ofrece un crédito de $100 para registrar un servidor en Digital Ocean mediante este enlace: [https://m.do.co/c/ef8add492554](https://m.do.co/c/ef8add492554)

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

[Copy of Quick Note: SSH Into A Server](https://www.notion.so/Copy-of-Quick-Note-SSH-Into-A-Server-36b0d8f60b3c42789adc74e88315f3a0)

[Copy of Resources: SSH Into A Server](https://www.notion.so/Copy-of-Resources-SSH-Into-A-Server-0a6d999f4e73422cab9f8079ff55e3d0)

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
