# Comandos GIT

- `git config --global user.name "nombreUsuario"`
    * Configurar el nombre del usuario de forma global
- `git config --global user.mail "ejemplo@email.com"`
    * Configurar el correo del usuario de forma global
- `git init`
    * Inicializar un nuevo repositorio a nivel de la carpeta donde se ejecuta el comando,
    * Se crea una carpeta oculta _.git_ en el nuevo espacio de trabajo
    * `--bare ruta/directorio.git` : Crea un repositorio de Git vacío, pero omite el directorio de trabajo, lo que imposibilita la edición de archivos y la confirmación de cambios en ese repositorio. Útil para aplicar `git push` y `git pull`, pero nunca realizar confirmaciones directamente en él.
    * `--template ruta/directorio` : Inicializa un nuevo repositorio de Git y copia los archivos de la plantilla al repositorio. Se puede configurar una plantilla para que tenga los directorios y archivos predeterminados que se copiarán en el subdirectorio de _.git_ del nuevo repositorio. Las plantillas de Git suelen ubicarse en /_usr/share/git-core/templates_, pero pueden encontrarse en una ruta diferente.
    * `--separate-git-dir=ruta/directorio` : Crea un archivo de texto que contiene la ruta al direcotrio _.git_ .
        + Resulta muy útil:
        + Si se quiere almacenar el directorio _.git_ en una ubicación o unidad independiente de los archivos de trabajo del proyecto.
        + Para mantener los archivos ocultos de la configuración del sistema (.bashrc, .vimrc, etc.) en el directorio principal, mientras que la carpeta de .git se conserva en otro lugar.
        + Cuando el historial de Git ocupa mucho espacio en el disco y necesitas moverlo a otro sitio de una unidad independiente de gran capacidad.
        + Cuando se quiere tener un proyecto de Git en un directorio de acceso público como _www:root_.
        + Se puede llamar a `git init --separate-git-dir` en un repositorio que ya exista y el directorio de _.git_ se moverá a la ruta de especificada.
    * `--SHARED[=(FALSE|TRUE|UMASK|GROUP|ALL|WORLD|EVERYBODY|0XXX)]` : Define los permisos de acceso del nuevo repositorio. Esto especifica qué usuarios y grupos de los que utilizan permisos de nivel de Unix pueden realizar las acciones de envío e incorporación de cambios en el repositorio.
- `git comando --help`
    * Consulta el modo de uso de un comando, información detallada
- `git cat archivo.ext`
    * Visualizar contenido de archivo en la bash
- `git grep "palabra"`
    * Busca concidencias con la palabra escrita en los archivos del repositorio
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
    * `--no-index` : Ver diferencias entre dos archivos que no necesariamente forman parte del repositorio
    * `--name-only` : Ver unicamente el nombre de los archivos modificados entre dos commits
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
- `git shortlog`
    * Ver cuantos commits a hecho los miembros del equipo
    * `-sn` : Muestra cuantos commit han hecho cada miembro
    * `-sn --all` : Todos los commits (también los borrados)
    * `-sn --all --no-merges` : Muestra cuantos commit han hecho cada miembro quitando los merges
- `git blame archivo`
    * Visualizar los cambios realizados por los miebros del equipo en un determinado archivo
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
- `git clean`
    * Actúa en archivos sin seguimiento, este tipo de archivos son aquellos que se encuentran en el directorio de trabajo, pero que aún no se han añadido al índice de seguimiento de repositorio
    * `--dry-run` : Lista los archivos que serán borrados
    * `-f` : Borrar todos los archivos listados (que no son carpetas)
    * `-d` : Para considerar en el borrado directorios añadidos
