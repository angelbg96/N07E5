# Comandos GIT

- `git config --global user.name "nombreUsuario"`
    * Configurar el nombre del usuario de forma global
- `git config --global user.mail "ejemplo@email.com"`
    * Configurar el correo del usuario de forma global
- `git init`
    * Inicializar un nuevo repositorio a nivel de la carpeta donde se ejecuta el comando,
    * Se crea una carpeta oculta *.git* en el nuevo espacio de trabajo
- `git cat archivo.ext`
    * Visualizar contenido de archivo en la bash
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
- `git checkout archivo.ext` || `git checkout -- archivo.ext`
    * Deshace los últimos cambios del archivo respecto al último commit realizado
    * `git checkout -f`
        + Borra cambios en todos los ficheros
- `git restore --staged archivo.ext` || `git reset HEAD archivo.ext`
    * Quitar archivos del área de preparación
- `git rm archivo.ext`
    * Borrar archivo del repositorio
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
- `git log -p rutaArchiv`
    * Muestra el histórico de cambios realizados en el archivo
-  `git show hashCommit:rutaArchivo`
    * Muestra el código fuente del archivo en el commit indicado
- `git stash`
    * Manda los cambios actuales del sistema de control de versiones a este espacio
    * Util cuando no se actualizó una rama remota y ya se hicieron cambios locales en el proyecto
- `git stash pop`
    * Regresa los cambios al workspace
- `git gc`
    * Ejecuta el recoletor de basura

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

## Reescribiendo historial
- `git commit --amend`
    * Enmendar, deshace el último commit para agregar o quitar archivos, o bien para editar el mensaje del commit
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
    * Permite reescribir historial de commits (mover, eliminarm cambiar mensajes, etc)
- `git rebase --abort`
    * Salir del proceso