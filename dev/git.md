# Comandos GIT

- `git config --global user.name "nombreUsuario"`
    - Configurar el nombre del usuario de forma global
- `git config --global user.mail "ejemplo@email.com"`
    - Configurar el correo del usuario de forma global
- `git init`
    - Inicializar un nuevo repositorio a nivel de la carpeta donde se ejecuta el comando,
    - Se crea una carpeta oculta *.git* en el nuevo espacio de trabajo
    - `--bare ruta/directorio.git` : Crea un repositorio de Git vacío, pero omite el directorio de trabajo, lo que imposibilita la edición de archivos y la confirmación de cambios en ese repositorio. Útil para aplicar `git push` y `git pull`, pero nunca realizar confirmaciones directamente en él.
    - `--template ruta/directorio` : Inicializa un nuevo repositorio de Git y copia los archivos de la plantilla al repositorio. Se puede configurar una plantilla para que tenga los directorios y archivos predeterminados que se copiarán en el subdirectorio de *.git* del nuevo repositorio. Las plantillas de Git suelen ubicarse en /_usr/share/git-core/templates_, pero pueden encontrarse en una ruta diferente.
    - `--separate-git-dir=ruta/directorio` : Crea un archivo de texto que contiene la ruta al direcotrio *.git* .
        + Resulta muy útil:
        + Si se quiere almacenar el directorio *.git* en una ubicación o unidad independiente de los archivos de trabajo del proyecto.
        + Para mantener los archivos ocultos de la configuración del sistema (.bashrc, .vimrc, etc.) en el directorio principal, mientras que la carpeta de .git se conserva en otro lugar.
        + Cuando el historial de Git ocupa mucho espacio en el disco y necesitas moverlo a otro sitio de una unidad independiente de gran capacidad.
        + Cuando se quiere tener un proyecto de Git en un directorio de acceso público como *www:root*.
        + Se puede llamar a `git init --separate-git-dir` en un repositorio que ya exista y el directorio de *.git* se moverá a la ruta de especificada.
    - `--SHARED[=(FALSE|TRUE|UMASK|GROUP|ALL|WORLD|EVERYBODY|0XXX)]` : Define los permisos de acceso del nuevo repositorio. Esto especifica qué usuarios y grupos de los que utilizan permisos de nivel de Unix pueden realizar las acciones de envío e incorporación de cambios en el repositorio.
- `git comando --help`
    - Consulta el modo de uso de un comando, información detallada
- `git cat archivo.ext`
    - Visualizar contenido de archivo en la bash
- `git grep "palabra"`
    - Busca concidencias con la palabra escrita en los archivos del repositorio
    - `-n` : mostrar la linea en la cual la palabra aparece en el archivo
- `git add`
    - Agrega archivos al sistema de control de versiones
    - `git add` `archivo.ext` || `nombre/`
        + Agrega un fichero específico o todo el contenido de una carpeta
    - `git add .`
        + Agrega todos los archivos respecto a la ubicación donde se ejecuta el comando, al área de preparación (staged)
    - `git commit -a .`
        + Agregar todos los archivos nuevos o modificados al siguiente commit
    - `git commit -am "mensaje corto"`
        + Agrega todos los archivos nuevos o modificados y escribe un mensaje corto en el commit
- `git tag`
    - Permite añadir un identificador textual a un commit
    - `git tag` : Muestra los tags creados
    - `git tag -l "nombreTag*"` : Muestra y filtra los tags con cierto texto en particular
    - `git tag nombreTag hashcommit` : Crea un tag para el commit indicado
    - `git tag nombreTag -d` : Borra el tag indicado
    - `git tag -f nombreRama` : Actualziar una etiqueta existente
    - `git tag -a nombreTag` : Crea un tag a la que se le añade una descripción más extensa (como un commit)
    - `git push origin nombreEtiqeta` : Enviar etiqueta al repositorio remoto
- `git checkout archivo.ext` || `git checkout -- archivo.ext` || `git restore archivo.ext`
    - Deshace los últimos cambios del archivo respecto al último commit realizado
    - `git checkout -f`
        + Borra cambios en todos los ficheros
- `git restore --staged archivo.ext` || `git reset HEAD archivo.ext`
    - Quitar archivos del área de preparación
- `git rm archivo.ext`
    - Borrar archivo del repositorio
- `git rm --cached archivo.ext`
    - Borrar un archivo del seguimiento del repositorio una vez que ya se le haya hecho un commit