- `git archive`
    * Crea un archivo comprimido a partir de una rama o archivos específicos
    * `-l` | `--list` : Muestra los formatos de compresión disponibles
    * `--format=nombreF` : Indicar el formato de compresión a exportar
    * `-o ruta/archivo` | `--outupt=ruta/archivo` : nombre de archivo con el que será exportado
    * `--remote=//servidor/ruta` : Guardar el archivo comprimido en la ruta del servidor
    * `git archive --format=zip master > project.zip` : Archiva la rama master en formato zip y el comprimido se llama "project"
    * `git archive master > project.zip` : Archiva la rama master en formato zip, otra forma de hacerlo
    * `git archive master | bzip2 > latest.tar.bz2` : Archiva la rama master, la compresión se realiza con comando de SO
    * `git archive -o latest.zip head` : Archivar en zip los últimos cambios realizados
    * `git archive --format=zip master^ carpeta1/ carpeta2/ *.ext > project.zip` : Exporta las carpetas señaladas y los archivos con extensión indicada en formato zip
    * `gdiff --name-only hashcommit | xargs git archive master --format=tar --output=archivo.tar` : archivar los ficheros afectados desde el commit indicado, con el formato y nombre indicado de la rama master

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
- `git push ramaRemota ramaLocal`
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
- `git cherry-pick  id_commit` : Permite coger uno o varios commits de otra rama sin tener que hacer un merge completo. Cuando se necesite realizar el merge, arrojará conflico debido al commit previamente combinado con la rama, se debe resolver manualmente
- `git rebase` : Realizar un merge entre ramas. Si se hace entre una rama y master es como si los cambios hubieran ocurrido directamente en master y la rama "se creó" hasta el commit del rebase, no antes. Primero se debe hacer un rebase en la rama y luego en master para evitar conflictos
    * `git rebase ramaOri` : Posicionado en la rama destino, se actualiza con lo que tiene la ramaOri
    * `-i HEAD~X`
        + Actualizar una rama respecto a _master_ (merge)
        + Permite reescribir historial de commits (mover, eliminar, cambiar mensajes, etc)
    * `--abort` : Salir del proceso

___
## Configuraciones en GIT
- Niveles de configuración
    * `--local` : De manera predeterminada, `git config` escribirá en un nivel local si no se pasa ninguna opción de configuración. Se aplica al repositorio en el que se invoca `git config`. Los valores de configuración locales se almacenan en un archivo que se puede encontrar en el directorio _.git_ del repositorio: _.git/config_
    * `--global` : Es específica del usuario, lo que significa que se aplica al usuario de un SO. Los valores de configuración globales se almacenan en un archivo que se encuentra en el directorio principal de un usuario. _~ /.gitconfig_ en sistemas unix y _C:\\.gitconfig _en Windows.
    * `--system` : Se aplica a toda una máquina. Afecta a todos los usuarios de un SO y a todos los repositorios. El archivo de configuración de nivel de sistema se encuentra en un archivo _gitconfig_ fuera de la ruta raíz del sistema. _/etc/gitconfig_ en sistemas Unix. En Windows, este archivo se encuentra en _C:\ProgramData\Git\config_.
- `git config --list`
    * Muestra todas las configuraciones establecidas en el archivo _~/.gitconfig_
- `git config --global alias.nombreAlias "comando de git"`
    * Configura el comando especificado en un Alias en las configuraciones globales de git en la computadora.
- `git config --global commit.template ~/.gitmessage.txt`
    * Configura el archivo _.gitmessage.txt_ como  plantilla para la escritura de commits de forma global
- `git config --global core.editor nombreEditor`
    * Configura el editor por defecto para escritura de commits, por defecto es _Vim_
    * Opciones _vim_, _emacs_, _nano_, personalizado: _"'c:/ruta/editor.exe' -w"~_
- `git config --global core.pager paginador`
    * Cuando se muestra un log o diff, git utiliza por defecto _less_, se puede configurar _more_ o incluso `''` para no utilizar ningún paginador y mostrar todo el contenido directamente
- `git config --global core.excludesfile ~/.gitignore_global`
    * Configura de forma global el archivo _.gitignore\_global_, funciona como un archivo _.gitignore_ pero de forma global
- `git config --global help.autocorrect tiempo`
    * Cuando se establece esta configruación, git intenta corregir el error en el comando escrito, la unidad de tiempo establecida es en _100ms_, si se coloca 50, el tiempo de espera hasta la ejecución del comando es de _5s_
- `git config --global core.autocrlf valor`
    * Git convierte automáticamente los finales CRLF en LF al hacer confirmaciones de cambios (commit); y, viceversa, al extraer código (checkout) a la carpeta de trabajo.
    * Si se trabaja en Windows, colocar `true`, para convertir finales LF en CRLF cuando se extraiga código (checkout)
    * Si se trabaja en Linux o Mac, entonces no es de interés convertir automáticamente los finales de línea al extraer código, sino indicar a Git que convierta CRLF en LF al confirmar cambios (commit) con un valor `input`
    * Si se trabaja en un entorno donde solo haya máquinas Windows, puedes desconectar esta funcionalidad, para almacenar CRLFs en el repositorio. Ajustando el parámero a `false`
