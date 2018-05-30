## Developers

This project would not be possible without other developers contibuting their time. If you find an error please create an [issue](https://github.com/SoPR/horas/issues) and if you can fix it we invite you to create and submit a pull request :smile".

We have a [chat room - #horas-project](https://startupsofpr.slack.com/messages/C4HAXGZL5) to help the team communicate and coordinate. If you need an account you can [create one here](https://bit.ly/sopr-slack).

* [SoPR Slack account creation](https://bit.ly/sopr-slack)
* [Chat Room - #horas-project](https://startupsofpr.slack.com/messages/C4HAXGZL5)

Please take a look at our [issue list](https://github.com/SoPR/horas/issues) for ideas on what to work on or add your own:

### Running the project

There's a couple of ways to run this project locally:

#### Option 1: Vagrant
You need to have installed [VirtualBox](https://www.virtualbox.org/) and [Vagrant](http://www.vagrantup.com/). Both are simple to install, free, and available in multiple platforms. This is probably the easiest option for new collaborators.

#### Steps

1. Clone the [SoPR/horas](https://github.com/SoPR/horas) repo and create the Vagrant instance:

```bash
$ git clone https://github.com/SoPR/horas.git
$ cd horas
$ vagrant up
```

2. Connect to the Vagrant instance and run the project:

```bash
$ vagrant ssh
$ cd horas
$ runhoras
```

Now you can point your browser to [http://localhost:8000/](http://localhost:8000/). To access the admin panel go to [http://localhost:8000/admin/](http://localhost:8000/admin/), and use the following credentials: 

* username: **admin**
* password: **abc123**


#### Option 2: Docker

**Installation**

**Linux**

You can find instructions on how to install Docker for a number of Linux distributions [here](https://docs.docker.com/engine/installation/#docker-editions).

Popular distributions:

- [Ubuntu](https://docs.docker.com/engine/installation/linux/ubuntu/)
- [Debian](https://docs.docker.com/engine/installation/linux/debian/)
- [Fedora](https://docs.docker.com/engine/installation/linux/fedora/)

**Mac OS**

The best/easiest way to have Docker on your Mac is using [Docker for Mac](https://www.docker.com/docker-mac).

**Windows**

The best/easiest way to have Docker on your Windows PC is using [Docker for Windows](https://www.docker.com/docker-windows).

** Creating Horas Docker images **

```bash
# Clone the repo
$ git clone https://github.com/SoPR/horas.git

# Install build dependencies
$ cd horas/static
$ npm install  # 'yarn' si lo tienes instalado

# Create the Docker image.
$ cd ..
$ docker-compose build

# Once the image is created you can create the container
$ docker-compose up -d

# When the containers are created and running you can then run Django manage commands
$ docker-compose exec web python manage.py collectstatic

# Django migrate and initial data load
$ python manage.py migrate
$ python manage.py loaddata apps/profiles/fixtures/admin.json
```

The docker-compose.yml file contains all the configuration needed to have a running instance of Horas.

Now you can point your browser to [http://localhost:8000/](http://localhost:8000/). To access the admin panel go to [http://localhost:8000/admin/](http://localhost:8000/admin/), and use the following credentials: 

* username: **admin**
* password: **abc123**

#### Opción 3: Local

**Requisitos**

- [Python 2.7](https://www.python.org/)
- [Node.js LTS](https://nodejs.org)
- [Yarn](https://yarnpkg.com) (opcional)

```bash
# Clone the rep
$ git clone https://github.com/SoPR/horas.git

# Install build dependencies
$ cd horas/static
$ npm install  # 'yarn' si lo tienes instalado

# Make a copy of the .env.example file
$ cd ..
$ cp .env.example .env

# Install Python dependencies
$ pip install -r requirements.txt

# Django migrate and initial data load
$ python manage.py migrate
$ python manage.py loaddata apps/profiles/fixtures/admin.json

# Run the Djang server with webpack
$ python manage.py webpackserver
```

Now you can point your browser to [http://localhost:8000/](http://localhost:8000/). To access the admin panel go to [http://localhost:8000/admin/](http://localhost:8000/admin/), and use the following credentials: 

* username: **admin**
* password: **abc123**

##### Mac OS users
When installing the Python dependencies with Pip:

```bash
$ pip install -r requirements.txt
```

It's possible to get the following error:

```
src/_pylibmcmodule.h:42:10: fatal error: 'libmemcached/memcached.h' file not found
    #include <libmemcached/memcached.h>
             ^
    1 error generated.
```

This can happen when __libmemcached__ is not installed on your system. To solve this please install __libmemcached__:

__Homebrew__

```bash
$ brew install libmemcached
```

__Ports__

```bash
$ sudo port install libmemcached
```

Once installed you can go to the following step to continue: `$ pip install -r requirements.txt`.

#### Running the Tests
```
$ python manage.py test --configuration=Testing --verbosity=3 --noinput
```

## Designers

We have a dedicated branch for you! We will maintain the most recent design [here](https://github.com/SoPR/horas/tree/design).