- `git rm -r --cached nombreDirectorio`
    - Borrar una carpeta y su contenido del repositorio una vez que ya se le haya realziado un commit
- `git diff archivo.ext`
    - Diferencia de cambios actuales en archivo vs último commit
    - `git diff --stat archivo.ext`
        + Estadística de cambios realizados en archivo
    - `git diff master nombreRama`
        + Muestra la diferencia de cambios entre ambas ramas
    - `git diff hashCommit1 hashCommit2`
        + Muestra la diferencia de cambios realizados entre ambos commits
    - `--no-index` : Ver diferencias entre dos archivos que no necesariamente forman parte del repositorio
    - `--name-only` : Ver unicamente el nombre de los archivos modificados entre dos commits
- `git checkout hashCommit`
    - Regresar en el tiempo a X commit
    - *hashCommit* mínimo 7 dígitos
    - `git checkout HEAD@X`
        + Visualiza el estado del proyecto X commits atrás
    - `git checkout master`
        + Regresa el apuntador cabecera (_HEAD_) a la actualidad en la rama master
- `git log` `[opciones]`
    - Mostrar el historial de commits
    - `--oneline` : Log de commits en una línea
    - `--all--graph` : Mostrar historial incluyendo las ramas donde fueron hechos los commits
    - `--decorate` : Agrega colores al log para resaltar información importante
    - `--pretty="format:"[texto y comodines]"`
        + Personalizar los campos que se desean mostrar en el log con un texto personalizado
        + Los campos de cada commit se escapan con *comodines* como:
            - `%n` : nombre de usuario
            - `%h` : hashCommit
    - `-p rutaArchiv` : Muestra el histórico de cambios realizados en el archivo
    - `-S "palabra a buscar"` : Buscar los commits en los cuales sale una palabra
- `git shortlog`
    - Ver cuantos commits a hecho los miembros del equipo
    - `-sn` : Muestra cuantos commit han hecho cada miembro
    - `-sn --all` : Todos los commits (también los borrados)
    - `-sn --all --no-merges` : Muestra cuantos commit han hecho cada miembro quitando los merges
- `git blame archivo`
    - Visualizar los cambios realizados por los miembros del equipo en un determinado archivo
    - `-c` : Muestra quien ha hecho cambios en dicho archivo identado
    - `-Llin_inicial,lin_final -c` : Muestra quien escribio el codigo desde *lin_inicial* a *lin_final* con un formato legible
-  `git show hashCommit:rutaArchivo`
    - Muestra el código fuente del archivo en el commit indicado
- `git stash`
    - Manda los cambios actuales del sistema de control de versiones a este espacio
    - Util cuando no se actualizó una rama remota y ya se hicieron cambios locales en el proyecto
    - `-u` : Crea un stash con todos los archivos. (Añadiendo los creados Untracked)
    - `save "mensaje"` : Crea un stash con el mensaje especificado
    - `list` : Permite visualizar todos los stash existentes
    - `clear` : Elimina todos los stash existentes
    - `drop` : Elimina el stash más reciente, tiene num_stash=0
    - `drop stash@{num_stash}` : Elimina un stash específico
    - `apply` : Aplica el stash más reciente (num_stash=0)
    - `apply stash@{num_stash}` : Aplica los cambios de un stash específico
    - `pop` : Aplica el stash más reciente al workspace y lo elimina
    - `pop stash@{num_stash}` : Aplica los cambios de un stash específico y elimina lo stash
    - `branch nombre_de_rama` : Crea una rama y aplica el stash mas reciente
    - `branch nombre_de_rama stash@{num_stash}` : Crea una rama y aplica el stash especificado
- `git gc`
    - Ejecuta el recoletor de basura
- `git clean`
    - Actúa en archivos sin seguimiento, este tipo de archivos son aquellos que se encuentran en el directorio de trabajo, pero que aún no se han añadido al índice de seguimiento de repositorio
    - `--dry-run` : Lista los archivos que serán borrados
    - `-f` : Borrar todos los archivos listados (que no son carpetas)
    - `-d` : Para considerar en el borrado directorios añadidos
