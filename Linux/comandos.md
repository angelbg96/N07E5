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
		+ *TERM* puede ser pasada al proceso mediante `-15`
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
- `cd ..`
	* Regresar un directorio atrás
- `cd /`
	* Ir a raiz
	* La `/` siempre es respecto a la raiz!
	* Sin la barra y se coloca una ruta, se mueve hacia subdirectorios
	* `./` Relativo al directorio actual
	* `../` Directorio superior
- `ls`
	* list, listar directorios dentro del directorio donde se esté posicionado
- `ls {opciones} {directorio}`
- `ls *.extension`
	* Listar archivos con extensión especificada
- `ls -lah`
	* Listar con un formato legible
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
- `touch nombreArch.ext`
	* Crear un archivo
- `nombreApp nombreArch.ext`
	abrir archivo con un programa instalado. p.ej. _nano_
- `history`
	* Muestra historial de comandos ejecutados
- `rm nombreArch.ext`
	* Eliminar un archivo
- `rm -R directorio/`
	* Elimina archivos de un directorio y la carpeta misma
- `cp rutaArchivo rutaCopia`
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
- `find rutaABuscar {opciones}`
- `find /ruta -name "texto"`
- `find . -iname "texto"`
- `find /users -iname "github" -type d`
- `find /ruta -mtime +3`
- `find /ruta -user alejandro`
	* `.` : buscar en directorio actual
	* `-name`: flag, busca el nombre del archivo o algún patrón de búsqueda
	* `-iname`: flag para buscar ficheros con case insentitive
	* `texto`: nombre.ext , *.ext , nombre
	* `-type`: flag para indicar el tipo del fichero seguido del indetificador del fichero
		+ `d` : directorio
		+ `f` : fichero
		+ `l` : enlace simbólico
	* `-mmin | -mtime` : flags para buscar elementos modificados hace X minutos o días, respectivamente
		+ `+/-` : modificadores para encontrar ficheros modificados hace más de X tiempo o menos de X tiempo, respectivamente
	* `-user | -group` : flags para buscar usuarios o grupos
	* `-size` : flag para buscar archivos por tamaño, seguido de valor numérico con prefijo de tamaño:
		+ `c` : bytes
		+ `k` : kilobytes
		+ `M` : megabytes
		+ `G` : gigabytes
		+ También se pueden usar los modificadores `+/-`
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

- `chown nombreUsuario nombreArchivo.ext`
	* Cambiar el propietario del archivo
- `chown root:nombreGrupo archivo.ext`
	* Cambiar a otro grupo el archivo
- `chmod permisos fichero`
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