# Comandos consola Linux

- Si se teclea alguna letra y se presiona TAB, se autocompleta algún nombre de archivo o directorio


* `ctrl + R` Busca algún comando en el historial

---
## Para interactuar con el SO

- `sudo comandos`
	* super user do, ejecutar comandos como admin
- `sudo su` || `su -`
	* Cambiar a usuario root para ejecutar comandos posteriores como admin
- `sudo apt-get update`
	* Resincroniza los índices de paquetes (de los directorios `/etc`, `/apt`, `/sources.list`) busca actualizaciones
- `sudo apt-get upgrade -y`
	* Instala nuevas versiones de los paquetes y dependencias
	* Con param `-y` se confirma el deseo de instalar las acts
- `sudo apt-get dist-upgrade`
	* Adicionalmente a `upgrade`, controla los cambios en las dependencias con la capacidad de resolver conflictos

Nota: paquete === aplicación

- `sudo apt-get install paquete1 paquete2 ...`
	* instalar progs
- `sudo apt-get remove paquete1 paquete2 ...`
	* Se desintala el paquete pero se quedan archivos de configuración y dependencias
- `sudo apt-get purge paquete1 paquete2 ...`
	* Elimina todo, todo, todo! del paquete
- `sudo apt-get autoremove`
	* Limpieza general de archivos remanentes
- `sudo shutdown`
	* Apagar máquina
- `sudo reboot`
	* Reiniciar máquina
- `fdisk -lm`
	* Muestra particiones de unidades de almacenamiento
- `ps [opciones]`
	* Visualizar los procesos en nuestro sistema, y obtener informacion de los mismos
	* `aux` : muestra todos los procesos del sistema
	* `axjf` : muestra un árbol jerárquico con la ruta del programa al que pertenece el proceso
- `top [opciones]`
	* Es otro gestor de procesos
	* `ps` nos muestra un listado de procesos estático, es decir, informa de los procesos, nombres, usuarios o recursos que se están usando en el momento de la petición; `top` da un informe en tiempo real de los mismos.
	* `–d N` : Donde N es el número de segundos a transcurrir entre cada muestreo
	* `–u usuario` : Mostrar los procesos del usuario especificado
- `kill [opciones] [PID del proceso]`
	* Detener los procesos que necesitemos
	* Envía una señal denominada TERM al proceso a detener. Esta señal TERM pedirá al proceso que termine, permitiéndole gestionar su función de cierre, completando las tareas necesarias y limpiando la información que ha cargado en memoria
	* `kill –KILL [PID del proceso]`
		+ En el caso de encontrarnos ante un proceso que no quiere cerrarse, se elimina por la fuerza con este comando, pasando a root previamente para no recibir  error
	* `-N` : Estas señales también pueden ser identificadas con números.
		+ _TERM_ puede ser pasada al proceso mediante `-15`
		+ `–KILL` es el equivalente a pasar `-9`
	* `kill –HUP [PID del proceso]`
		+ Para reiniciar servicios, la mayoría de ellos responde al argumento ‘HUP’ (Hang up) de kill.
		+ Su equivalente numérico es -1
- `pkill -N htop`
	* Si se conoce el nombre exacto del proceso también se puede usar
	* `pkill` funciona exactamente igual que `kill`, pero preparado para trabajar con nombres de proceso en lugar de con PID
- `killall programa`
	* Es una variante del comando `kill` con el que se envia la misma señal a todos los procesos pertenecientes a un programa

---
## Comandos esenciales

- `password nombreUsuario`
	* Asignar una contraseña para el usuario
- `su nombreUsuario`
	* Cambiar de sesión a la del usuario indicado

- `man comando`
	* Ver ayuda sobre algún comando
- `man hier`
	* Ver estructura de directorios
- `pwd`
	* Ubicación del directorio donde se encuentra
- `cd ruta`
	* change directory, cambiar de directorio
	* `cd ..` : Regresar un directorio atrás
	* `cd /` : Ir a raiz
		+ La `/` siempre es respecto a la raiz!
		+ Sin la barra y se coloca una ruta, se mueve hacia subdirectorios
		+ `./` Relativo al directorio actual
		+ `../` Directorio superior
- `ls`
	* list, listar directorios dentro del directorio donde se esté posicionado
