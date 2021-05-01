# Desarrollo de software

## Introducción
- __Lenguaje informático.__ Instrucciones que ejecuta una computadora
- __Lenguaje de programación.__ Resuelve un algoritmo tiene su propia sintaxis, tipos de datos y funciones nativas para realizar diferentes tareas
- __Algoritmo.__ Conjunto de instrucciones lógicas ordenadas que resuleven un problema. Un algoritmo debe ser:
    * Definido. Resuelve el problema, los mismos datos de entrada deben obtener los mismos datos de salida
    * Preciso. Obtener el resultado correcto
    * Legible
    * Finito. Debe tener un Inicio y un Final
- __Paradigma.__ Forma de programar para resolver un problema
- __Ciudadanos de primera clase.__ Elementos de un lenguaje de programación que tienen más privilegios que otros elementos dentro del mismo lenguaje. Se consideran elementos de primera clase si:
    * Puede ser guardado en variables
    * Puede ser enviado como argumento en funciones
    * Puede ser usado como valor de retorno
    * Tiene identidad propia

## Tipos de lenguajes de programación
- Por su compilación
    * Compilado. Convierte el código fuente en código binario para que sea entendido y ejecutado por la computadora
    * Interpretado. Existe un intérprete que lee el código fuente y lo traduce en binario en tiempo de ejecución.
        + JIT (Just In Time). Compilar en tiempo de ejecución
- Por su paradigma
    * Multiparadigma. Compatible con múltiples formas de trabajo
    * Estructurado. Programa que ejecuta instrucciones de forma secuencial
    * Programación Orientada a Objetos. Separa el programa en entidades y las acciones que son capaces de realizar. Sus pilares son la abstracción, encapsulamiento, herencia y polimorfismo. Una clase es el molde con el que se crean los objetos, a la acción de crear un objeto de una clase se le llama _instanciar_, un objeto es una instancia de una clase.
    * Funcional. Todo es una función, deben existir datos de entrada y datos de salida
    * Reactiva. El programa reacciona de acuerdo a la interacción que realice el usuario. Con el framework Rx se brinda la posibilidad de trabajar con este paradigma en distintos lenguajes
    * Otro grupo de clasificación es:
        - Imperativa. Se define paso a paso como debe ejecutarse un programa
        - Declarativa. Se indica al sistema lo que se quiere hacer pero no se sabe como lo realiza
- Por su próposito
    * General (GPL). Se puede desarrollar cualquier aplicación y resolver cualquier problema.
    * Específico (DSL - Domain Specific Language). Lenguaje que fue creado para un uso en particular. Por ejemplo, SQL
- Por su nivel de abstracción
    * Alto nivel. Lenguaje con sintaxis más fácil de entender por el humano. Se ejecuta sobre la capa de abstracción de software
    * Mediano nivel. Lenguaje que es entendible por los humanos pero con una sintaxis que permite una interacción muy cercana con el SO y hardware. Lenguaje C
    * Bajo nivel. Lenguaje que se comunica y manipula el hardware. Ensamblador y máquina
- Por su tipado
    * No tipados. En su sintaxis no se especifica el tipo de dato al declarar una variable, la reserva de memoria se realiza de forma dinámica (infiere su valor). Por lo regular son débilmente tipados (se puede sobrescribir el tipo de dato de una variable ya declarada)
    * Tipados. Se establece su tipo de dato en tiempo de programación y no puede almacenar valores con otros tipos de dato (fuertemente tipado). Existen lenguajes que, aunque no se defina el tipo de dato en tiempo de programación, una vez que se inicialice, no podrá almacenar datos de otros tipos

## Áreas de la programación
- Desarrollo WEB
    * Frontend
    * Backend
    * Fullstack
    * Administrador de base de datos
    * Administrador de servidores
- Desarrollo movil
    * Nativo (Android o Apple)
    * Multiplataforma. A partir de tecnologías web o un lenguaje intermedio, crear una aplicación movil para los diferentes sistemas operativos móviles
    * PWA. A partir de tecnologías web, una aplicación que funcione de forma offline y capaz de utilizar las APIs del celular
- Desarrollo de escritorio. Para SO de computadoras
- Videojuegos
    * Consola
    * PC
    * Movil
- Realidad virtual (inmerción total de un escenario) y aumentada (agregar elementos virtuales en la realidad)
- Sistemas operativos, embebidos, IoT
- Seguridad informática
    * Ofensiva. Hacking ético (white hat), detecta vulnerabilidades
    * Defensiva. A nivel de infraestructura, configurar hardware y software; a nivel de desarrollo, buenas prácticas de programación