- `git config --global core.whitespace opciones`
    * Git viene preajustado para detectar y resolver algunos de los problemas más típicos relacionados con los espacios en blanco. Puede vigilar seis tipos de problemas de espaciado: tres los tiene activados por defecto  y tres vienen desactivados por defecto.
    * Los que están activos de forma predeterminada son `blank-at-eol`, que busca espacios al final de la línea; `blank-at-eof`, que busca líneas en blanco al final del archivo y `espace-before-tab`, que busca espacios delante de las tabulaciones al comienzo de una línea.
    * Los que están inactivos de forma predeterminada son `ident-with-non-tab`, que busca líneas que empiezan con espacios en blanco en lugar de tabulaciones (y se controla con la opción _tabwidth_); `tab-in-indent`, que busca tabulaciones en el trozo indentado de una línea; y `cr-at-eol`, que informa a Git de que los CR al final de las líneas son correctos.
    * Para activar o desactivar, usar los valores on/off separados por comas. Se Pueden desactivar dejándolos fuera de la cadena de ajustes, como añadiendo el prefijo `-` delante del valor.

### Cambiando el usuario que realiza commits
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

## Git Attributes
- Algunos ajustes pueden ser especificados para una ruta (path) concreta, de tal forma que Git los aplicará únicamente para una carpeta o grupo de archivos determinado. Estos ajustes específicos se denominan atributos en Git, y se establecen mediante un archivo _.gitattributes_ en uno de los directorios del proyecto (normalmente en la raíz del proyecto), o mediante el archivo _git/info/attributes_.
- Por medio de los atributos, se pueden indicar diferentes estrategias de fusión para archivos o carpetas concretas del proyecto, decirle a Git cómo comparar archivos no textuales, o indicar a Git que filtre ciertos contenidos antes de guardarlos o de extraerlos del repositorio.
- Cada línea del archivo tiene la forma: `pattern attr1 attr2 ...`
- Los espacios en blanco iniciales y finales se ignoran
- Las líneas que comienzan con `#` se ignoran
- Cuando el patrón coincide con la ruta en cuestión, los atributos enumerados en la línea se asignan a la ruta
- Cuando más de un patrón coincide con la ruta, la línea posterior anula la línea anterior.Esta anulación se hace por atributo.
- Los patrones negativos están prohibidos
- Los patrones que coinciden con un directorio no coinciden recursivamente con las rutas dentro de este (usar `path/` no tiene efecto, usar `path/**` en su lugar)
- Cada atributo puede estar en alguno de estos estados para cada ruta:
    * _Set_ : La ruta tiene el atributo con valor especial "true"; esto se especifica listando sólo el nombre del atributo en la lista de atributos.
    * _Unset_ : La ruta tiene el atributo con valor especial "falso"; esto se especifica enumerando el nombre del atributo con el prefijo de un guión `-` en la lista de atributos.
    * _Set to a value_ : La ruta tiene el atributo con un valor de cadena especificado; esto se especifica enumerando el nombre del atributo seguido de un signo `=` y su valor en la lista de atributos.
    * _Unspecified_ : Ningún patrón coincide con la ruta, y nada dice si la ruta tiene o no el atributo, se dice que el atributo no está especificado.
- Check-out y check-in. Estos atributos afectan la forma en que los contenidos almacenados en el repositorio se copian en los archivos del árbol de trabajo cuando se ejecutan comandos como `git switch`, `git checkout` y `git merge`. También afectan la forma en que Git almacena el contenido que se prepara en el árbol de trabajo en el repositorio después de `git add` y `git commit`.

