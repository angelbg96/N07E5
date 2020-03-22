# Comandos de consola PowerShell

- Es una shell de línea
- Es más que CMD, tiene un entorno completo de scripting!
- Se pueden abrir aplicaciones escribiendo su nombre desde el shell!
- Tiene autocompletado, al escribir parte de un comando y luego TAB, se autocompleta, y si se sigue presionando TAB, muestra otras coincidencias con el escrito
- Se puede arrastar una carpeta al shell y se copiará la ruta!

---
-  `get-host`
	* Versión del shell con la que se trabaja
- `get-command *-service`
	* Muestra los servicios disponibles
- `get-help nombreServ`
	* Especificaciones de un servicio en particular
- `function prompt {"nombrePerso >"}`
	* Cambiar nombre al prompt, en vez de mostrar la ruta de ejecución, muestra ese nombre
- `cls` || `clear`
	* Limpiar ventana
- `ipconfig`
- `dir` || `ls`
	* Muestra contenido de un directorio
- `date`
	* Muestra fecha y hora
- `pwd`
	* Conocer la ruta donde me encuentro
- `pushd`
	* Guardar alguna ruta
- `popd`
	* Ir a la ruta que se guardó
- `mkdir nombre`
	* Crea un directorio en la ruta donde te encuentres y con el nombre especificado
- `ni` || `New-Item nombre.ext`
	* Crea un nuevo fichero vacio
- `echo` || `Write-Output` `"cadena de texto" > archivo.ext`
	* Crear archivo y escribir la cadena de texto en su contenido
- `cd ..`
	* Ir a un directorio superior

---
### Ejecutar como admin
- `Get-WindowsDriver -oneline -All`
	* Muestra drivers instalados en la consola
- `Get-WindowsDriver -oneline -All | Out-GridView`
	* Muestra drivers instalados en una ventana de diálogo con detalles del mismo
- `export-windowsdriver -online -destination c:\ruta`
	* Respalda drivers en esa ruta

---
### Gestionar procesos de windows
- `get-process`
	* Muestra los procesos que se están ejecuando
- `get-process -?`
	* Muestra mas detalles de los procesos
- `start-process nombre.ext`
	* Ejecutar un proceso
- `stop-process -name nombreProc`
	* Detener un proceso
- `get-process -name nombreProceso`
	* Obtener info de un proceso determinado. cada proceso tiene un ID!
- `get-process -ID id`
	* Obtener infor de un proceso por su ID
- `get-process -name letras*`
	* Obtener info de los procesos que empiecen con las letras especificadas

---
### Alias
- `get-alias`
	* Obtener los equivalentes de alias vs comando
- `alias nombreAKA`
	* Muestra el nombre completo del comando
- `New-Alias`
	* Crear un nuevo alias, al dar enter, el shell pedirá que se agregue un nombre al alias y su respectivo comando al que será equivalente
- `New-Alias -Name nombreAKA comandoEquivalente`
    * Agregar un nuevo alias
- `Get-Alias -Name letras*`
	* Obtener listado de alias que empiecen con las letras especificadas
- `Get-Alias -Name letras* -Exclude letras2*`
	* Listado de alias que empiecen con *letras* pero excluir los alias con coincidencia de *lestras2*
	* ej: `Get-Alias -Name s* -Exclude sl*`
        + Obtén alias que empiecen con *S* y excluye los que seguido de *S* sea un caracter *L*
- `Get-Alias -Name letras*, letras2*`
	* Dos consultas que empiecen con esos dos conjuntos de letras
- `Get-Alias -Name *letras*`
	* Alias con letras en cualquier parte del nombre

---
### Operaciones matemáticas
- (+ , -, *, /, % (porcientos)) con num enteros y decimales!
    * ej: 10%100 -> 10% de 100!
- se pueden trabajar con hexadecimal! anteponiendo 0X al numero!
- operaciones en Bytes! KB, MB, GB!
    * ej: 0x45 + 1KB
- `[system.math]::sqrt(x)`
	* Hacer raíz cuadrada
- `$nombre = valor`
	* Crear variable
- `$nombre`
	* Muestra contenido de la variable

---
### Respaldar información
- respaldo total -> no omite carpetas ni archivos! verificar que carpeta destino esté vacio 
- incremental -> archivos que se hayan modificado o nuevos archivos se van a agregar al respaldo
- `ROBOCOPY rutaOrigen rutaDestino`
	* Respaldo basico
- `ROBOCOPY rutaOrigen rutaDestino /MIR`
	* Incluye subdirectorios y archivos dentro de ellos
	* Al agregar un archivo o editar un archivo del directorio origen y se aplica este último comando, se copiarán solamente los modificados y los nuevos, los otros se verán omitidos.
	* Al final de la actualización del respaldo, mostrará detalles sobre la tansferencia
- `ROBOCOPY rutaOrigen rutaDestino /MIR /MOV`
	* Mover contenido del directorio! la carpeta origen se elimina al no tener contenido :)
- `ROBOCOPY rutaOrigen *.ext* rutaDestino /MIR /S`
	* Copia los archivos con la extensión especificada y omite carpetas vacias
- `ROBOCOPY rutaOrigen *.ext* rutaDestino /MIR /E`
	* Copia archivos con la extensión especificada y considera carpetas vacias
- `ROBOCOPY rutaOrigen rutaDestino /MIR /V`
	* Copia archivos y al final, muestra los detalles de los archivos copiados
- `ROBOCOPY rutaOrigen rutaDestino /MIR /V /PURGE`
	* Cuando en origen se eliminó un archivo, se suprimirá en destino y hará las actualizaciones de archivos correspondientes (nuevos arch o modificados)
- `ROBOCOPY rutaOrigen rutaDestino /MIR /V /XD "rutaDirOmitido"`
	* Copiar archivos a carpeta destino y omitiendo la carpeta especificada en las comillas
- `ROBOCOPY rutaOrigen rutaDestino /MIR /V /R:numero`
	* Copiar archivos, en dado caso que algún archivo arroje un error debido a que está siendo utilizado por una app u otro caso, hará la copia X cantidad de intentos, si lo supera, lo omite y muestra advertencia
