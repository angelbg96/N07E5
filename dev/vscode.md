# Configuraciones de Visual Studio Code

## Extensiones
- __Better Comments__, _Aaron Bond_ : Escribir comentarios que resultan visualmente más facil de leer y más descriptivos
- __Bracket Pair Colorizer__, _CoenraadS_ : Colorear los pares de paréntesis, llaves y corchetes
- __Live Server__, _Ritwick Dey_ : Servidor local para levantar proyectos web
- __MinifiAll__, _Jose Garcia Berenguer_ : Minimizar código fuente en diferentes lenguajes de programación, muy útil para desarrollo web
- __open in browser__, _TechER_ : Abrir el archivo actual en el navegador
- __simple icons__, _Laurent Tréguiler_ : Iconos para visualizar los archivos fuente de distintos lenguajes
- __SonarLint__, _SonarSource_ : Reglas para seguir buenas prácticas de desarrollo en diferentes lenguajes
- __Thunder Client__, _Ranga Vadhineni_ : Cliente para solicitudes HTTP, es una GUI
- __Go__, _Go Team at Google_ : Herramientas para soporte de Golang


## Configuraciones
- Trabajar sobre un Workspace
    * Al iniciar por primera vez VScode, crear archivos y/o inicializar algún proyecto
    * File > Save Workspace As... > Elegir nombre y ruta del workspace
    * File > Open Workpace > Buscar el workspace recientemente creado
    * Se almacenarán las configuraciones del editor, además de que se pueden agregar carpetas al espacio de trabajo, que podrían ser los proyectos sobre los que se están trabajando
- Preferencias
    * File > Preferencias > Se visualizan las distintas preferencias como:
    * Activar auto guardado
    * Estilo del cursor : line
    * Cursor blinking, parpadeo del cursor : Expand
    * Tamaño de letra en pixeles: 16
    * Familia de la fuente, se elige la default y sus fallback : 'Fira Code', consolas, monospace
    * Ligaduras de fuente : true
    * Ancho de la fuente : 300
    * Minimap, vista general del código en una columna lateral : descativado
    * Tamaño de la sangría : 4
    * Insertar espacios al teclear `Tab`  : Activado
    * Desbordamiento a líneas extensas (Wrapping) : Desactivado
    * Asociar extensiones de archivos a algún lenguaje
    * Color Theme : Dark
    * Icon Theme : Seleccionar el paquete de íconos favorito
- Configurar Terminal
    * Configuraciones > Settings > Buscar "_Shell_"
    * Seleccionar la opción _Terminal > Integrated > Shell : Windows_
    * Colocar la ruta a la shell por default a utilizar
    * Abrir Paleta de comandos : Configuración > Paleta de comandos | CTRL + SHIFT + P
    * Buscar : Reload Window (CTRL + R)
- Atajos de teclado
    * Visualizar los atajos configurados y agregar nuevos
    * Ej. agregado : Buscar "_wrap_", seleccionar _Emmet wrap with abbreviation_, asignarle una confugiración de teclas


## Keyboard Shortcuts
- `alt + flecha up/down` : mueve bloque de código
- `click + alt` : multicursores
- `ctrl + alt + flecha up/down` : multicursores a nivel de esa columna
- `ctrl + D` : selección mútiple de coincidencias con código enmarcado
- `ctrl + F2` : seleccionar todas las ocurrencias
- `ctrl + shift + k` : borra línea de código (no seleccionar texto, solo cursor en línea)
- `ctrl + }` : comentar bloque de código
- `ctrl + i` : encerrar bloque de código con etiqueta HTML con notación Emmet
- `alt + z` : ver código con/sin desbordamiento
- `F2 en nombre de etiqueta HTML ` : renombra el par de etiquetas
- `ctrl + space` : muestra intellisense
- `ctrl + click en archivo` : abrir archivo en otro panel

## Emmet
- `etiq.class.class2` : elemento al que se le asignan dos clases "class class2"
- `etiq#idEtiq` : elemento al que se le asigna el id "idEtiq"
- `etiq > etiq` : contendor e hijo
- `etiq + etiq` : elementos hermano
- `etiq[atrib="valor"]` : elemento al que se especifica un atributo
- `etiq{texto}` : elemento al que se le especifica su contenido
- `etiq{Item $}*n` : elemento el cual se va a colocar 'n' veces y su contenido tendrá una numeración de 1 a 'n'
- `etiq{Item $@x}*n` : elemento el cual se va a colocar 'n' veces y su contenido tendrá una numeración de 'x' a 'x+n'
- `(etiq>etiq.class)*n` : estructura contendor - hijo colocado 'n veces'
- `etiq1>etiq^etiq2` : sube un nivel de bloque, etiq2 es hermano de etiq1
- ej: nav>ul>li*5>a\[href="#"\]{Item $} : la barra de navegación tiene 5 elementos "li", que contiene un elemento "a" y su texto es Item índice