- `git archive`
    - Crea un archivo comprimido a partir de una rama o archivos específicos
    - `-l` | `--list` : Muestra los formatos de compresión disponibles
    - `--format=nombreF` : Indicar el formato de compresión a exportar
    - `-o ruta/archivo` | `--outupt=ruta/archivo` : nombre de archivo con el que será exportado
    - `--remote=//servidor/ruta` : Guardar el archivo comprimido en la ruta del servidor
    - `git archive --format=zip master > project.zip` : Archiva la rama master en formato zip y el comprimido se llama "project"
    - `git archive master > project.zip` : Archiva la rama master en formato zip, otra forma de hacerlo
    - `git archive master | bzip2 > latest.tar.bz2` : Archiva la rama master, la compresión se realiza con comando de SO
    - `git archive -o latest.zip head` : Archivar en zip los últimos cambios realizados
    - `git archive --format=zip master^ carpeta1/ carpeta2/ *.ext > project.zip` : Exporta las carpetas señaladas y los archivos con extensión indicada en formato zip
    - `gdiff --name-only hashcommit | xargs git archive master --format=tar --output=archivo.tar` : archivar los ficheros afectados desde el commit indicado, con el formato y nombre indicado de la rama master

----------
## Ramas
- `git checkout -b nombreRama`
    - Crea una nueva rama y se posiciona en ella
- `git branch`
    - Lista las ramas existentes
- `git checkout` || `switch nombreRama`
    - Posicionarse en la rama especificada
- `git merge nombreRama`
    - Fusiona commits de la rama donde se encuentra posicionado con la rama indicada
- `git branch -d nombreRama`
    - Borra la ramma, comprueba que los commits de la rama estén integrados en la rama master
- `git branch -D nombreRama`
    - Elimina la rama independientemente de que los cambios realizados en ella estén en master
    - No se debe estar posicionado en la rama a eliminar
- `git merge --abort`
    - Cancelar la fusión de commits debido a algún conflicto
    - Cuando se terminen de resolver los conflictos de forma manual, realizar un `git add` y `commit` del archivo que presentó conflictos
- `git reflog`
    - Registro de cambios en las ramas
    - Muestra *hashCommit* y la descripción de dicho cambio

----------
## Remoto
- `git clone URLrepo`
    - Clonar repositorio almacenado en la nube
- `git remote -v`
    - Listar ramas remotas
- `git remote add upstream URLrepo`
    - Crea rama *upstream* para monitorear los cambios del repositorio en la nubre
- `git pull upstream master`
    - Descargar cambios del repositorio remoto
- `git push upstream master`
    - Subir cambios al repositorio remoto
- `git pull ramaRemota ramaLocal`
    - Sincroniza los commits de la rama local con la remota
    - Ej: `git pull origin master`
- `git push ramaRemota ramaLocal`
    - Envía cambios de la rama local a la remota
    - Ej: `git push origin master`
- `git push origin nombreRama`
    - Crea una rama de enlace remoto a partir de una rama remota
- `git push --delete origin nombreRama`
    - Borra la rama remota

----------
## Reescribiendo historial
- `git commit --amend`
    - Enmendar, deshace el último commit para agregar o quitar archivos, o bien para editar el mensaje del commit
    -  Antes de ejecutar el *amend*...
        + Si se trata de un archivo que no debe ir en ese commit, reestablecer el archivo y ejecutar el ammend. Es mejor utilizar un `git reset` si este es el caso
        + Si se olvidó realizar un cambio o se encontró alguna errata, editar el archivo, hacer un `git add `y luego ejecutar el *ammend*
- `git reset`
    - Deshacer cambios debido a commits erróneos, dichos cambios quedarán fuera del historial (elimina los commits posteriores)
    - `git reset hashCommit`
        + Deshace los cambios para tener el proyecto en el estado en que se hizo el commit indicado
    - `git reset HEAD^`
        + Apuntar un commit atrás en el pasado
        + Cada `^` significa el número de commits a retroceder
    - `git reset HEAD~X`
        + Retroceder *X* commits
    - `reset` || `reset --soft`
        + Deshace cambios y los deja en el workspace
    - `reset --mixed`
        + Deshace cambios, los deja en workspace pero no considera los archivos agregados o eliminados
    - `reset --hard`
        + No deja ningún cambio en workspace, lleva el proyecto al estado en el que se encontraba en ese momento
- `git reverse hashCommit` || `HEAD~X`
    - Revierte los cambios hasta el commit indicado, una vez que se restaura crea un commit indicando dicho cambio. No afecta el historial.
