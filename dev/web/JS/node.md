# Node JS

## Instalación
En caso de tratarse de una instalación manual en Windows, seguir los pasos que serían similares a instalación en Linux
~~~ bash
NODE_HOME=/ruta/node/v_x.y
# NPM normalmente se encuentra en carpeta roaming
NPM_HOME=/ruta/npm/v_x.y

export PATH=$PATH:$NODE_HOME:$NODE_HOME/bin:$NPM_HOME
# opcionalmente (por si no funciona correctamente Node) agregar tambien
export PATH=$PATH:$NODE_HOME/node_modules
~~~

## Fundamentos Teoricos
- Se ejecuta a través del motor V8 de Chrome, que interpreta el código JS para convertirlo en  lenguaje máquna (Bytecode). Está escrito en C++
    - Funcionamiento:
    - Genera un entorno Global
        - Genera el objeto global, en el navegador es `window`
        - Genera la variable `this`, depende del contexto donde se esté llamando. por default su valor es `windows`
        - Contexto de ejecución: Ejecuta el código JS a través de un stack de tareas.
    - Interacción V8 con Navegador
        - Parseo: Busca en el documento JS las *keywords* del lenguaje
        - AST (Arbol de Sintaxis Abstracta) : JS genera un arbol sintáxico del documento para que después lo pueda interpretar en el navegador
        - Interpretar: Genera código Bytecode. Si el intérprete se da cuenta que hay código que se puede optimizar, un Profiler (monitor) lo intenta refactorizar, lo compila y regresa el bytecode optimizado
    - Hoisting : Es el proceso que realiza el motor de JS de colocar las declaraciones de variables y funciones hasta arriba de nuestro código, almacenándolas así previamente en memoria dentro de un contexto de ejecución. El motor de JS intenta ayudar en la optimización del código, que por malas práticas puede ocasionar errores en la ejecución del código. Sucede con variables y funciones
        - Si se llama una variable antes de ser declarada, el compilador crea la variable en la *memory heap* y la inicializa como *undefined*
        - Con las funciones, primero se llaman a las funciones antes de ejecutarlas.
        - El hoisting funciona pero no se tiene el control de las variables que se van a cambiar
        - Si se llama a una constante (const) antes de inicializar retorna un error de tipo: *Uncaught ReferenceError*, que corresponde a variables que son referenciadas pero no pudieron ser capturadas
    - Ejecución:
        - JS solo puede ejecutar una tarea a la vez
        - *Memory Heap* : Es el espacio de memoria donde se guardan objetos y funciones en bloques de memoria de forma arbitraría y sin un orden, los cuales pueden ser usados múltiples veces a través de una referencia única.
        - *Call Stack* : Espacio de memoria que apila las tareas (llamados a funciones) una tras otra (LIFO). Se ejecuta una tarea a la vez y al terminar, se quita del stack
        - *Garbage Collection* : Cuando hay elementos que ya no se están llamando, el *Engine* las marca (mark) y las limpia (Sweep). p.ej. al sobreescribir el valor de una variable
        - *Stack Overflow* : Se genera cuando el *call stack* se llena completamente (pila de tareas). Esto pasa cuando se trabaja con bucles infinitos, recurcividad y funciones
    - JS Runtime
        - Memory Heap y Call Stack
        - Web APIs
        - Callback Queue. Cuando hay funciones que no le corresponden a JS sino al navegador o SO lo delega y JS continúa ejecutando las tareas del *call stack*, al terminar de ejecutarse la función delegada, se coloca en esta lista (fila de espera)
        - Event Loop. Monitorea constantemente (watcher) el *call stack* y el *callback queue*, en cuanto una tarea del *callback queue* ha terminado, la coloca en el *call stack* para ser atendida
- Basado en módulos, para añadir funcionalidad se deben importar
- Existen módulos globales como: *console*, *module*, *interval*, *timeout*, *require()*
- `node ruta/archivo.js` : Ejecuta un script

## Debug
- `node inspect ruta/archivo.js` : Ejecuta el script en modo depuración
- `node --inspect ruta/archivo.js` : Ejecuta el script en modo depuración utilizando las devtools de chrome
    - `--inspect=pto` : establece un puerto personalizado para la depuración con las dev tools
    - `--inspect-brk` : Ejecuta el script en modo depuración y se interrumpe en la primer línea
- Comandos para avanzar en la depuración:
    - `cont` | `c`: Continúa la ejecución normal del script
    - `next` | `n`: Salta a la siguiente línea
    - `step` | `s`: Salta dentro de la definición de la línea en ejecución
    - `out` | `o`: Salta a la salida de la definición en ejecución
