# Windows Terminal

- Se descarga de Microsoft Store
- Las configuraciones se realizan en su archivo `settings.json`


## Substistema de Linux
- Activar el WSL y la virtualización en el menú de _características de Windows_
- Instalar la distro que se desee en _Microsoft Sotre_
- con PowerShell ejecutar `wsl -l -v` para revisar la versión instalada de WSL
- Para elegir la versión 2 WSL, con powershell ejecutar `wsl --set-default-version 2`
    * Pedirá la instalación del paquete del Kernel de WSL2 y muestra URL de documentación y descarga
    * Ejecutar nuevamente el comando para establecer por defecto WSL2
    * Si las distros no se actualizan para trabajar con la versión del kernel, ejectuar `wsl --set-version nombreDistro 2`
- Para limitar el consmo de RAM:
    * En la ruta `c:\Users\nombreUsuario`, crear fichero _.wslconfig_
    * colocar la siguiente configuración para  limitar el uso a 2GB
    ~~~ go
    [wsl2]
    memory=2048MB
    swap=0
    localhostForwarding=true
    ~~~


## Terminales que emulan comandos Linux
- Git Bash
- Cmnder
- Cygwin


## Configuraciones de Windows Terminal

### Agregar una nueva terminal
- Con PowerShell ejecutar `[guid]::NewGuid()`, genera un ID paa agregar al archivo de configuraciones
- En el elemento _Profiles_ > _list_ agregar
~~~ json
{
    "guid": "{ID generado}",
    "hidden": false,
    "name": "Nombre Bash",
    "tabTitle": "Nombre Bash a visualizar en las tablas",
    "commandline": "\"D:\\rutaBash\\bash.exe\"",
    "icon": "D:\\rutaIcono\\icono.ico"
},
~~~
- Si se quiere cambiar la bash por defecto, modificar:
~~~ json
"defaultProfile": "{ID bash}",
 ~~~

### Cambiar presentación
- Para cambiar las configuraciones generales modificar el elemento _defaults_:
~~~ json
    "useAcrylic": true, // Usar transparencia
    "acrylicOpacity": 0.6, // Porcentaje de opacidad
    "fontSize": 12,
    "fontFace" : "Consolas",
    "startingDirectory" : "D:\\angel\\Documents"
~~~
- O en su caso, realizar modificaciones por cada perfil (terminal)
- Instalar un prompt
    * Ir al sitio web oficial de [Oh My Posh](https://ohmyposh.dev/docs/)
    * Utilizar una tipogrfía de [Nerd Fonts](https://www.nerdfonts.com/font-downloads)
    * Powershell
        - `Get-PoshThemes` : Listar temas de terminal
        - `Set-PoshPrompt -Theme nombreTema` : Establecer tema a la terminal
        - Powershell: Guardar tema en el perfil del la terminal `notepad $PROFILE`
    * Linux
        - Seguir procedimiento de documentación
        - Guardar configuración en archivo `~/.profile`


## Atajos de teclado
- Cerrar una ventana `ctrl shift w`
- Crear subventana a lado | abajo `alt shit +` | `-`
- Cambiar tamaño de la ventana `alt shift ←`| `↑` | `→` | `↓`
- Abrir una nueva ventana de acuerdo a su consecutivo en el menú de terminales `ctrl shift n`, n: 1, 2, ...
- Navegar entre pestañas `ctrl shift tab`