- `git cherry-pick  id_commit` : Permite coger uno o varios commits de otra rama sin tener que hacer un merge completo. Cuando se necesite realizar el merge, arrojará conflico debido al commit previamente combinado con la rama, se debe resolver manualmente
- `git rebase` : Realizar un merge entre ramas. Si se hace entre una rama y master es como si los cambios hubieran ocurrido directamente en master y la rama "se creó" hasta el commit del rebase, no antes. Primero se debe hacer un rebase en la rama y luego en master para evitar conflictos
    - `git rebase ramaOri` : Posicionado en la rama destino, se actualiza con lo que tiene la ramaOri
    - `-i HEAD~X`
        + Actualizar una rama respecto a *master* (merge)
        + Permite reescribir historial de commits (mover, eliminar, cambiar mensajes, etc)
    - `--abort` : Salir del proceso

----------
## Git Hooks
- Los hooks son scripts que se ejecutan automáticamente cada vez que ocurre un evento en particular en un repositorio de Git. Permiten personalizar el comportamiento interno de Git y desencadenar acciones personalizables en puntos clave del ciclo de vida del desarrollo.
- Los casos de uso incluyen alterar el entorno del proyecto según el estado del repositorio e implementar flujos de trabajo de integración continua, automatizar u optimizar prácticamente cualquier aspecto de su flujo de trabajo de desarrollo.
- Los hooks pueden residir en repositorios locales o del lado del servidor, y solo se ejecutan en respuesta a acciones en ese repositorio.
- Los hooks residen en el directorio *.git/hooks* de cada repositorio de Git. Los hooks deben tener permisos de ejecucicón del SO
- Puede utilizar cualquier lenguaje de secuencias de comandos que desee siempre que se pueda ejecutar. La línea shebang (`#!/bin/sh`) en cada secuencia de comandos define cómo se debe interpretar su archivo. Para usar un lenguaje diferente, se debe cambiar a la ruta de su intérprete. Ejemplo: `#!/usr/bin/env python`
- Mantener enlaces para un equipo de desarrolladores puede ser un poco complicado porque el directorio *.git/hooks* no se clona con el resto del proyecto, ni está bajo el control de versiones. Una solución simple es almacenar los hooks en el directorio del proyecto. Para instalar el hook, puede crear un enlace simbólico en *.git/hooks* o simplemente copiarlo y pegarlo en el directorio cada vez que se actualice.
- Hooks que se pueden configurar:
    - Los primeros 4 ganchos permiten conectarse a todo el ciclo de vida de la confirmación, y los 2 finales permiten realizar algunas acciones adicionales o verificaciones de seguridad para los comandos `git checkout` y `git rebase`.
    - Todos los hooks *pre* permiten modificar la acción que está a punto de tener lugar, mientras que los *post* se utilizan solo para notificaciones.
    - **pre-commit**. Se ejecuta cada vez que ejecuta `git commit` antes de que Git le pida al desarrollador un mensaje de confirmación o genere un objeto de confirmación. Puede utilizar este hooks para inspeccionar la instantánea que está a punto de confirmarse, ejecutar algunas pruebas automatizadas que se aseguren de que la confirmación no interrumpa ninguna funcionalidad existente. No se pasan argumentos al hook y si termina con un estado distinto de cero aborta toda la confirmación. 
    - **prepare-commit-msg**. Se llama después del hook *pre-commit* para llenar el editor de texto con un mensaje de confirmación. Este es un buen lugar para modificar los mensajes de confirmación generados automáticamente para confirmaciones pull-request o fusionadas. Se pasan de uno a tres argumentos al prepare-commit-msgscript:
        + El nombre de un archivo temporal que contiene el mensaje. Cambia el mensaje de confirmación modificando este archivo en el lugar.
        + El tipo de compromiso. Esto puede ser message (-m o -F), template (-t), merge (si la confirmación es una confirmación de fusión) o squash (si la confirmación es un pull-request).
        + El hash SHA1 de la confirmación relevante. Sólo si se da la opción -c, -C o --amend.
        + Si el hook termina con un estado distinto de cero aborta la confirmación.
    - **commit-msg**. Se llama después de que el usuario ingresa un mensaje de confirmación. Este es un lugar apropiado para advertir a los desarrolladores que su mensaje no se adhiere a los estándares de su equipo. El único argumento que se pasa a este hook es el nombre del archivo que contiene el mensaje. Si no le gusta el mensaje que ingresó el usuario, puede alterar este archivo en el lugar (al igual que con prepare-commit-msg) o puede abortar la confirmación por completo saliendo con un estado distinto de cero.
    - **post-commit**. Se llama inmediatamente después del hook `commit-msg`. No puede cambiar el resultado de la operación `git commit`, por lo que se usa principalmente con fines de notificación. El script no toma parámetros y su estado de salida no afecta la confirmación de ninguna manera. Para la mayoría de los scripts `post-commit`, querrá acceder a la confirmación que se acaba de crear. Puede usar `git rev-parse HEAD` para obtener el hash SHA1 de la nueva confirmación, o puede usar `git log -1 HEAD` para obtener toda su información.
    - **post-checkout**. Funciona de manera muy similar al hook *post-commit*, pero se llama siempre que verifica con éxito una referencia con `git checkout`. Esto es bueno para limpiar su directorio de trabajo de archivos generados que de otra manera causarían confusión. Este gancho acepta tres parámetros y su estado de salida no afecta al git checkoutcomando.
        + La referencia del HEAD anterior
        + La referencia del nuevo HEAD
        + Una bandera que le indica si se trató de un checkout de rama o de un archivo. La bandera será 1 y 0, respectivamente.
    - **pre-rebase**. Se llama antes de que `git rebase` cambie algo, por lo que es un buen lugar para asegurarse de que no suceda algo terrible. Este gancho toma 2 parámetros: 
        + La rama ascendente desde la que se bifurcó la serie y la rama que se está rebasando.
        + El segundo parámetro está vacío si el rebase es sobre la rama actual.
        + Para abortar el rebase, salga con un estado distinto de cero.