- Breakpoints
    - Al escribir `debugger;` en el código fuente del script, se agrega un breakpoint
    - Establecer breakpoints durante la depuración `setBreakpoint()` | `sb()`:
        - sb(numLinea) : Establece el breakpoint en la línea especificada
        - sb('script.js', linea) : Agrega el breakpoint en el archivo y linea especificada
        - `clearBreakpoint()`, `cb()` : Limpia el breakpoint especificado, sus parámetros son los mismos que los de `sb()`
- Comandos informativos
    - `backtrace` | `bt`: Muestra la traza del cuadro de ejecución actual
    - list(N): Muestra N líneas antes y después de la línea en pausa actual
    - watch(expr): Agrega una expresión a la lista de observadores
    - unwatch(expr): Remueve la expresión de la lista de observadores
    - watchers: Lista los observadores y sus valores (automaticamente se lista en cada breakpoint)
    - repl: Abre la consola REPL de Node
    - exec expr: Ejecuta una expresión dentro del contexto del script en ejecución

## Modulos
- `const nombreCTE = require('modulo')` : Importar un módulo instalado en el proyecto o en el sistema, generalmente se trata de un objeto con múltiples propiedades y funciones
- `const nombreCTE = require('./ruta/archivo.js')` : Importar un módulo JS de nuestro mismo proyecto
- `nombreCTE.prop` : Modo de uso de la variable, objeto, arreglo o función del módulo importado
- `exports.prop = valor` : Modo de exportar un valor, variable, objeto, arreglo o función de la definición de un módulo. Si no se exporta alguna variable o función, esa propiedad no estará definida en el script que importa este módulo
    - `module.exports = obj` : exporta todo un objeto o función. Si se trata de un objeto es como si se exportara una a una sus propiedades (`exports.prop = valor`)
