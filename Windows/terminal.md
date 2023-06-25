# Windows Terminal

- Se descarga de Microsoft Store
- Las configuraciones se realizan en su archivo `settings.json`


## Substistema de Linux
- Activar el WSL y la virtualización en el menú de *características de Windows*
- Instalar la distro que se desee en *Microsoft Sotre*
- con PowerShell ejecutar `wsl -l -v` para revisar la versión instalada de WSL
- Para elegir la versión 2 WSL, con powershell ejecutar `wsl --set-default-version 2`
    - Pedirá la instalación del paquete del Kernel de WSL2 y muestra URL de documentación y descarga
    - Ejecutar nuevamente el comando para establecer por defecto WSL2
    - Si las distros no se actualizan para trabajar con la versión del kernel, ejectuar `wsl --set-version nombreDistro 2`
- Para limitar el consmo de RAM:
    - En la ruta `c:\Users\nombreUsuario`, crear fichero *.wslconfig*
    - colocar la siguiente configuración para  limitar el uso a 2GB
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
- En el elemento *Profiles* > *list* agregar
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
- Para cambiar las configuraciones generales modificar el elemento *defaults*:
~~~ json
    "useAcrylic": true, // Usar transparencia
    "acrylicOpacity": 0.6, // Porcentaje de opacidad
    "fontSize": 12,
    "fontFace" : "Consolas",
    "startingDirectory" : "D:\\angel\\Documents"
~~~
- O en su caso, realizar modificaciones por cada perfil (terminal)
- Instalar un prompt
    - Ir al sitio web oficial de [Oh My Posh](https://ohmyposh.dev/docs/) para descargar los paquetes de acuerdo al SO y visualizar los temas disponibles
    - Utilizar una tipogrfía de [Nerd Fonts](https://www.nerdfonts.com/font-downloads)
    - Los [temas predeterminados](https://ohmyposh.dev/docs/themes) se descargan a la PC, se debe elegir uno o bien, personalizar un prompt a su gusto (archivo *.omp.json*)
    - Powershell
        - Para aplicar el tema elegido a la terminal se ejecuta: `oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\NombreTema.omp.json" | Invoke-Expression`
        - Guardar comando en la configuración del perfil con `notepad $PROFILE` y refrescar configuración de terminal con `. $PROFILE`
        - **Nota**. Si aparece un error de que no se pueden ejecutar scripts en el equipo, aplicar una exepción de politicas de acuerdo a la [documentacion de Microsfot](https://learn.microsoft.com/es-mx/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.3)
            - Se aplica la política ejecutando powershell con permisos de administrador `Set-ExecutionPolicy -ExecutionPolicy TipoPolitica -Scope AlcancePolitica`
            - P.ej. `Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope LocalMachine` (No usar a menos de estar consiente del riesgo que implica la política y alcance usados en el ejemplo)
    - Linux
        - Los temas se descargan por default en la carpeta de root, por lo que para permitir acceso al usuario se deben seguir los siguientes pasos (omitir si se descargaron en otra ruta o si es tema personalizado):
            - Instalar `setfactl` si no existe `sudo apt install acl`
            - Agregar facultades al usuario especificado `sudo setfacl -m user:NombreUsuario:rx /root` y `sudo setfacl -m user:NombreUsuario:rx /root/themes/*`
        - Ejecutar comando para aplicar tema a la terminal `eval "$(oh-my-posh init bash --config /ruta/themes/NombreTema.omp.json)"`
        - Guardar configuración en archivo `~/.profile`


## Atajos de teclado
- Cerrar una ventana `ctrl shift w`
- Clonar panel actual `alt shift D`
- Crear subventana a lado | abajo `alt shit +` | `-`
- Cambiar tamaño de la ventana `alt shift ←`| `↑` | `→` | `↓`
- Abrir una nueva ventana de acuerdo a su consecutivo en el menú de terminales `ctrl shift n`, n: 1, 2, ...
- Navegar entre pestañas `ctrl shift tab` || `alt ←`| `↑` | `→` | `↓`
- Crear un panel de otra terminal en panel actual `click alt panel`