- Hooks del lado del servidor. Funcionan igual que los locales, excepto que residen en repositorios del lado del servidor (un repositorio central o un repositorio público de un desarrollador). Cuando se adjuntan al repositorio oficial, algunos de estos pueden servir como una forma de hacer cumplir la política al rechazar ciertas confirmaciones. Existen 3 ganchos:
    - Los hooks permiten reaccionar en diferentes etapas del proceso `git push`. La salida de los hooks del lado del servidor se envía a la consola del cliente, por lo que es muy fácil enviar mensajes al desarrollador. Pero, también debe tener en cuenta que estos scripts no devuelven el control del terminal hasta que terminan de ejecutarse, por lo que debe tener cuidado al realizar operaciones de larga duración.
    - **pre-receive**. Se ejecuta cada vez que alguien usa `git push` para enviar confirmaciones al repositorio. Siempre debe residir en el repositorio remoto que es el destino del envío. El hook se ejecuta antes de que se actualicen las referencias, por lo que es un buen lugar para hacer cumplir cualquier tipo de política de desarrollo que desee. Si no le gusta quién realiza el push, cómo está formateado el mensaje de confirmación o los cambios contenidos en la confirmación, puede rechazarlo. No puede evitar que los desarrolladores realicen confirmaciones mal formadas, puede evitar que estas confirmaciones ingresen al código base oficial. El script no toma parámetros, pero cada referencia que se empuja se pasa al script en una línea separada en la entrada estándar. Si se hace push de varias referencias, y el hook devuelve un estado distinto de cero se cancelan todas.
    - **update**. Se llama después *pre-receive* y funciona de la misma manera, se llama por separado para cada referencia que se hizo push. Eso significa que si el usuario intenta empujar 4 ramas, el hook se ejecuta 4 veces. Acepta los siguientes 3 argumentos:
        + El nombre de la referencia que se está actualizando
        + El nombre del objeto antiguo almacenado en la referencia
        + El nuevo nombre del objeto almacenado en la referencia
        + Puede rechazar algunas referencias y permitir otras
    - **post-receive**. Se ejecuta después de una operación de inserción exitosa, lo que lo convierte en un buen lugar para realizar notificaciones. Enviar correos electrónicos a otros desarrolladores y activar un sistema de integración continua son casos de uso comunes. El script no toma parámetros, pero se envía la misma información que a *pre-receive* través de la entrada estándar.