- Módulos del core de Node: *file system*, *os*, *net*, *process*, *http*, *https*, *path*, *repl*, entre otros más
- Las funciones del core de Node normalmente son asíncronas, por lo que se le puede mandar un *callback* como parámetro para que al final de su ejecicón informe si se obtuvo un error o realizar alguna notificación, pero en algunos casos existe su versión síncrona
- Nueva sintaxis:
    - Exportar
        ~~~ js
        export function hello() {
	        return 'Hello!'
        }

        export const bye = 'Bye!'
        ~~~
    - Importar
        ~~~ js
        /** Una a una cada propiedad / función
         - Con la posibilidad de reenombrar alguna propiedad
         -/
        import { hello, bye as byeGreeting } from './module'

        console.log(hello())
        console.log(byeGreeting)
        ~~~
        ~~~ js
        // Todo el módulo
        import * as allGreetings from './module'

        console.log(allGreetings.hello())
        console.log(allGreetings.bye)
        ~~~
### Uso de módulos
- `child*process` : Tiene dos funciones `spawn` y `exec`, mediante las cuales se inicia un proceso secundario para ejecutar otros programas en el sistema. La diferencia entre estas es que `spawn` devuelve un *stream* y `exec` devuelve un *buffer*.
    - Usar `spawn` cuando se quiera que el proceso hijo devuelva datos binarios enormes a Node y cuando se quiera recibir datos desde que el proceso arranca.
    - Usar `exec` cuando se quiera que el proceso hijo devuelva mensajes de estado simples o cuando solo se quiera recibir datos al final de la ejecución.

## Variables de Entorno
- El script se debe ejecutar de la siguiente manera: `VAR1=valor VAR2=valor node script.js`
- Para obtener los valores de las va. se codifica:
    ~~~ js
    const var1 = process.env.VAR1 || 'valor default'; // Buena práctica establecer un valor default por si no se pasa el valor de la variable con el script
    const var2 = process.env.VAR2 || 0 ;
    ~~~
- También se pueden leer las variables desde un archivo *.env* haciendo uso del módulo `dotenv`

## NPM
- Es el gestor de dependencias de Node, la mejor forma de añadir dependencias es con:
    - `npm init` : presenta asistente para inicializar un proyecto node, se crea archivo *package.json*
    - `npm install -g npm` : actualizar a una versión superior NPM de forma global
    - `npm install -g nombreModulo` : Instala el módulo de forma global
    - `npm i nombreModulo@#.#.#` : Instala el módulo en el directorio actual con el número de versión especificada
    - `npm i` : instala los módulos indicados en el archivo *package.json*
    - `npm i nombreModulo --save` | `npm i nombreModulo -S` : instala el módulo en el proyecto actual y actualiza el archivo *package.json*
    - `npm uninstall nombreModulo --save` : desinstala el módulo en el proyecto actual y actualiza el archivo *package.json*
    - `npm uninstall nombreModulo --no-save` : desinstala el módulo en el proyecto actual sin actualizar el archivo *package.json*
    - `npm i nombreModulo --save-dev` | `npm i nombreModulo -D` : Agrega una dependencia únicamente para el ambiente de desarrollo
    - `npm i nombreModulo -O` : Indica que la instalación de ese módulo es opcional
    - `npm i nombreModulo --dry-run` : Simula la instalación del módulo, muestra los detalles de la isntalación aunque no se haya efectuado
    - `npm list` : Muestra el listado de los módulos instalados en el proyecto
    - `npm list -g --depth 0` : Listado de módulos instalados de forma global
    - `npm outdate` : Muestra los módulos que pueden estar desactualizados. Con el flag `--dd` se puede obtener una salida más detallada
    - `npm update` : Realiza la actualziación de todos los paquetes desactualizados
    - `npm update nombreModulo@latest` : Realiza la actualziación del paquete señalado en la última versión 
    - `npm cache clean --force` : Borra el cache de los módulos instalados
    - `npm cache verify` : Valida que el cache se encuentre limpio
    - `npm audit` : Revisa las vulnerabilidades de los paquetes instalados y su impacto
        - `npm audit --json` : Realiza la auditoría y entrega el resultado en JSON
    - `npm audit fix` : Actualiza todos los paquetes que tienen vulnerabilidades
- El archivo *package.json* contiene metadatos, configuraciones, scripts y dependecias del proyecto.
    - Como metadatos está el nombre del proyecto, número de versión, autor, descripción, keywords (separados por comas) y licencia
    - Como configuración está el archivo de entrada (primer archivo a ejecutarse), repositorio de control de versiones y scripts, que le indican a npm que debe ejecutar un comando bajo algún nombre como keyword "start", "test" (`npm start`), o keyword "personalizado" (`npm run personalizado`).
    - Como dependencias se encuentran el nombre y versión de los módulos, además de que también existe una sección de dependencias exclusivamente de desarrollo
        - ` ` : Vacío, mantiene la versión del paquete estática
        - `^` : Actualiza la versión del paquete de cambios menores y parches
        - `~` : Actualiza la versión del paquete solamente en parches
        - `<` : Versión menor a la indicada
        - `<=` : Versión menor o igual a la indicada
        - `>` : Versión mayor a la indicada
        - `>=` : Versión mayor o igual a la indicada
- El archivo *package-lock.json* es un archivo generado automáticamente cuando se instalan paquetes o dependencias en el proyecto. Su finalidad es mantener un historial de los paquetes instalados y optimizar la forma en que se generan las dependencias del proyecto y los contenidos de la carpeta *node\*modules/*
- Crear configuraciones default:
    ~~~ bash
    npm set init.author.email "your@email.com" # Establece el email
    npm set init.author.name "your name" # Establece el nombre del autor
    npm set init.license "MIT" # Establece la licencia MIT
    ~~~
- Actualizar Node con NPN:
    ~~~ bash
    npm cache clean -f # borra cache
    npm install -g n # instala el módulo "n" de forma global
    n estable # Instala la última versión estable de Node, también se puede especificar una versión con #.#.#
    ~~~
- Actualizar NPM:
    ~~~ bash
    npm cache clean --force
    npm install@latest -g | npm install -g npm@latest
    ~~~
- Crear un módulo de NPM:
    - Iniciar un proyecto Git y conectarlo al repositorio remoto y luego iniciar proyecto Node
    - Escribir un Readme
    - Crear la carpeta *bin* y dentro el archivo global.js establecer la *shebang line* como `#!/usr/bin/env node` y utilizar el módulo
    - En el archivo *package.json* agregar
    ~~~ json
    "bin" : {
        "nombre-modulo" : "./bin/global.js"
    },
    "preferGlobal" : true,
    ~~~
    - `npm link` : Ejecutar el comando en el directorio del proyecto, con esto, se instala de forma global y realiza análisis de vulnerabilidades
        - `npm i -g ruta/proyecto` : Si se realizan cambios en el proyecto, volver a instalar el paquete
    - Registrarse en NPM para publicar paquete
        - `npm adduser` : Agregar credenciales de NPM -> username, password, email
    - `npm publish` : Ejecutar en la carpeta del proyecto, se publica paquete en NPM
    - Al realizar cambios en el proyecto, se debe actualizar su versión con los siguientes comandos, automáticamente se actualiza el archivo *package.json* y volver a publicar:
        - `npm version patch` : Actualiza la versión en la sección de parches
        - `npm version minor` : Actualiza la versión en la sección de cambio menor
        - `npm version major` : Actualiza la versión en la sección de cambio mayor

