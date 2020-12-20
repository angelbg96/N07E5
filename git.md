# Comandos GIT

- `git config --global user.name "nombreUsuario"`
    * Configurar el nombre del usuario de forma global
- `git config --global user.mail "ejemplo@email.com"`
    * Configurar el correo del usuario de forma global
- `git init`
    * Inicializar un nuevo repositorio a nivel de la carpeta donde se ejecuta el comando,
    * Se crea una carpeta oculta _.git_ en el nuevo espacio de trabajo
- `git comando --help` : Consulta el modo de uso de un comando, información detallada
- `git cat archivo.ext`
    * Visualizar contenido de archivo en la bash
- `git grep "palabra"` : Busca concidencias con la palabra escrita en los archivos del repositorio
    * `-n` : mostrar la linea en la cual la palabra aparece en el archivo
- `git add`
    * Agrega archivos al sistema de control de versiones
    * `git add` `archivo.ext` || `nombre/`
        + Agrega un fichero específico o todo el contenido de una carpeta
    * `git add .`
        + Agrega todos los archivos respecto a la ubicación donde se ejecuta el comando, al área de preparación (staged)
    * `git commit -a .`
        + Agregar todos los archivos nuevos o modificados al siguiente commit
    * `git commit -am "mensaje corto"`
        + Agrega todos los archivos nuevos o modificados y escribe un mensaje corto en el commit
- `git checkout archivo.ext` || `git checkout -- archivo.ext` || `git restore archivo.ext`
    * Deshace los últimos cambios del archivo respecto al último commit realizado
    * `git checkout -f`
        + Borra cambios en todos los ficheros
- `git restore --staged archivo.ext` || `git reset HEAD archivo.ext`
    * Quitar archivos del área de preparación
- `git rm archivo.ext`
    * Borrar archivo del repositorio
- `git rm --cached archivo.ext`
    * Borrar un archivo del seguimiento del repositorio una vez que ya se le haya hecho un commit
- `git rm -r --cached nombreDirectorio`
    * Borrar una carpeta y su contenido del repositorio una vez que ya se le haya realziado un commit
- `git diff archivo.ext`
    * Diferencia de cambios actuales en archivo vs último commit
    * `git diff --stat archivo.ext`
        + Estadística de cambios realizados en archivo
    * `git diff master nombreRama`
        + Muestra la diferencia de cambios entre ambas ramas
    * `git diff hashCommit1 hashCommit2`
        + Muestra la diferencia de cambios realizados entre ambos commits
- `git checkout hashCommit`
    * Regresar en el tiempo a X commit
    * _hashCommit_ mínimo 7 dígitos
    * `git checkout HEAD@X`
        + Visualiza el estado del proyecto X commits atrás
    * `git checkout master`
        + Regresa el apuntador cabecera (_HEAD_) a la actualidad en la rama master
- `git log` `[opciones]`
    * Mostrar el historial de commits
    * `--oneline` : Log de commits en una línea
    * `--all--graph` : Mostrar historial incluyendo las ramas donde fueron hechos los commits
    * `--decorate` : Agrega colores al log para resaltar información importante
    * `--pretty="format:"[texto y comodines]"`
        + Personalizar los campos que se desean mostrar en el log con un texto personalizado
        + Los campos de cada commit se escapan con _comodines_ como:
            - `%n` : nombre de usuario
            - `%h` : hashCommit
    * `-p rutaArchiv` : Muestra el histórico de cambios realizados en el archivo
    * `-S "palabra a buscar"` : Buscar los commits en los cuales sale una palabra
- `git shortlog` : Ver cuantos commits a hecho los miembros del equipo
    * `-sn` : Muestra cuantos commit han hecho cada miembro
    * `-sn --all` : Todos los commits (también los borrados)
    * `-sn --all --no-merges` : Muestra cuantos commit han hecho cada miembro quitando los merges
- `git blame archivo` : Visualizar los cambios realizados por los miebros del equipo en un determinado archivo
    * `-c` : Muestra quien ha hecho cambios en dicho archivo identado
    * `-Llin_inicial,lin_final -c` : Muestra quien escribio el codigo desde _lin\_inicial_ a _lin\_final_ con un formato legible
-  `git show hashCommit:rutaArchivo`
    * Muestra el código fuente del archivo en el commit indicado
- `git stash`
    * Manda los cambios actuales del sistema de control de versiones a este espacio
    * Util cuando no se actualizó una rama remota y ya se hicieron cambios locales en el proyecto
    * `-u` : Crea un stash con todos los archivos. (Añadiendo los creados Untracked)
    * `save "mensaje"` : Crea un stash con el mensaje especificado
    * `list` : Permite visualizar todos los stash existentes
    * `clear` : Elimina todos los stash existentes
    * `drop` : Elimina el stash más reciente, tiene num_stash=0
    * `drop stash@{num_stash}` : Elimina un stash específico
    * `apply` : Aplica el stash más reciente (num_stash=0)
    * `apply stash@{num_stash}` : Aplica los cambios de un stash específico
    * `pop` : Aplica el stash más reciente al workspace y lo elimina
    * `pop stash@{num_stash}` : Aplica los cambios de un stash específico y elimina lo stash
    * `branch nombre_de_rama` : Crea una rama y aplica el stash mas reciente
    * `branch nombre_de_rama stash@{num_stash}` : Crea una rama y aplica el stash especificado
