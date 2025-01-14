## Developers

Este proyecto no sería posible sin la colaboración de otros developers que han donado su tiempo para crear esta aplicación. Si encuentras un error por favor crea un [issue](https://github.com/Code4PuertoRico/horas/issues) y si puedes arreglarlo te invitamos a hacer y someter un pull request.

Tenemos un [chat room - #horas-project](https://startupsofpr.slack.com/messages/C4HAXGZL5) para facilitar la comunicación y coordinación del equipo. Si necesitas una cuenta puedes [crearla aqui](https://bit.ly/sopr-slack).

* [Creación de Cuenta para Slack de SoPR](https://bit.ly/sopr-slack)
* [Chat Room - #horas-project](https://startupsofpr.slack.com/messages/C4HAXGZL5)

Si necesitas ideas de como ayudar puede ver la lista de tareas pendientes.

[Github issues](https://github.com/Code4PuertoRico/horas/issues)


### Para correr el proyecto

Hay dos opciones para correr el proyecto, la primera usando Docker y la segunda instalandolo en tu ambiente local.

#### Opción 1: Docker

**Instalación**

**Linux**

Puedes encontrar instrucciones de como instalar Docker para diferentes distribuciones de Linux [aqui](https://docs.docker.com/engine/installation/#docker-editions).

Distribuciones populares:

- [Ubuntu](https://docs.docker.com/engine/installation/linux/ubuntu/)
- [Debian](https://docs.docker.com/engine/installation/linux/debian/)
- [Fedora](https://docs.docker.com/engine/installation/linux/fedora/)

**Mac OS**

La mejor manera de utilizar Docker en Mac OS o Windows PC es utilizando [Docker Desktop](https://www.docker.com/products/docker-desktop).

** Cómo crear imágenes de `Horas` con Docker **

```bash
# Clonear repositorio
$ git clone https://github.com/Code4PuertoRico/horas.git


# Copiar archivo de variables de ambiente
$ cp .env.example .env

# Instalar dependencias del frontend
$ cd horas/static
$ npm install

# Crear la imagen de Docker y correrla en un contenedor separado del terminal
$ cd ..
$ docker-compose up --detach
```

El archivo docker-compose.yml contiene toda la configuración de los servicios de Docker necesarios tener una instancia de Horas corriendo.

Abre tu browser en [http://localhost:8000/](http://localhost:8000/). Para accesar la sección de administración ve a [http://localhost:8000/admin/](http://localhost:8000/admin/), y usa el username **admin** y el password **abc123**.

#### Opción 2: Local

**Requisitos**

- [Python 3.7](https://www.python.org/)
- [Pipenv](https://docs.pipenv.org/en/latest/)
- [Node.js 14](https://nodejs.org) (incluye npm)

```bash
# Clonear repositorio
$ git clone https://github.com/Code4PuertoRico/horas.git

# Instalar dependencias para el build de JS / CSS
$ cd horas/static
$ npm install

# Copiar archivo de variables de ambiente
$ cd ..
$ cp .env.example .env

# Instalar dependencias python
$ pipenv install --dev

# Migración y data inicial
$ pipenv run python manage.py migrate
$ pipenv run python manage.py loaddata apps/profiles/fixtures/admin.json

# Correr servidor de django
$ pipenv run python manage.py runserver
```

Abre tu browser en [http://localhost:8000/](http://localhost:8000/). Para accesar la sección de administración ve a [http://localhost:8000/admin/](http://localhost:8000/admin/), y usa el username **admin** y el password **abc123**.

##### Para los usuarios de Mac OSX
Durante la instalacion de los requerimientos con pip:

```bash
$ pipenv install --dev
```
Es posible que se encuentren con este error:

```
src/_pylibmcmodule.h:42:10: fatal error: 'libmemcached/memcached.h' file not found
    #include <libmemcached/memcached.h>
             ^
    1 error generated.
```

Esto se puede dar cuando __libmemcached__ no esta instalada en su sistema. La solucion es instalar __libmemcached__ de una de las siguientes maneras:

__Homebrew__

```bash
$ brew install libmemcached
```

Una vez hecho esto pueden volver al paso ```$ pipenv install --dev``` y continuar con las instrucciones.

#### Para correr tests
```
$ pipenv run python manage.py test --configuration=Testing --verbosity=3 --noinput
```
## Diseñadores

Tenemos un branch dedicado para compartir y colaborar sobre el diseño de la plataforma. Mantendremos el diseño más reciente en ese branch.

[Design](https://github.com/Code4PuertoRico/horas/tree/design) - Branch dedicado al diseño de este proyecto.