- Machine learning, deep learning, data science, big data, visión por computadora
- Cloud computing
    * IaaS. Infraestructura como servicio
    * PaaS. Plataforma como servicio
    * SaaS. Software como servicio
    * BaaS. Backend como servicio
    * DaaS. Escritorio como servicio
    * FaaS. Funciones como servicio

## Tecnicismos
- _Hardcoding_. Mala prática en la que se incrustan datos (comunmente configuraciones) en lugar de obtenerlos de una fuente de datos. En consecuencia, toda futura modificación tendrá un alto costo
- _Debugging_. Proceso de identificar y depurar el código de bugs (errores)
- _Workaround_. Solución temporal ante un problema o limitación en el sistema hasta su corrección definitiva
- _Build_. Versión funcional de un software que icluye todas las características del producto final
- _Release_. Lanzamiento de una versión de un software, se identifica con números como v1.2.0
- _Deploy_. Proceso de lanzar una versión nueva del software al servidor
- _Refactorizar_. Mejora en el código fuente para mejorar su escalabilidad o legibilidad
- _Issue_. Es un asunto por resolver, como arreglar un bug, una mejora en el sistema o una tarea pendiente
- _Testing_. Consiste en probar la calidad del sistema. Puede ser a nivel de código, funcinalidad, rendimiento, etc. Pueden realizarse de forma manual o automatizada
- _Rollback_. Se revierten los últimos cambios del sistema, volviendo a la última versión estable
- _Code review_. Ayuda prestada entre desarrolladores para revisar en conjunto el código realizado, aportan ideas, se discuten bugs, mejoras y más
- _Workspace_. Grupo de archivos que contienen los recursos necesarios y permiten al desarrollador trabajar con ellos como una unidad
- _Enviroment_. Ambiente, entorno de trabajo donde el desarrollador obtiene los servicios necesarios para desarrollar software
- _CLI_. Interfaz de línea de comandos, se utiliza para intercatuar con software y con el SO
- _REPL_. Acrónimo que signica Read, Eval, Print, Loop, es un entorno por consola que permite ejecutar intrucciones y/o comandos
- _Shell_. Término usado en informática para referirse a un intérprete de comandos. Mediante instrucciones que aporta el intérprete, el usuario puede comunicarse con el kernel y por extensión, ejecutar dichas órdenes, así como herramientas que le permiten controlar el funcionamiento del sistema
- _Bash_. Acrónimo de Bourne-again shell, es un intérprete de órdenes, es un superconjunto de sh (Bourne Shell es un programa informático cuya función consiste en interpretar órdenes basadas en POSIX. Incorpora características como control de procesos, redirección de entrada/salida, listado y lectura de ficheros, protección, comunicaciones y un lenguaje de órdenes para escribir programas por lotes o “scripts”)
- _Stringfy_. Método con el que un objeto o valor se convierte en una cadena de texto JSON
- _Serialización_. Proceso de convertir un tipo de dato A a un tipo de dato B a través de un flujo de red o un flujo hacia un archivo
- _ORM_. acrónimo de Object Relational Mapping, es una técnica de programación para convertir datos entre el sistema de tipos utilizado en un lenguaje de programación orientado a objetos y la utilización de una base de datos relacional como motor de persistencia
- _Hooking_. Técnicas utilizadas para alterar o aumentar el comportamiento de un sistema operativo, de aplicaciones o de otros componentes de software interceptando llamadas de función, mensajes o eventos pasados entre componentes de software.
- _Hardening o endurecimiento_. Es el proceso de asegurar un sistema reduciendo sus vulnerabilidades o agujeros de seguridad, para los que se está más propenso cuanto más funciones desempeña
- _Ofuscación_. Se refiere a hacer ilegible el código sin afectar su funcionalidad. Las técnicas utilizadas para ocultar el código de esta manera varían considerablemente. Abarcan desde la sustitución de nombres legibles en el código por alternativas difíciles de descifrar (ofuscación de nombre) hasta la modificación de la estructura lógica del código para hacerlo menos predecible y rastreable (ofuscación de flujo de control). Otra técnica consiste en la conversión de expresiones aritméticas y lógicas simples en equivalentes complejas (ofuscación aritmética).
    * Al sustituir todos los nombres de las variables y de las funciones por nombres de una sola letra, es prácticamente imposible comprender el código del programa. En ocasiones, también se utilizan ofuscadores de este tipo con el propósito de reducir el tamaño del código fuente
