# Estructura de directorios

- raiz `/` 
    * Directorio de jerarquía primaria, origen de todo
- `/bin` 
    * Directorio estático, se almacenan archivos binarios/ejecutables necesarios para el funcionamiento del sistema
	* No puede contener subdirectorios!
- `/boot` 
    * Archivos necesarios para arrancar el sistema
- `/dev` 
    * Dispositivos de hardware como si fueran ficheros!
    * Dichos dispositivos son unidades de discos permanentes
- `/etc` 
    * Ficheros de configuración estáticos
		+ `/apt` Gestor de paquetes
		+ `/opt` Configuraciones de apps que se instalaron
		+ `/x11` Sistema de ventanas
- `/home` 
	* Directorio variable , contiene info de los usuarios registrados en el SO
- `/lib` 
    * Es estático, contiene bibliotecas necesarias para correr ejecutables de /bin
- `/mnt` 
    * Almacena los puntos de montajes de diversos dispositivos (temporales)
- `/media` 
    * Montar pendrives o unidades CD, parecido a `/mnt`
- `/opt` 
    * Es estático, almacena progrs que instala el usuario
- `/pro` 
	* Guarda el sistema e archivos virtual
	* Brinda info de los procesos y apps que se están ejecutando en el SO (en RAM)
- `/root` 
	* Es variable y compartido con los usuarios registrados
	* No se encuentra en `/home`!
- `/sbin` 
	* Es estático y compartido
	* Contiene binarios que solo pueden ser ejecutados por el usuario root!
- `/srv` 
	* Almacenar directorios y datos que utilizan los servidores instalados
	* P.Ej. Apache, ftp, etc.
- `/tmp` 
	* Para archivos temporales
    * Se borran al cerrar sesión, apagar la maáquina o de acuerdo a la configuración de las apps que lo generaron
- `/var` 
	* Es compartido y dinámico
	* Contiene datos y datos temporales como log del SO, log de apps, estado de apps, tareas pendientes