- `ls [opciones] directorio`
	* `ls *.extension` : Listar archivos con extensión especificada
	* `ls -lah` : Listar con un formato legible
		+ `l`: listado en una columna con detalles de cada fichero
		+ `a`: todos los archivos, incluyendo ocultos
		+ `h`: formato legible para los humanos, Bytes con prefijos (KB, MB, etc)
		+ `t`: ordenar por marca de tiempo (fecha de modificación)
		+ `S`: ordenar por tamaño de fichero
		+ `X`: ordenar fichero alfabeticamente por su extensión
		+ `F`: a los directorios les agrega al final "/" y a los ejecutables "/*"
		+ `r`: revertir el orden del listado (Z-A, antiguo-nuevo, - to + pesado)
- `mkdir nombreDirectorio`
	* Crear un directorio dentro del directorio actual
- `touch archivo.ext`
	* Crear un archivo
- `nombreApp archivo.ext`
	abrir archivo con un programa instalado. p.ej. _nano_
- `history`
	* Muestra historial de comandos ejecutados
- `rm archivo.ext`
	* Eliminar un archivo
- `rm -R directorio/`
	* Elimina archivos de un directorio y la carpeta misma
- `cp ruta/archivo.ext rutaCopia`
	* Copiar un archivo a otro directorio
- `cp -r directorio/ rutaCopia/nombreDir`
	* Copiar carpeta, subcarpetas y archivos de forma recursiva (-r)
	* nombreDir : se puede cambiar el nombre del directorio en su nuevo destino
- `mv rutaArch rutaDestino`
	* Mover un fichero
- `mv directorio rutaDest/nombreDir`
	* Mover directorio a la ruta destino, se le puede cambiar el nombre
- `mv directorio nuevoNombre`
	* Se utiliza para renombrar un directorio
- `comando1 && comando2`
	* El doble andpersand sirve apra concatenar comandos, es decir, se ejecuta uno después del otro
- `cat [opciones] archivo.ext`
	* Su uso es concatenar (unir, sumar) archivos e imprimirlos en una salida estandard
	* `-A` : Mostrar todo
	* `-b` : Omitir los números de línea para los espacios en blanco en la salida
	* `-e` : Un caracter _$_ se mostrará al final de cada línea anterior a una nueva línea
	* `-E` : Muestra un _$_ al final de cada línea
	* `-n` : Numera todas las líneas
	* `-s` : Si la salida tiene múltiples líneas vacías las sustituye con una única línea vacía
	* `-T` : Muestra los caracteres de tabulación, se imprimen como `^I`
	* `-v` : Mostrar los caracteres no imprimibles
	* `cat > archio.ext` : Se crea el archivo y se puede escribir en él. Cuando se haya terminado, presionar `CTRL + D` para salir del archivo
	* `cat archivo.ext | more` : Para evitar desplazarse por archivos muy grandes. También con `| less`
	* `cat *.ext` : mostrar el contenido de todos los archivos con la extensión especificada
	* `cat archivo1.ext archivo2.ext > archivoDestino.ext` : Se redirige la salida de los archivos al fichero destino. Si el archivo de destino no existe, el comando lo creará o sobrescribirá uno existente con el mismo nombre
	* `cat archivo.ext >> archivoDestino.ext` : Agrega el contenido del archivo origen al ya existente del fichero destino
	* `tac archivo.ext` : Ver el contenido de un archivo en orden inverso, comenzando con la última línea y terminando con la primera
- `find rutaABuscar [opciones]`
	* `find /ruta -name "texto"`
	* `find . -iname "texto"`
	* `find /users -iname "github" -type d`
	* `find /ruta -mtime +3`
	* `find /ruta -user alejandro`
		+ `.` : buscar en directorio actual
		+ `-name`: flag, busca el nombre del archivo o algún patrón de búsqueda
		+ `-iname`: flag para buscar ficheros con case insentitive
		+ `texto`: nombre.ext , *.ext , nombre
		+ `-type`: flag para indicar el tipo del fichero seguido del indetificador del fichero
			- `d` : directorio
			- `f` : fichero
			- `l` : enlace simbólico
		+ `-mmin | -mtime` : flags para buscar elementos modificados hace X minutos o días, respectivamente
			- `+/-` : modificadores para encontrar ficheros modificados hace más de X tiempo o menos de X tiempo, respectivamente
		+ `-user | -group` : flags para buscar usuarios o grupos
		+ `-size` : flag para buscar archivos por tamaño, seguido de valor numérico con prefijo de tamaño:
			- `c` : bytes
			- `k` : kilobytes
			- `M` : megabytes
			- `G` : gigabytes
			- También se pueden usar los modificadores `+/-`