- _Encriptación_ Garantiza que el código y los datos de la aplicación no se puedan acceder mientras la aplicación está en reposo. El código encriptado es descifrado inmediatamente cuando se ejecuta la aplicación, lo que garantiza que funcione según lo previsto. Para ser efectiva, la encriptación debe aplicarse en varias capas. Las técnicas de encriptación esenciales incluyen la encriptación de cadenas, encriptación de clases, encriptación de asset y encriptación de recursos.

## Buenas prácticas
- Variables
    * Nombrar las va. con sentido (que sean autodescriptivas) que indiquen el dato que está almacenando. ¡No nos cobran por caracter!
    * Convención (notación) de nombres para variables:
        + _Camel Case_. Combina las palabras directamente, sin usar ningún símbolo, estableciendo que la primera letra de cada palabra esté en mayúscula: `miVariable` (Lower Camel Case), `DatoNombre` (Upper Camel Case)
        + _Snake Case_. Combina las palabras usando un guión bajo `\_` como nexo: `mi_variable`
        + _Kebab Case_. Combina las palabras usando un guión `\-` como nexo. Las letras están en minúscula. Es el estándar que se usa en la creación de URLs: `mi-variable`
        + _Notación Húngara_. Cuando se tienen arreglos de datos o el mismo dato con diferentes tipos, se puede identificar con un prefijo en el nombre de la va. haciendo referencia a dicho tipo: `lstPersonas` - lista de personas, `arrPersonas` - arreglo de personas, `iNumero` - Numero entero, `sNumero` - Numero como texto
        + En caso de utilizar constantes, nombrarlas con mayúsculas (_Upper Case_ \+ _Snake Case_) o con algún prefijo (_Upper Case_ \+ _Notación Húngara_)
    * Evitar usar o tener demasiadas variables globales
    * Recomendación: declarar las va. a utilizar al principio de la función
- Funciones
    * Tener en promedio en el bloque de código aproximadamente 20 instrucciones
    * Tener un nombre descriptivo de lo que hace la función
    * Dedicarse a un único objetivo. Si se requiere lógica adicional a lo que indica que realiza la función, utilizar otra función. Estas funciones adicionales se recomienda colocar debajo de la función que las invoca
    * Evitar anidar demasiadas sentencias de control condicional, se vuelve poco legible el códig
- Dcoumentar
    * Evitar comentarios o redundantes. Si la va./función ya tiene un nombre descriptivo no es necesario comentar a que hace referencia
    * Evitar bloques de código. Tener código comentado mezclado con código funcional vuelve ilegible la comprensión de este


## Versionamiento Semántico (VerSem)
Divide el número de cada versión en tres segmentos numéricos, que tienen el propósito de indicar el estado y la compatibilidad de una pieza de software: `cambiosMayores.características.parches`
- _La parte más pequeña o el segmento de los parches_. Este número se usa para indicar que no se está introduciendo nueva funcionalidad en ella. Comúnmente se usa cuando se corrigen errores dentro de esta o cualquier otro cambio que no modifique la apariencia "externa" de una API. Este número puede cambiar con rapidez a medida que se resuelven errores o casos excepcionales en el código.
- _Segmento de los cambios menores o características_. Se usa para indicar que se le ha añadido funcionalidad nueva a la biblioteca pero que nada de lo anterior dejará de funcionar de la manera en la que ya lo hace. Es decir, mientras que la apariencia exterior de la biblioteca versionada ha cambiado, lo que antes se conectaba con ella, puede seguir haciéndolo sin problema. Si la versión menor cambia, el número de parches debe ser reestablecido a 0.
- _Componente de cambios mayores o de ruptura_. Se emplea para indicar cambios tanto externos como internos que resultan en hacer que el software no sea compatible con versiones anteriores. Se llama _de ruptura_ puesto que si la persona que usa una biblioteca actualiza descuidadamente la versión, probablemente encontrará muchos errores y cosas inservibles en su código.
### Especificación de Versionado Semántico
En el documento original se usa el __RFC 2119__ para el uso de las palabras _MUST_, _MUST NOT_, _SHOULD_, _SOULD NOT_ y _MAY_. Para que la traducción sea lo más fiel posible, MUST se traduce como el verbo _deber en presente_ (DEBE, DEBEN), _SHOULD_ como el verbo _deber en condicional_ (DEBERÍA, DEBERÍAN) y el verbo _MAY_ como el verbo _PODER_.
1. El software que use Versionado Semántico DEBE declarar una API pública. Esta API puede ser declarada en el código mismo o existir en documentación estricta. De cualquier manera, debería ser precisa y completa.
2. Un número normal de versión DEBE tomar la forma X.Y.Z donde X, Y, y Z son enteros no negativos. X es la versión “major”, Y es la versión “minor”, y Z es la versión “patch”. Cada elemento DEBE incrementarse numéricamente en incrementos de 1.
    - Por ejemplo: 1.9.0 -> 1.10.0 -> 1.11.0.