----------
## Configuraciones en GIT
- Niveles de configuración
    - `--local` : De manera predeterminada, `git config` escribirá en un nivel local si no se pasa ninguna opción de configuración. Se aplica al repositorio en el que se invoca `git config`. Los valores de configuración locales se almacenan en un archivo que se puede encontrar en el directorio *.git* del repositorio: *.git/config*
    - `--global` : Es específica del usuario, lo que significa que se aplica al usuario de un SO. Los valores de configuración globales se almacenan en un archivo que se encuentra en el directorio principal de un usuario. *~ /.gitconfig* en sistemas unix y *C:\\.gitconfig* en Windows.
    - `--system` : Se aplica a toda una máquina. Afecta a todos los usuarios de un SO y a todos los repositorios. El archivo de configuración de nivel de sistema se encuentra en un archivo *gitconfig* fuera de la ruta raíz del sistema. */etc/gitconfig* en sistemas Unix. En Windows, este archivo se encuentra en *C:\ProgramData\Git\config*.
- `git config --list`
    - Muestra todas las configuraciones establecidas en el archivo *~/.gitconfig*
- `git config --global alias.nombreAlias "comando de git"`
    - Configura el comando especificado en un Alias en las configuraciones globales de git en la computadora.
- `git config --global commit.template ~/.gitmessage.txt`
    - Configura el archivo *.gitmessage.txt* como  plantilla para la escritura de commits de forma global
- `git config --global core.editor nombreEditor`
    - Configura el editor por defecto para escritura de commits, por defecto es *Vim*
    - Opciones *vim*, *emacs*, *nano*, personalizado: *"'c:/ruta/editor.exe' -w"~*
- `git config --global core.pager paginador`
    - Cuando se muestra un log o diff, git utiliza por defecto *less*, se puede configurar *more* o incluso `''` para no utilizar ningún paginador y mostrar todo el contenido directamente
- `git config --global core.excludesfile ~/.gitignore_global`
    - Configura de forma global el archivo *.gitignore_global*, funciona como un archivo *.gitignore* pero de forma global
- `git config --global help.autocorrect tiempo`
    - Cuando se establece esta configruación, git intenta corregir el error en el comando escrito, la unidad de tiempo establecida es en *100ms*, si se coloca 50, el tiempo de espera hasta la ejecución del comando es de *5s*
- `git config --global core.autocrlf valor`
    - Git convierte automáticamente los finales CRLF en LF al hacer confirmaciones de cambios (commit); y, viceversa, al extraer código (checkout) a la carpeta de trabajo.
    - Si se trabaja en Windows, colocar `true`, para convertir finales LF en CRLF cuando se extraiga código (checkout)
    - Si se trabaja en Linux o Mac, entonces no es de interés convertir automáticamente los finales de línea al extraer código, sino indicar a Git que convierta CRLF en LF al confirmar cambios (commit) con un valor `input`
    - Si se trabaja en un entorno donde solo haya máquinas Windows, puedes desconectar esta funcionalidad, para almacenar CRLFs en el repositorio. Ajustando el parámero a `false`
- `git config --global core.whitespace opciones`
    - Git viene preajustado para detectar y resolver algunos de los problemas más típicos relacionados con los espacios en blanco. Puede vigilar seis tipos de problemas de espaciado: tres los tiene activados por defecto  y tres vienen desactivados por defecto.
    - Los que están activos de forma predeterminada son `blank-at-eol`, que busca espacios al final de la línea; `blank-at-eof`, que busca líneas en blanco al final del archivo y `espace-before-tab`, que busca espacios delante de las tabulaciones al comienzo de una línea.
    - Los que están inactivos de forma predeterminada son `ident-with-non-tab`, que busca líneas que empiezan con espacios en blanco en lugar de tabulaciones (y se controla con la opción *tabwidth*); `tab-in-indent`, que busca tabulaciones en el trozo indentado de una línea; y `cr-at-eol`, que informa a Git de que los CR al final de las líneas son correctos.
    - Para activar o desactivar, usar los valores on/off separados por comas. Se Pueden desactivar dejándolos fuera de la cadena de ajustes, como añadiendo el prefijo `-` delante del valor.

### Cambiando el usuario que realiza commits
- Ir a las credenciales de windows, buscar las credenciales de Git y/o GitHub y eliminarlas, o en su caso, modificarlas
- En el bash de git :
    - `git config --global --list`
        + Para listar las configuraciones generales de Git
    - `git config --global --unset-all user.name`
    - `git config --global --unset-all user.email`
        + Eliminar el usuario actual (username y correo)
    - `git config --global --add user.name nuevoUsuario`
    - `git config --global --add user.email ejemplo@correo.com`
        + Configurar los nuevos datos (username y correo)