- `grep [options] pattern archivo`
	* *Global Regular Expression Print*, se utiliza para hacer coincidir e imprimir un patrón de búsqueda o una expresión regular de uno o varios archivos de texto.
	* Buscará el patrón en los archivos, si coinciden, imprimirá el resultado en pantalla o en un archivo de salida.
	* `grep palabra ejemplo.txt test.txt`
		+ Busca las coincidencias con "palabra" en esos dos archivos
	* `grep palabra *.*`
		+ Busca "palabra" en todos los archivos con cualquier nombre o extensión
	* `grep palabra file > salida.txt`
		+ Las coincidencias de búsqueda las guarda en el fichero salida.txt
    * `-c` : Cuenta el número de coincidencias
    * `-E` : Expresión regular extendida
    * `-f` : Obtiene el patrón o los patrones de búsqueda de un fichero (Uno por cada línea)
    * `-i` : Insensible a mayúsculas y minúsculas
    * `-l` : Imprime el nombre de cada fichero de entrada donde se encuentren coincidencias
    * `-n` : Imprime el número de línea en donde se encuentren coincidencias
    * `-o` : Imprime sólo la parte que coincide
    * `-v` : Invierte el sentido de la búsqueda
    * `–color` : Resalta la palabra que coincide con el color especificado en la variable de entorno `GREP_COLOR` (rojo por defecto)
    * `-r,-R` : Busca coincidencias en todos los ficheros que se encuentran debajo de un directorio, incluyendo los subdirectorios
	* `grep query1 file | grep query2 file` || `grep -E 'query1|query2' file`
- `tail [opciones] archivo`
	* Imprime los últimos N números o colas (tails) de una entrada. Por lo general, muestra o imprime los últimos 10 números del archivo que se le proporcionó
	* `-n N` : muestra las últimas N líneas del archivo.
	* `+n N` : comienza a mostrar el archivo en el renglón N
	* `–c C` : escribe los últimos N bytes del archivo
	* `-f` : muestra las últimas 10 líneas del archivo y lo supervisa para ver las actualizaciones; la cola continúa generando nuevas líneas que se agregan al archivo monitoreado.
- `file [opciones] archivo`
	* Es una utilidad que realiza una serie de pruebas (test) para determinar el tipo y formato de un archivo. Se detallan a continuación dichas pruebas, en el orden en que se llevan a cabo por este comando:
	1. Sistema de archivos: se intenta determinar si el archivo a examinar es un archivo del sistema por medio de la función (system call) stat. Gracias a esta prueba se puede determinar si es un dispositivo, enlace simbólico, una tubería, etc.
    2. Número mágicos: Se intenta determinar el tipo, analizando determinados bytes ubicados en específicas posiciones dentro del archivo. Estos bytes se los denomina números mágicos, y suelen estar al comienzo de la cabecera. La información para realizar dicho análisis figura en el archivo /usr/share/misc/magic.mgc.
    3. Prueba de sintaxis: esta última prueba consiste en determinar que tipo de sintaxis posee un archivo de texto. Esta prueba solo se realiza sobre los archivos que se haya determinado que sean texto plano.
	* `-d` : Realiza las pruebas de sintaxis y de números mágicos del sistema. Esta es la opción default
	* `-h` : Si el archivo a analizar es un enlace simbólico, lo identifica como tal
	* `-m` : Realiza una prueba adicional de números mágicos con el archivo indicado
	* `-M` : Similar a `-m`, salvo que no realiza las pruebas de sintaxis y de números mágicos por defecto del sistema
	* `-b` : No imprime el nombre del archivo en cada resultado
	* `-i` : Muestra el tipo mime junto con la codificación utilizada
	* `-f` : el archivo contiene una lista de los archivos a examinar
	* `-p` || `--preserve-date` : conserva la fecha de último acceso del fichero
	* `--mime-type` : similar a `-i`, salvo porque solo muestra el tipo mime
	* `--mime-encoding` : averiguar la codificación de caracteres con que fue guardado un archivo
	* `-z` : Examina los archivos comprimidos.
	* `-e prueba` : Excluye de realizar la prueba indicada
        + `apptype` : Tipo de aplicación EMX (solo para EMX)
        + `ascii` : Esta prueba intenta determinar la codificación, más allá de la indicada dentro del propio archivo.
        + `encoding` : Varios tipos de codificaciones para la prueba suave de números mágicos
        + `tokens` : Busca cadenas conocidas dentro de los archivos de texto
        + `cdf` : Muestra detalles de los archivos CDF (Compound Document Files). Por ejemplo SVG, XHTML, etc
        + `compress` : Analiza y busca dentro de los archivos comprimidos
        + `elf` : Muestra detalles de archivos ELF
        + `soft` : Consulta de archivos mágicos
        + `tar` : Analiza archivos Tar
	* `file ruta/archivo` || `file ruta/*`
	* `file -f Listado-de-archivos.txt`
	* `file [a-g]*` : analizar los ficheros cuyo nombre empiece desde _a_ hasta _g_
	* `file ruta/* | grep palabra` : se analiza todos los documentos que hay en esa path, el comando grep los filtra por lo que contengan la _palabra_ indicada