### Text
- Habilita y controla la normalización de final de línea en el directorio de trabajo, use el atributo `eol` para un solo archivo y la variable de configuración `core.eol` para todos los archivos de texto. Tenga en cuenta que la configuración `core.autocrlf = true | input` anula `core.eol`
- _Set_ : Habilita la normalización de final de línea y marca la ruta como un archivo de texto. La conversión de final de línea se realiza sin adivinar el tipo de contenido.
- _Unset_ : Le indica a Git que no intente ninguna conversión de final de línea.
- _Set to a value_ : "auto". La ruta se marca para la conversión automática de final de línea. Si Git decide que el contenido es texto, sus finales de línea se convierten a LF. Cuando el archivo se ha confirmado con CRLF, no se realiza ninguna conversión.
- _Unspecified_ : Si no está especificado, Git usa la variable de configuración _core.autocrlf_ para determinar si el archivo debe convertirse.
- `eol`
    * Este atributo establece un estilo de final de línea específico que se utilizará en el directorio de trabajo. Permite la conversión de final de línea sin ninguna verificación de contenido.
    * _Set to a value_ : "crlf". Este ajuste obliga a Git a normalizar las terminaciones de las líneas de este archivo en CRLF.
    * _Set to a value_ : "lf". Este ajuste obliga a Git a normalizar las terminaciones de línea a LF.
~~~ yml
    *           text=auto
    *.txt       text
    *.vcproj    text eol=crlf
    *.sh        text eol=lf
    *.jpg       -text
~~~

### Archivos binarios
Indicarle a Git cuáles archivos son binarios (en los casos en que Git no podría llegar a determinarlo por sí mismo), dándole a Git instrucciones especiales sobre cómo tratar estos archivos. Por ejemplo, algunos archivos de texto se generan automáticamente y no tiene sentido compararlos; mientras que algunos archivos binarios sí que pueden ser comparados. Con esto, Git no intentará convertir ni corregir problemas CRLF en los finales de línea, ni intentará hacer comparaciones ni mostar diferencias de este archivo cuando se ejecuten comandos `git show` o `git diff` en el proyecto.
- `*.ext binary`
    * Indica a git que trate archivos con determinada extensión como archivos binarios
- `*.ext diff=nombreHerramienta`
    * Indica a Git que herramienta debe utilizar para comparar los cambios en un archivo
    * Para establecer una herramienta personalizada para comparar archivos bianrios `git config diff.nombreHerramienta.textconv programa`

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
    * Establece el atributo a archivos con determinada extensión
- Estableciendo los filtros en las configuraciones
    * `git config filter.nombreFiltro.smudge programa | script`
    * `git config filter.nombreFiltro.clean 'comando'`

### Exportación del repositorio
- Se puede indicar a Git que ignore y no exporte ciertos archivos o carpetas cuando genera un archivo de almacenamiento. Cuando se tiene alguna carpeta o archivo que no se desea incluir en los registros, pero que se quiere tener controlado en el proyecto.
- Cada vez que se ejecute el comando `git archive` para crear un archivo comprimido del proyecto, esa carpeta no se incluirá en él.
- Uso: `patron export-ignore`
- Otra cosa que se puede realizar sobre los archivos es algún tipo de sustitución simple de claves. Git te permite poner la cadena `$Format:$` en cualquier archivo, con cualquiera de las claves de formateo de `--pretty=format`
- Por ejemplo, si se desea incluir un archivo llamado _LAST\_COMMIT_ en el proyecto, y poner en él automáticamente la fecha de la última confirmación de cambios cada vez que se ejecute el comando `git archive`
~~~ bash
echo 'Last commit date: $Format:%cd$' > LAST_COMMIT
echo "LAST_COMMIT export-subst" >> .gitattributes
git add LAST_COMMIT .gitattributes
git commit -am 'adding LAST_COMMIT file for archives'
~~~

### Estrategias de fusión (merge)
- Una opción muy útil es la que permite indicar a Git que no intente fusionar ciertos archivos concretos cuando tengan conflictos, manteniendo en su lugar los archivos principales sobre los de cualquier otro.
- Puede ser interesante si una rama del proyecto es divergente o esta especializada, pero se desea seguir siendo capaz de fusionar cambios de vuelta desde ella, e ignorar ciertos archivos. Si hay un archivo modificado en las dos ramas, y se desea fusionar en la otra rama sin perturbarlo:
    * `archivo.ext merge=ours`
    * Se define una estrategia ours con: `git config --global merge.ours.driver true`
    * Con esto, se realiza un auto merging recursivo

