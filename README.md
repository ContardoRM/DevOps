### Desafio DevOps
### Se compone de las siguientes actividades
* [Instalar docker](#Instalacion)
* [Cuenta Github](#Github)
* [Clonar Proyecto Base](#Clonar)
* [Correr Localmente](#Localmente)
### III.  Levantar instancia Docker con python
### IV.   Levantar instancia Docker con mongodb

## Instalacion
### Open Suse
Para instalar Docker y Docker Compose
```bash
zypper install docker docker-compose
```
Para agregar el demonio de docker al boot:
```bash
sudo systemctl enable docker
```
Iniciar el servicio Docker
```bash
sudo systemctl start docker
```
Agregar Usuario al grupo docker 
```bash
sudo usermod -G docker -a YOURUSERNAME
```
Para que tenga efectos volver a logearse a nivel de consola.


### MacOS 

Docker for Mac is best installed with [Homebrew](http://brew.sh) and [Homebrew Cask](http://caskroom.io/). For other ways to install on MacOS, see [Install Docker for Mac](https://docs.docker.com/docker-for-mac/install/) in Docker's docs.

```bash
brew cask install docker       # Install Docker
open /Applications/Docker.app  # Start Docker
```

> :bulb: Tip: Avoid _Docker Toolbox_ and _boot2docker_. These are older packages that have been ceded by _Docker for Mac_.

### Arch Linux

Docker is available in Arch Linux's repositories. Also see [Docker in ArchWiki](https://wiki.archlinux.org/index.php/Docker).

```bash
sudo pacman -Syu docker        # Install Docker
sudo systemctl start docker    # Start Docker
```

### Ubuntu

`docker.io` is available from the Ubuntu repositories (as of Xenial).

```bash
# Install Docker
sudo apt install docker.io
sudo apt install docker-compose

# Start it
sudo systemctl start docker
```

> :bulb: Tip: If the `docker.io` package isn't available for you, see [Get Docker CE for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/) for an alternative.

### Windows

Install [Windows Subsystem for Linux][wsl] and choose _Ubuntu_ as your guest OS. Install Docker as you normally would on Ubuntu (see above). After that, [see these instructions](https://github.com/Microsoft/WSL/issues/2291#issuecomment-383698720) for info on how to get it running.

> :bulb: Tip: Avoid _Docker for Windows_. While it works in most cases, you'll still face NTFS limitations without WSL (eg, lack of symlinks, which is needed for Yarn/npm to work).

[wsl]: https://docs.microsoft.com/en-us/windows/wsl/install-win10

### Other OS's

For other operating systems, see: <https://www.docker.com/community-edition#download>

## Verifying if it works

If everything works, you should have the following commands available:

```bash
$ docker info
Containers: 0
Running: 0
Paused: 0
...
```

```bash
$ docker-compose --version
docker-compose version 1.21.2, build unknown
```

## Starting Docker

If you get an error like the one below, you might need to start the Docker daemon.

```bash
$ docker info
Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
```

To start the Docker daemon, it probably needs one of these commands

```bash
open /Applications/Docker.app  # macOS
sudo systemctl start docker    # Arch, Ubuntu, CentOS
```

## Enabling on startup

For Arch Linux, Ubuntu and CentOS, this will enable auto-starting of the Docker service:

```sh
sudo systemctl enable docker
```
## Github

Lo primero que necesitas es una cuenta de usuario gratuita. Simplemente visita https://github.com, elige un nombre de usuario que no esté ya en uso, proporciona un correo y una contraseña, y pulsa el botón verde grande “Sign up for GitHub”.
Lo siguiente que verás es la página de precios para planes mejores, pero lo puedes ignorar por el momento. GitHub te enviará un correo para verificar la dirección que les has dado. Confirma la dirección ahora, es bastante importante (como veremos después).
Si pulsas en el logo del gato con patas de pulpo en la parte superior izquierda de la pantalla llegarás a tu escritorio principal. Ahora ya estás listo para comenzar a usar GitHub.
Si prefieres usar SSH, necesitas configurar una clave pública. Si aun no la tienes, mira cómo generarla en Generando tu clave pública SSH.) Abre tu panel de control de la cuenta utilizando el enlace de la parte superior derecha de la ventana:

https://git-scm.com/book/es/v2/GitHub-Creaci%C3%B3n-y-configuraci%C3%B3n-de-la-cuenta


## Clonar

```bash
$ git clone git@github.com:intelygenz/the-real-devops-challenge.git
Cloning into 'the-real-devops-challenge'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (3/3), done.
$ cd ./the-real-devops-challenge
```
## Localmente
### Run the app

If you want to run the app locally:

```bash
$ virtualenv -p python3 .venv
Running virtualenv with interpreter /usr/bin/python3
Using base prefix '/usr'
New python executable in /home/angel.barrera/work/intelygenz/the-real-devops-challenge/.venv/bin/python3
Also creating executable in /home/angel.barrera/work/intelygenz/the-real-devops-challenge/.venv/bin/python
Installing setuptools, pip, wheel...
done.
$ source .venv/bin/activate
$ pip install -r requirements.txt
Collecting Flask-PyMongo==2.2.0 (from -r requirements.txt (line 1))
  Using cached https://files.pythonhosted.org/packages/d5/c8/22ddacfe05893884dceef5b9ecfa683f947ba155bd63cd9d841aea29b7b7/Flask_PyMongo-2.2.0-py2.py3-none-any.whl
Collecting isodate==0.6.0 (from -r requirements.txt (line 2))
  Using cached https://files.pythonhosted.org/packages/9b/9f/b36f7774ff5ea8e428fdcfc4bb332c39ee5b9362ddd3d40d9516a55221b2/isodate-0.6.0-py2.py3-none-any.whl
Collecting Flask>=0.11 (from Flask-PyMongo==2.2.0->-r requirements.txt (line 1))
  Using cached https://files.pythonhosted.org/packages/7f/e7/08578774ed4536d3242b14dacb4696386634607af824ea997202cd0edb4b/Flask-1.0.2-py2.py3-none-any.whl
Collecting PyMongo>=3.0 (from Flask-PyMongo==2.2.0->-r requirements.txt (line 1))
  Using cached https://files.pythonhosted.org/packages/b1/45/5440555b901a8416196fbf2499c4678ef74de8080c007104107a8cfdda20/pymongo-3.7.2-cp36-cp36m-manylinux1_x86_64.whl
Collecting six (from isodate==0.6.0->-r requirements.txt (line 2))
  Using cached https://files.pythonhosted.org/packages/67/4b/141a581104b1f6397bfa78ac9d43d8ad29a7ca43ea90a2d863fe3056e86a/six-1.11.0-py2.py3-none-any.whl
Collecting Werkzeug>=0.14 (from Flask>=0.11->Flask-PyMongo==2.2.0->-r requirements.txt (line 1))
  Using cached https://files.pythonhosted.org/packages/20/c4/12e3e56473e52375aa29c4764e70d1b8f3efa6682bef8d0aae04fe335243/Werkzeug-0.14.1-py2.py3-none-any.whl
Collecting itsdangerous>=0.24 (from Flask>=0.11->Flask-PyMongo==2.2.0->-r requirements.txt (line 1))
  Using cached https://files.pythonhosted.org/packages/76/ae/44b03b253d6fade317f32c24d100b3b35c2239807046a4c953c7b89fa49e/itsdangerous-1.1.0-py2.py3-none-any.whl
Collecting click>=5.1 (from Flask>=0.11->Flask-PyMongo==2.2.0->-r requirements.txt (line 1))
  Using cached https://files.pythonhosted.org/packages/fa/37/45185cb5abbc30d7257104c434fe0b07e5a195a6847506c074527aa599ec/Click-7.0-py2.py3-none-any.whl
Collecting Jinja2>=2.10 (from Flask>=0.11->Flask-PyMongo==2.2.0->-r requirements.txt (line 1))
  Using cached https://files.pythonhosted.org/packages/7f/ff/ae64bacdfc95f27a016a7bed8e8686763ba4d277a78ca76f32659220a731/Jinja2-2.10-py2.py3-none-any.whl
Collecting MarkupSafe>=0.23 (from Jinja2>=2.10->Flask>=0.11->Flask-PyMongo==2.2.0->-r requirements.txt (line 1))
  Using cached https://files.pythonhosted.org/packages/08/04/f2191b50fb7f0712f03f064b71d8b4605190f2178ba02e975a87f7b89a0d/MarkupSafe-1.1.0-cp36-cp36m-manylinux1_x86_64.whl
Installing collected packages: Werkzeug, itsdangerous, click, MarkupSafe, Jinja2, Flask, PyMongo, Flask-PyMongo, six, isodate
Successfully installed Flask-1.0.2 Flask-PyMongo-2.2.0 Jinja2-2.10 MarkupSafe-1.1.0 PyMongo-3.7.2 Werkzeug-0.14.1 click-7.0 isodate-0.6.0 itsdangerous-1.1.0 six-1.11.0
$ export MONGO_URI=mongodb://YOUR_USERNAME:YOUR_PASSWORD@YOUR_MONGO_HOST:YOUR_MONGO_PORT/YOUR_MONGO_DB_NAME
$ python app.py
 * Serving Flask app "app" (lazy loading)
 * Environment: production
   WARNING: Do not use the development server in a production environment.
   Use a production WSGI server instead.
 * Debug mode: off
 * Running on http://0.0.0.0:8080/ (Press CTRL+C to quit)
```

You will be able to access the api locally in the `8080` port.

#### The API

- `/api/v1/restaurant`: Returns a list containing all the restaurants.
- `/api/v1/restaurant/{id}`: Returns a list with a single restaurant that match the `id` path parameter.

Examples:

```bash
curl localhost:8080/api/v1/restaurant | jq
.
.
.
 {
    "URL": "http://www.just-eat.co.uk/restaurants-bayleafn9/menu",
    "_id": "55f14313c7447c3da7052249",
    "address": "61 Bounces Road",
    "address line 2": "Edmonton",
    "name": "Bayleaf",
    "outcode": "N9",
    "postcode": "8JE",
    "rating": 5,
    "type_of_food": "Curry"
  },
  {
    "URL": "http://www.just-eat.co.uk/restaurants-bayleafn9/menu",
    "_id": "55f14313c7447c3da705224a",
    "address": "61 Bounces Road",
    "address line 2": "Edmonton",
    "name": "Bayleaf",
    "outcode": "N9",
    "postcode": "8JE",
    "rating": 5,
    "type_of_food": "Curry"
  },
  {
    "URL": "http://www.just-eat.co.uk/restaurants-bayleaf-de75/menu",
    "_id": "55f14313c7447c3da705224b",
    "address": "39 Market Street",
    "address line 2": "Heanor",
    "name": "Bayleaf",
    "outcode": "DE75",
    "postcode": "7NR",
    "rating": 5,
    "type_of_food": "Curry"
  },
  .
  .
  .
```

This is an example output, to get the full output, test it locally.

```bash
curl localhost:8080/api/v1/restaurant/55f14313c7447c3da705224b | jq
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   241  100   241    0     0    317      0 --:--:-- --:--:-- --:--:--   317
[
  {
    "URL": "http://www.just-eat.co.uk/restaurants-bayleaf-de75/menu",
    "_id": "55f14313c7447c3da705224b",
    "address": "39 Market Street",
    "address line 2": "Heanor",
    "name": "Bayleaf",
    "outcode": "DE75",
    "postcode": "7NR",
    "rating": 5,
    "type_of_food": "Curry"
  }
]
```