3. Una vez que un paquete versionado ha sido liberado (release), los contenidos de esa versión NO DEBEN ser modificadas. Cualquier modificación DEBE ser liberada como una nueva versión.
4. La versión major en cero (0.y.z) es para desarrollo inicial. Cualquier cosa puede cambiar en cualquier momento. El API pública no debiera ser considerada estable.
5. La versión 1.0.0 define el API pública. La forma en que el número de versión es incrementado después de este release depende de esta API pública y de cómo esta cambia.
6. La versión patch Z (x.y.Z | x > 0) DEBE incrementarse cuando se introducen solo arreglos compatibles con la versión anterior. Un arreglo de bug se define como un cambio interno que corrige un comportamiento erróneo.
7. La versión minor Y (x.Y.z | x > 0) DEBE ser incrementada si se introduce nueva funcionalidad compatible con la versión anterior. Se DEBE incrementar si cualquier funcionalidad de la API es marcada como deprecada. PUEDE ser incrementada si se agrega funcionalidad o arreglos considerables al código privado. Puede incluir cambios de nivel patch. La versión patch DEBE ser reseteada a 0 cuando la versión minor es incrementada.
8. La versión major X (X.y.z | X > 0) DEBE ser incrementada si cualquier cambio no compatible con la versión anterior es introducida a la API pública. PUEDE incluir cambios de niver minor y/o patch. Las versiones patch y minor DEBEN ser reseteadas a 0 cuando se incrementa la versión major.
9. Una versión pre-release PUEDE ser representada por adjuntar un guión y una serie de identificadores separados por puntos inmediatamente después de la versión patch. Los identificadores DEBEN consistir solo de caracteres ASCII alfanuméricos y el guión. Las versiones pre-release satisfacen pero tienen una menor precedencia que la versión normal asociada.
    - Ejemplos: 1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7, 1.0.0-x.7.z.92.
10. La metadata de build PUEDE ser representada adjuntando un signo más y una serie de identificadores separados por puntos inmediatamente después de la versión patch o la pre-release. Los identificadores DEBEN consistir sólo de caracteres ASCII alfanuméricos y el guión. Los meta-datos de build DEBIERAN ser ignorados cuando se intenta determinar precedencia de versiones. Dos paquetes con la misma versión pero distinta metadata de build se consideran la misma versión.
    - Ejemplos: 1.0.0-alpha+001, 1.0.0+20130313144700, 1.0.0-beta+exp.sha.5114f85.
11. La precedencia DEBE ser calculada separando la versión en major, minor, patch e identificadores pre-release en ese orden (La metadata de build no figuran en la precedencia). Las versiones major, minor, y patch son siempre comparadas numéricamente. La precedencia de pre-release DEBE ser determinada comparando cada identificador separado por puntos de la siguiente manera: los identificadores que solo consisten de números son comparados numéricamente y los identificadores con letras o guiones son comparados de acuerdo al orden establecido por ASCII. Los identificadores numéricos siempre tienen una precedencia menor que los no-numéricos.
    - Ejemplo: 1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0.


## Sobre paradigmas
### Funcional
- Centrado en funciones, son ciudadanos de primera clase.
- Función de orden superior. Pueden recibir o retornar funciones.
- Principales operaciones: _map_ (transformación de un valor a otro), _reduce_ (acumulación de elementos), _filter_ (criterios de elegibilidad  de elementos de una colección para introducirlos en otra)
- Utiliza recursividad en lugar de iteración
- No existe la mutabilidad de una variable asignada declarada dentro de un bloque de código
- No almacena estados. Al llamar a una función multiples veces con las mismas entrdas siempre devolverá los mismos resultados, estos no se verán influenciados por condiciones externas o estados almacenados previamente. También se le conoce como _transparencia referencial_,
- Útil en procesamiento paralelo
- Suelen ser declarativo: se le dice al programa que hacer pero no como

### Reactiva
- Útil en procesos asíncronos, flujo asíncronos de datos
- Una forma de implementar el patrón de diseño Observer
- Obsevables. Flujos de datos, añade suscriptores al flujo de datos
- Observadores. Módulos que consumen los flujos de datos. Implementan 3 métodos: reaccionar al siguiente valor, reaccionar a un error, reaccionar al informe de término del flujo de datos