- `iconv [options] -f codificacionOrigen -t codifDestino archivo.ext`
	* Es utilizado para cambiar la codificación de un archivo de texto
	* `-l` : Lista todas las codificaciones de juegos de caracteres conocidos
	* `-c` : Desechar los caracteres que no se pueden convertir en lugar de terminar el proceso
	* `-verbose` : Imprimir la información del progreso de error estándar al procesar varios archivos
	* `-o archivoSalida.ext` || `–output=archivoSalida.ext` : Para tener un archivo de salida
	* `//IGNORE` : se agrega después de la codificación destino, los caracteres que no se pueden convertir se descartan y se imprime un error después de la conversión
	* `//TRANSLIT` : se agrega después de la codificación destino, los caracteres que no se pueden representar en el conjunto de caracteres de destino, se puede aproximar a través de uno o varios caracteres similares
- `tar [opciones] /ruta/fichero.gtar ruta/carpeta`
	* Significa _Tape Archive_, lo que en español sería archivo de cinta de grabación, y se utiliza para comprimir y descomprimir una colección de archivos y carpetas
	* `-c` : Crear un nuevo archivo .tar
	* `-v` : Muestra una descripción detallada del progreso de la compresión
	* `-f` : Nombre del archivo
	* `-z` : Compresión gzip, la extensión del archivo de salida será _.tar.gz_ o _tgz_
	* `-j` : Compresión bzip2
	* `-C` : Extraer archivos en un directorio diferente
	* `-x` : Extraer el archivo
	* `-r` : Actualizar o agregar un archivo o directorio en un archivo .tar existente
	* `-t` : Lista el contenido del fichero .tar
	* `tar -cvf archivo.tar /ruta/irectorio` : comprimir una carpeta mientras se ve el progreso del proceso
	* `tar -xvf archivo.tar` : descomprimir un archivo .tar mientras se muestra el progreso del proceso
	* `tar -cvf output.tar /rutaEntrada1 /rutaEntrada2 /rutaEntrada3` : comprimir varios archivos y/o carpetas
	* `tar -rvfarchivo.tar example.ext` | `ruta/directorio` : Agregar un archivo o directorio a un comprimido ya existente
	* `tar -cvf archivo.tar /ruta/entrada –exclude = /ruta/*.ext -exclude = /ruta/directorio-excluido` : Comprimir los archivos y carpetas de la entrada, pero exluir todos los archivos _.ext_ y excluir también, el directorio señalado
	* `tar -xvf archivo.tar -C /nuevaRuta` : descomprimir un archivo en un directorio diferente
	* `tar -xvf archivo.tar example.ext` : extraer un único archivo del comprimido
	* `tar -xvfarchivo.tar file1 file2` : extraer multiples archivos de un comprimido
	* `tar -tf archivo.tar` : listar el contenido del archivo comprimido, alternativamente agregar opcion `v` para ver más detalles