- `git gc`
    * Ejecuta el recoletor de basura
- `git clean` : Actúa en archivos sin seguimiento, este tipo de archivos son aquellos que se encuentran en el directorio de trabajo, pero que aún no se han añadido al índice de seguimiento de repositorio
    * `--dry-run` : Lista los archivos que serán borrados
    * `-f` : Borrar todos los archivos listados (que no son carpetas)
    * `-d` : Para considerar en el borrado directorios añadidos

___
## Ramas
- `git checkout -b nombreRama`
    * Crea una nueva rama y se posiciona en ella
- `git branch`
    * Lista las ramas existentes
- `git checkout` || `switch nombreRama`
    * Posicionarse en la rama especificada
- `git merge nombreRama`
    * Fusiona commits de la rama donde se encuentra posicionado con la rama indicada
- `git branch -d nombreRama`
    * Borra la ramma, comprueba que los commits de la rama estén integrados en la rama master
- `git branch -D nombreRama`
    * Elimina la rama independientemente de que los cambios realizados en ella estén en master
    * No se debe estar posicionado en la rama a eliminar
- `git merge --abort`
    * Cancelar la fusión de commits debido a algún conflicto
    * Cuando se terminen de resolver los conflictos de forma manual, realizar un `git add` y `commit` del archivo que presentó conflictos
- `git reflog`
    * Registro de cambios en las ramas
    * Muestra _hashCommit_ y la descripción de dicho cambio

___
## Remoto
- `git clone URLrepo`
    * Clonar repositorio almacenado en la nube
- `git remote -v`
    * Listar ramas remotas
- `git remote add upstream URLrepo`
    * Crea rama _upstream_ para monitorear los cambios del repositorio en la nubre
- `git pull upstream master`
    * Descargar cambios del repositorio remoto
- `git push upstream master`
    * Subir cambios al repositorio remoto
- `git pull ramaRemota ramaLocal`
    * Sincroniza los commits de la rama local con la remota
    * Ej: `git pull origin master`
- git push ramaRemota ramaLocal
    * Envía cambios de la rama local a la remota
    * Ej: `git push origin master`
- `git push origin nombreRama`
    * Crea una rama de enlace remoto a partir de una rama remota
- `git push --delete origin nombreRama`
    * Borra la rama remota

___
## Reescribiendo historial
- `git commit --amend`
    * Enmendar, deshace el último commit para agregar o quitar archivos, o bien para editar el mensaje del commit
    *  Antes de ejecutar el _amend_...
        + Si se trata de un archivo que no debe ir en ese commit, reestablecer el archivo y ejecutar el ammend. Es mejor utilizar un `git reset` si este es el caso
        + Si se olvidó realizar un cambio o se encontró alguna errata, editar el archivo, hacer un `git add `y luego ejecutar el _ammend_
- `git reset`
    * Deshacer cambios debido a commits erróneos, dichos cambios quedarán fuera del historial (elimina los commits posteriores)
    * `git reset hashCommit`
        + Deshace los cambios para tener el proyecto en el estado en que se hizo el commit indicado
    * `git reset HEAD^`
        + Apuntar un commit atrás en el pasado
        + Cada `^` significa el número de commits a retroceder
    * `git reset HEAD~X`
        + Retroceder _X_ commits
    * `reset` || `reset --soft`
        + Deshace cambios y los deja en el workspace
    * `reset --mixed`
        + Deshace cambios, los deja en workspace pero no considera los archivos agregados o eliminados
    * `reset --hard`
        + No deja ningún cambio en workspace, lleva el proyecto al estado en el que se encontraba en ese momento
- `git reverse hashCommit` || `HEAD~X`
    * Revierte los cambios hasta el commit indicado, una vez que se restaura crea un commit indicando dicho cambio. No afecta el historial.
- `git rebase -i HEAD~X`
    * Actualizar una rama respecto a _master_ (merge)
    * Permite reescribir historial de commits (mover, eliminar, cambiar mensajes, etc)
- `git rebase --abort`
    * Salir del proceso

___
## Cambiando el usuario que realiza commits
- Ir a las credenciales de windows, buscar las credenciales de Git y/o GitHub y eliminarlas, o en su caso, modificarlas
- En el bash de git :
    * `git config --global --list`
        + Para listar las configuraciones generales de Git
    * `git config --global --unset-all user.name`
    * `git config --global --unset-all user.email`
        + Eliminar el usuario actual (username y correo)
    * `git config --global --add user.name nuevoUsuario`
    * `git config --global --add user.email ejemplo@correo.com`
        + Configurar los nuevos datos (username y correo)