----------
## Git Attributes
- Algunos ajustes pueden ser especificados para una ruta (path) concreta, de tal forma que Git los aplicará únicamente para una carpeta o grupo de archivos determinado. Estos ajustes específicos se denominan atributos en Git, y se establecen mediante un archivo *.gitattributes* en uno de los directorios del proyecto (normalmente en la raíz del proyecto), o mediante el archivo *git/info/attributes*.
- Por medio de los atributos, se pueden indicar diferentes estrategias de fusión para archivos o carpetas concretas del proyecto, decirle a Git cómo comparar archivos no textuales, o indicar a Git que filtre ciertos contenidos antes de guardarlos o de extraerlos del repositorio.
- Cada línea del archivo tiene la forma: `pattern attr1 attr2 ...`
- Los espacios en blanco iniciales y finales se ignoran
- Las líneas que comienzan con `#` se ignoran
- Cuando el patrón coincide con la ruta en cuestión, los atributos enumerados en la línea se asignan a la ruta
- Cuando más de un patrón coincide con la ruta, la línea posterior anula la línea anterior.Esta anulación se hace por atributo.
- Los patrones negativos están prohibidos
- Los patrones que coinciden con un directorio no coinciden recursivamente con las rutas dentro de este (usar `path/` no tiene efecto, usar `path/**` en su lugar)
- Cada atributo puede estar en alguno de estos estados para cada ruta:
    - *Set* : La ruta tiene el atributo con valor especial "true"; esto se especifica listando sólo el nombre del atributo en la lista de atributos.
    - *Unset* : La ruta tiene el atributo con valor especial "falso"; esto se especifica enumerando el nombre del atributo con el prefijo de un guión `-` en la lista de atributos.
    - *Set to a value* : La ruta tiene el atributo con un valor de cadena especificado; esto se especifica enumerando el nombre del atributo seguido de un signo `=` y su valor en la lista de atributos.
    - *Unspecified* : Ningún patrón coincide con la ruta, y nada dice si la ruta tiene o no el atributo, se dice que el atributo no está especificado.
- Check-out y check-in. Estos atributos afectan la forma en que los contenidos almacenados en el repositorio se copian en los archivos del árbol de trabajo cuando se ejecutan comandos como `git switch`, `git checkout` y `git merge`. También afectan la forma en que Git almacena el contenido que se prepara en el árbol de trabajo en el repositorio después de `git add` y `git commit`.

### Text
- Habilita y controla la normalización de final de línea en el directorio de trabajo, use el atributo `eol` para un solo archivo y la variable de configuración `core.eol` para todos los archivos de texto. Tenga en cuenta que la configuración `core.autocrlf = true | input` anula `core.eol`
- *Set* : Habilita la normalización de final de línea y marca la ruta como un archivo de texto. La conversión de final de línea se realiza sin adivinar el tipo de contenido.
- *Unset* : Le indica a Git que no intente ninguna conversión de final de línea.
- *Set to a value* : "auto". La ruta se marca para la conversión automática de final de línea. Si Git decide que el contenido es texto, sus finales de línea se convierten a LF. Cuando el archivo se ha confirmado con CRLF, no se realiza ninguna conversión.
- *Unspecified* : Si no está especificado, Git usa la variable de configuración *core.autocrlf* para determinar si el archivo debe convertirse.
- `eol`
    - Este atributo establece un estilo de final de línea específico que se utilizará en el directorio de trabajo. Permite la conversión de final de línea sin ninguna verificación de contenido.
    - *Set to a value* : "crlf". Este ajuste obliga a Git a normalizar las terminaciones de las líneas de este archivo en CRLF.
    - *Set to a value* : "lf". Este ajuste obliga a Git a normalizar las terminaciones de línea a LF.
~~~ properties
    -          text=auto
    -.txt       text
    -.vcproj    text eol=crlf
    -.sh        text eol=lf
    -.jpg       -text
~~~

### Archivos binarios
Indicarle a Git cuáles archivos son binarios (en los casos en que Git no podría llegar a determinarlo por sí mismo), dándole a Git instrucciones especiales sobre cómo tratar estos archivos. Por ejemplo, algunos archivos de texto se generan automáticamente y no tiene sentido compararlos; mientras que algunos archivos binarios sí que pueden ser comparados. Con esto, Git no intentará convertir ni corregir problemas CRLF en los finales de línea, ni intentará hacer comparaciones ni mostar diferencias de este archivo cuando se ejecuten comandos `git show` o `git diff` en el proyecto.
- `*.ext binary`
    - Indica a git que trate archivos con determinada extensión como archivos binarios
