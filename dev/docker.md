# Docker

## Fundamentos Teoricos
- *Contenedor*: Forma de empaquetar aplicaciones con sus dependencias y archivos de configuración manteniendo siempre el mismo entorno en la misma versión, por lo que los hacen portables.
    - Existen repositorios/Registro de contenedores privados y públicos, el repositorio público más popular es DockerHub.
    - Se crea a partir de una imagen, que es el empaquetado que contiene dependencias, código, variables de entorno. Por lo que un contenedor son capas de varias imágenes, donde su capa base/fundamental es una imagen del SO Linux (comunmente Alpine) hasta llegar a la imagen del software de aplicación. Cada imagen con su versión tiene su propio hash ID.
    - Un contenedor está totalmente aislado del equipo donde se ejecuta, por lo que si se requiere que obtenga información del sistema o interactuar con él, se deben crear volumenes y mapear los puertos del equipo hacia el contenedor, respectivamente.
- La única dependencia que tiene un contenedor es el runtime de Docker, y este utiliza directamente el Kernel del SO para ejecutarse
- Virtualziación. Se basa en tres capas: Hardware donde se ejecuta, Kernel del sistema operativo, aplicaicones que se ejecutan. Tipos de virtualziación:
    - Para virtualziación. Toma como base los conceptos de host y host guest. Donde el host es el SO donde se va a ejecutar la virtualización y los clientes son los SO que se van a virtualizar. El SO anfitrión trata de otorgar la mayor cantidad de acceso de hardare a los clientes.
    - Virtualziación parcial. Algunos componentes de hardware se virtualizan para el SO cliente.
    - Virtualziación completa. Se virtualiza todos los componentes (hadware) que utiliza el SO cliente.
- Tipos de Volumenes
    - *Anonimo*. Solo se indica la ruta del contenedor a persistir, Docker determinar donde va a persistir los datos
    - *De Anfitrion o Host_. Se especifica el directorio a montar y donde se monta
    - *Nombrado*. Parecido al anonimo pero se puede referenciar en la configuración de los contenedores que se decidan que lo utilicen

## Manejo de Docker
- Docker Desktop es una VM que se ejecuta sobre linux, y es la que ejecuta los contenedores, contiene varias herramientas como Dcoker Compose, CLI (Command Line Interface)
- En DockerHub se almacenan una gran cantidad de imagenes oficiales de diferentes productos de software, además de que estas imagenes muestran el historial de versiones y sobre que imagen base de SO fueron construidas.
- Al descargar una imagen, y si no se indica su versión, se va a descargar la última versión publicada, y se identificará con la etiqueta *latest*. Si las capas inferiores de la imagen a descargar ya existen en el sistema, no se vuelven a descargar
    - `docker pull nombreImagen:versionTag` : Descarga la versión de la imagen señalada
    - `docker images` : Lista las imagenes descargadas
    - `docker image rm nombreImagen:versionTag` : Elimina la versión de la imagen indicada
- Para crear un contenedor, se debe tener la imagen descargada de lo que se desea crear. Para crear algunos contenedores se requiere agregar parámetros de configuración, esto se puede consultar en DockerHub de acuerdo a la imagen que se va a crear.
    - `docker create --name nombreContenedor nombreImagen` | `docker container create --name nombreContenedor nombreImagen` : Crea un contenedor a partir de una imagen y le asigna el nombre al contenedor
        - `--publish` | `-p puertoHost:puertoContenedor` : Son opciones equivalentes, mapea los puertos de la PC al contenedor
        - `--enviroment` | `-e NOMBRE_VAENV=valor` : Configura la variable de entorno que requiere el contenedor
        - `--volume` | `-v directorioHost:directorioContenedor:permisos` : Especifica un directorio o archivo para persistir la información que se maneja en el contenedor. Se pueden delimitar los permisos a los volumenes
        - `--network nombreRed` : Se agrega el contenedor a la red de docker especificada. Para versiones anteriores de docker, se recomienda especificar `--network-alias nombreAlias` para nombrar el dominio del contenedor
        - `--restart` : Indica si el contenedor se reinicia con el runtime de Docker `always` | `unless-stopped`
    - `docker ps` : Muestra los datos de los contenedores que están en ejecución: De forma tabular se muestra el ID del contenedor, la imagen base del contenedor, el comando mediante el cual se ejecuta el contenedor, estatus de ejecución delcontenedor, puertos a la escucha de la computadora y del contenedor, y nombre asignado del contenedor
    - `docker ps -a` : Muestra todos los contenedores, considerando los que no están en ejecución
    - `docker start contenedorID` | `nombreContenedor` : Ejecuta el contenedor indicado
    - `docker stop contenedorID` | `nombreContenedor` : Detiene los procesos del contenedor indicado
    - `docker rm contenedorID` | `nombreContenedor` : Elimina el contenedor indicado
    - `docker logs contenedorID` | `nombreContenedor` : Muestra los logs creados del contenedor
        - `--follow` | `-f` : Se mantiene a la escucha de la escritura de nuevos logs
    - `docker exec -it contenedorID` | `nombreContenedor comando` : Ejecuta el comando indicado dentro del contenedor en ejecución
        - `-i` : La terminal será interactiva
        - `-t` : Emula una terminal
        - Muy util para acceder al SO del contenedor, por ejemplo con `bash` o `sh`
    - `docker run nombreImagen` : Comando de atajo que ejecuta e infire las acciones de los comandos `pull`, `create`, `start` para crear (utiliza las opciones del comando `create`) y ejecutar el contenedor de la imagen especificada en primer plano
        - `--detach` | `-d` : Manda la ejecución del contenedor al segundo plano