- `uname [opciones]`
	* Proviene de la abreviatura _Unix Name_ y es una herramienta para mostrar información del sistema operativo como la versión del mismo, kernel y detalles del equipo entre otras posibilidades.
	* `-s` : Muestra el tipo de núcleo, por ejemplo Linux
	* `-p` : Muestra el tipo del procesador, en caso de no conocerse mostrará _unknown_
	* `-m` : Muestra la arquitectura del procesador: x86 para 32 bits y x86_64 para 64 bits
	* `-n` : Muestra el nombre que le hemos dado al equipo para la red, si no lo cambiamos será el que le dimos en la instalación de nuestra distribución. Este nombre se toma de /etc/hostname por lo que podemos cambiarlo en este archivo
	* `-o` : Devuelve el Sistema Operativo que estamos usando, suele detectar como GNU/Linux en las distribuciones que he comprobado
	* `-r` : Muestra la información del kernel que tenemos en uso, si reiniciamos y usamos otro kernel cambiará al ejecutar este comando
	* `-v` : Se utiliza para conocer la fecha en la que se publicó el kernel que tenemos en uso a este instante
	* `-i` : Muestra la plataforma para el hardware, siempre vi que devolviera “unknown”
	* `-a` : Hace referencia a _all_, mostrando toda la información de las opciones anteriores

- ### Alias
- `alias nombreAKA = 'comando'` 
    * Permite crear un atajo a un comando o grupo de comandos para facilitar la escritura en la terminal
    * Al cerrar sesión, los alias se eliminan, no son persistentes!
    * Para hacerlo ir a direcotrio `/root` y agregar los alias en el fichero `.bashrc`
- `alias`
	* Lista los alias guardados

- ### Variables de entorno
    Variables que contienen valores que pueden ser utilizadas por diferentes programas, ayudan a los programas a realizar sus funciones
- `echo $variable`
	* Ver contenido de la va
- `variable PATH`
    * Identifica rutas de archivos que tienen la capacidad de ejecutarse (bin's!)
	* Si alguna ruta no está en PATH, podemos agregar la ruta absoluta a la va
- `SHLVL`
	* Nivel de profundidad del bash
	* `bash` : crea un nivel de shell
	* `exit` : sale del nivel shell
- `NOMBRE = valor`
	* Crear va de entorno
    * Para persistir las va de entorno, agregarla en fichero:
	    + `/etc/profile` : para todos los usuarios
	    + `$HOME/.bashrc` : para todos los shells, incluyendo shell de inicio

- `useradd -m nombreUsuario`
	* Crear usuarios
- `useradd -g nombreGrupo nombreUsuario`
	* Crea usuario y crea grupo
- `userdel nombreUSer`
	* Eliminar usuarios

- ### grupos de usuario
    Reunir personas que comparten los mismos privilegios de configuración o acceso
- `groupadd nombreGrupo`
	* Crear nuevo grupo
- `groupdel nombreGrupo`
	* Eliminar grupo
- `group`
	* Lista los grupos existentes

- `usermod -G nombreGrupo usuario`
	* Agregar usuario a un grupo
- `adduser nombreUsuario sudo`
	- Otorgar permisos de superusuario

- ### Permisos
    El esquema de permisos se trabaja en el sistema octal (bloques de 3 bits), se separa en permisos de propietario, grupo y otros
	* Si empieza con `d` es un directorio
	* Si empieza con `-` es un fichero
	* `r` : 4 (read), `w` : 2 (write), `x` : 1 (execute)
	* [d/-] [bits propietario] [bits grupo] [bits otros]

- `chown nombreUsuario archivo.ext`
	* Cambiar el propietario del archivo
- `chown root:nombreGrupo archivo.ext`
	* Cambiar a otro grupo el archivo
- `chmod permisos archivo.ext`
	* Cambiar el nivel de alcance de un fichero, los permisos son valor numerico!
    * 3 digitos: para propietario, grupo y otros

---

#### Notas si se trabaja con una maquina virtual de AWS

- `sudo sshd_config`
	* Abrir y configurar el servicio Daemon (demonio)
- `sudo service ssh restart`
	* Reiniciar servicio

Al enlazarse con la MV, y evitar que  se desconecte al no ver actividad usar:
- `ssh -o TCPkeepAlive=yes -o ServerAliveInterval=100`

Para habiliar el poder hacer ping a la MV, ir al panel de AWS
- click en maquina > inbound > edit > addruk
	* all ICMP IPV4