- `*.ext diff=nombreHerramienta`
    - Indica a Git que herramienta debe utilizar para comparar los cambios en un archivo
    - Para establecer una herramienta personalizada para comparar archivos bianrios `git config diff.nombreHerramienta.textconv programa`

### working-tree-encoding
- Git reconoce archivos codificados en ASCII o uno de sus superconjuntos (UTF-8, ISO-8859-1) como archivos de texto. Los archivos codificados en otras codificaciones (por ejemplo UTF-16) se interpretan como binarios y, por lo tanto, las herramientas de procesamiento de texto Git integradas (por ejemplo, git diff ), así como la mayoría de las interfaces web de Git no visualizan el contenido de estos archivos de forma predeterminada.
- Puede decirle a Git la codificación de un archivo en el directorio de trabajo, Git vuelve a codificar el contenido de la codificación especificada a UTF-8.
- Las implementaciones alternativas de Git (JGit o libgit2) y las versiones anteriores de Git (a partir de marzo de 2018) no admiten este atributo. Si decide utilizar el atributo, se recomienda  asegurarse de que todos los clientes que trabajan con el repositorio lo admitan.
- Volver a codificar contenido a codificaciones que no sean UTF puede provocar errores, ya que es posible que la conversión no sea segura para el viaje de ida y vuelta UTF-8. Si sospecha que su codificación no es segura de ida y vuelta, agréguela a `core.checkRoundtripEncoding` para que Git verifique la codificación de ida y vuelta.
- Use este atributo solo si no puede almacenar un archivo en codificación UTF-8 y si desea que Git pueda procesar el contenido como texto.
- Uso: `*.ext   text working-tree-encoding=UTF-16LE eol=CRLF`

### Filtros
- Se puede escribir filtros personalizados para realizar sustituciones en los archivos al guardar o recuperar (commit/checkout). Se trata de los filtros “clean” y “smudge”.
- Se indican filtros para carpetas o archivos determinados y luego preparar scripts personalizados para procesarlos justo antes de confirmar cambios en ellos (“clean”), o justo antes de recuperarlos (“smudge”).
- `*.ext filter=nombreFiltro`
    - Establece el atributo a archivos con determinada extensión
- Estableciendo los filtros en las configuraciones
    - `git config filter.nombreFiltro.smudge programa | script`
    - `git config filter.nombreFiltro.clean 'comando'`

### Exportación del repositorio
- Se puede indicar a Git que ignore y no exporte ciertos archivos o carpetas cuando genera un archivo de almacenamiento. Cuando se tiene alguna carpeta o archivo que no se desea incluir en los registros, pero que se quiere tener controlado en el proyecto.
- Cada vez que se ejecute el comando `git archive` para crear un archivo comprimido del proyecto, esa carpeta no se incluirá en él.
- Uso: `patron export-ignore`
- Otra cosa que se puede realizar sobre los archivos es algún tipo de sustitución simple de claves. Git te permite poner la cadena `$Format:$` en cualquier archivo, con cualquiera de las claves de formateo de `--pretty=format`
- Por ejemplo, si se desea incluir un archivo llamado *LAST_COMMIT* en el proyecto, y poner en él automáticamente la fecha de la última confirmación de cambios cada vez que se ejecute el comando `git archive`
~~~ bash
echo 'Last commit date: $Format:%cd$' > LAST_COMMIT
echo "LAST_COMMIT export-subst" >> .gitattributes
git add LAST_COMMIT .gitattributes
git commit -am 'adding LAST_COMMIT file for archives'
~~~

### Estrategias de fusión (merge)
- Una opción muy útil es la que permite indicar a Git que no intente fusionar ciertos archivos concretos cuando tengan conflictos, manteniendo en su lugar los archivos principales sobre los de cualquier otro.
- Puede ser interesante si una rama del proyecto es divergente o esta especializada, pero se desea seguir siendo capaz de fusionar cambios de vuelta desde ella, e ignorar ciertos archivos. Si hay un archivo modificado en las dos ramas, y se desea fusionar en la otra rama sin perturbarlo:
    - `archivo.ext merge=ours`
    - Se define una estrategia ours con: `git config --global merge.ours.driver true`
    - Con esto, se realiza un auto merging recursivo