- Para que un contenedor se comunique con otro contenedor, se debe crear una Red. Para acceder a los contenedores, estos van a tener como nombre de dominio el mismo nombre del contenedor creado
    - `docker network ls` : Muestra las netwkors creadas (por runtime de Docker y usuario)
    - `docker network create nombreRed` : Crea una red con el nombre especificado
    - `docker network rm nombreRed` : Elimina la red indicada

## Creando nuevas imagenes
- Se crean a partir del archivo *Dockerfile*, debe indicarse la imagen base
- `FROM nombreImagen:version` : Imagen base del contenedor
- `RUN comando` : Ejecuta comandos dentro del contenedor, pensado más que nada para preparar la instalación del mismo (crear estructuras de directorios, instalar dependencias, etc)
- `WORKDIR rutaContenedor` : Indica cual es el directorio de trabajo donde se ejecuta la aplicación
- `COPY rutaHost rutaContenedor` : Copia archivos de la computadora Host al contenedor
- `EXPOSE numeroPuerto` : Puerto que se expone
- `CMD ["comandoEjecucion", "parametros"]` : Comando para ejecutar el contenedor
- `ENTRYPOINT ["comandoEjecucion"]` : Comando que ejecuta el contenedor, pero este espera parametros para inciar el contenedor
- `docker build -t nombreNvaImagen:Tag rutaDockerfile` : Crea una imagen a partir del dockerfile indicado

## Docker Compose
- Herramienta que viene inteegrada en la instalación de docker, sirve para agilizar la creación de contenedores
- Su archivo de configuración es `docker-compose.yml`
    - `version: "3.9"` : Version del docker compose a utilizar
    - `volumes:` : Se definen todos los volumenes que se desean crear y son necesarios para la ejecución de los contenedores, estos deben tener una tabulación para que se identifiquen como elementos hijo de esta etiqueta `nombre-volumen:`
    - `services:` : Se deben agregar los nombres de los contenedores que se van a crear, estos deben tener una tabulación para que se identifiquen como elementos hijo de esta etiqueta
    - A cada contenedor se le debe indicar como construirse, por lo que las siguientes etiquetas deben estar a su vez identadas para que se reconozcan como elementos hijo
        - `build: rutadockerFile` : Se indica como se construye el contenedor. Esta opción puede tener otros elementos hijo:
            - `context: rutadockerFile` : Ruta donde se encuentra el archivo dockerfie
            - `dockerfile: dockerfile.nombreEspecifico` : Archivo dockerfile que se utilizará explicitamente para construir el contenedor
        - `imagen: nombreImagen:Tag` : Se indca la imagen base del contenedor
        - `ports:` : Mediante una tabulación y un guión medio (Representa un listado), se indican los puertos exponer y mapear con el contenedor `- "puertoHost:puertoContenedor"`
        - `links:` : Listado de nombres de contenedores que se van a comunicar con el contenedor en configuración `- miContenedor1`
        - `enviroment:` : Listado de variables de entorno que utiliza el contenedor `- MI_VAENV=valor` (También acepta sintaxis `MI_VAENV: valor`)
        - `volumes:` : Listado de volumenes que utiliza el contenedor `- nombre-volumen:rutaContenedor` o `rutaHost:rutaContenedor`
- `docker compose up` | `docker-compose up`: Crea y ejecuta en primer plano los contenedores indicados en el archivo de configuración. Muestra todos los logs de todos los contenedores.
    - `-d` : Manda la ejecución de los contenedores al segundo plano
    - `-f archivoPersonalizado` : Contrusye los contenedores a partir del archivo especificado, por lo que no se utiliza el archivo por default
- `docker compose down` : Elimina los contenedores y redes configuradas en el archivo de configuración

## Punlicar imagen en Repositorio
- Se debe tener una cuenta en *DockerHub*
- `docker login` : Login en PC con cuenta de DockerHub
- `docker targ imagenID usuarioDockerHub/nombreImagen:tag` : Agregar una etiqueta a una imagen local, esto es necesario para publicar una imagen en el repositorio, se indica el nombre de usuario de dockerhub
- `docker push usuarioDockerHub/nombreImagen:tag` : Comando para publicar imagen en repositorio

## Comandos adicionales de Docker
- `docker inspect conetenedorID` : Revisar parametros e información de como se configuró y construyó el contenedor
- `docker cp contenedor:ruta/recurso ruta/destino` : Copiar archivos del contenedor al host
- `docker save imagenID > ruta/archivo.tar` | `docker save -o ruta/archivo.tar nombreImagen` : Exporta la imagen a un archivo comprimido
- `docker load archivo.tar` : Importa una imagen desde un archivo comprimido
- `docker top contenedorID` : Revisar los procesos que está ejecutando el contenedor
- `docker events` : Revisar los eventos que ocurren en docker, p.ej. cuando se detiene o ejecuta un contenedor
- `docker diff contenedorID` : Visualizar los cambios que ocurrieron desde que se incia un contenedor hasta el momento que se ejecuta el comando
- `docker history imagenID` : Visualizar los pasos para construir una imagen
- `docker pause contenedorID` | `docker unpause contenedorID` : Pausa/reinicia ejecución del contenedor indicado
- `docker update flag=valor contenedorID` : Cambia la configuración de la bandera con el valor señalado
- `docker wait contenedorID` : Espera a que el contenedor termine y revisa el código de error con el que finaliza

