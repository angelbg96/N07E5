# Node JS

- Se ejecuta a través del motor V8 de Chrome, que interpreta el código JS para convertirlo en  lenguaje máquna. Está escrito en C++
- Basado en módulos, para añadir funcionalidad se deben importar
- Existen módulos globales como: _console_, _module_, _interval_, _timeout_, _require()_
- `node ruta/archivo.js` : Ejecuta un script

## Debug
- `node inspect ruta/archivo.js` : Ejecuta el script en modo depuración
- `node --inspect ruta/archivo.js` : Ejecuta el script en modo depuración utilizando las devtools de chrome
    * `--inspect=pto` : establece un puerto personalizado para la depuración con las dev tools
    * `--inspect-brk` : Ejecuta el script en modo depuración y se interrumpe en la primer línea
- Comandos para avanzar en la depuración:
    * `cont` | `c`: Continúa la ejecución normal del script
    * `next` | `n`: Salta a la siguiente línea
    * `step` | `s`: Salta dentro de la definición de la línea en ejecución
    * `out` | `o`: Salta a la salida de la definición en ejecución
- Breakpoints
    * Al escribir `debugger;` en el código fuente del script, se agrega un breakpoint
    * Establecer breakpoints durante la depuración `setBreakpoint()` | `sb()`:
        + sb(numLinea) : Establece el breakpoint en la línea especificada
        + sb('script.js', linea) : Agrega el breakpoint en el archivo y linea especificada
        + `clearBreakpoint()`, `cb()` : Limpia el breakpoint especificado, sus parámetros son los mismos que los de `sb()`
- Comandos informativos
    * `backtrace` | `bt`: Muestra la traza del cuadro de ejecución actual
    * list(N): Muestra N líneas antes y después de la línea en pausa actual
    * watch(expr): Agrega una expresión a la lista de observadores
    * unwatch(expr): Remueve la expresión de la lista de observadores
    * watchers: Lista los observadores y sus valores (automaticamente se lista en cada breakpoint)
    * repl: Abre la consola REPL de Node
    * exec expr: Ejecuta una expresión dentro del contexto del script en ejecución

## Modulos
- `const nombreCTE = require(modulo)` : Importar un módulo instalado en el proyecto o en el sistema, generalmente se trata de un objeto con múltiples propiedades y funciones
- `const nombreCTE = require(./ruta/archivo.js)` : Importar un módulo JS de nuestro mismo proyecto
- `nombreCTE.prop` : Modo de uso de la variable, objeto, arreglo o función del módulo importado
- `exports.prop = valor` : Modo de exportar un valor, variable, objeto, arreglo o función de la definición de un módulo. Si no se exporta alguna variable o función, esa propiedad no estará definida en el script que importa este módulo
    * `module.exports = obj` : exporta todo un objeto o función. Si se trata de un objeto es como si se exportara una a una sus propiedades (`exports.prop = valor`)
- Módulos del core de Node: _file system_, _os_, _net_, _process_, _http_, _https_, _path_, _repl_, entre otros más
- Las funciones del core de Node normalmente son asíncronas, por lo que se le puede mandar un _callback_ como parámetro para que al final de su ejecicón informe si se obtuvo un error o realizar alguna notificación, pero en algunos casos existe su versión síncrona
- Nueva sintaxis:
    * Exportar
        ~~~ js
        export function hello() {
	        return 'Hello!'
        }

        export const bye = 'Bye!'
        ~~~
    * Importar
        ~~~ js
        /** Una a una cada propiedad / función
         * Con la posibilidad de reenombrar alguna propiedad
         */
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

## NPM
- Es el gestor de dependencias de Node, la mejor forma de añadir dependencias es con:
    * `npm init` : presenta asistente para inicializar un proyecto node, se crea archivo _package.json_
    * `npm install -g npm` : actualizar a una versión superior NPM de forma global
    * `npm install -g nombreModulo` : Instala el módulo de forma global
    * `npm i nombreModulo` : Instala el módulo en el directorio actual
    * `npm i` : instala los módulos indicados en el archivo _package.json_
    * `npm i nombreModulo --save` : instala el módulo en el proyecto actual y actualiza el archivo _package.json_
    * `npm uninstall nombreModulo --save` : desinstala el módulo en el proyecto actual y actualiza el archivo _package.json_
- El archivo _package.json_ contiene metadatos, configuraciones, scripts y dependecias del proyecto.
    * Como metadatos está el nombre del proyecto, número de versión, autor, descripción, keywords y licencia
    * Como configuración está el archivo de entrada (primer archivo a ejecutarse), repositorio de control de versiones y scripts, que le indican a npm que debe ejecutar un comando bajo algún nombre como keyword "start", "test" (`npm start`), o keyword "personalizado" (`npm run personalizado`).
    * Como dependencias se encuentran el nombre y versión de los módulos, además de que también existe una sección de dependencias exclusivamente de desarrollo
- El archivo _package-lock.json_ es un archivo generado automáticamente cuando se instalan paquetes o dependencias en el proyecto. Su finalidad es mantener un historial de los paquetes instalados y optimizar la forma en que se generan las dependencias del proyecto y los contenidos de la carpeta _node\_modules/_
- Actualizar Node con NPN:
    ~~~ js
    npm cache clean -f // borra cache
    npm install -g n // instala el módulo "n" de forma global
    n estable // Instala la última versión estable de Node, también se puede especificar una versión con #.#.#
    ~~~


