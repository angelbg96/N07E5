# Desarrollo de software

## Introducción
- **Lenguaje informático.** Instrucciones que ejecuta una computadora
- **Lenguaje de programación.** Resuelve un algoritmo tiene su propia sintaxis, tipos de datos y
  funciones nativas para realizar diferentes tareas
- **Algoritmo.** Conjunto de instrucciones lógicas ordenadas que resuleven un problema. Un algoritmo
  debe ser:
	- Definido. Resuelve el problema, los mismos datos de entrada deben obtener los mismos datos de
	  salida
	- Preciso. Obtener el resultado correcto
	- Legible
	- Finito. Debe tener un Inicio y un Final
- **Paradigma.** Forma de programar para resolver un problema
- **Ciudadanos de primera clase.** Elementos de un lenguaje de programación que tienen más
  privilegios que otros elementos dentro del mismo lenguaje. Se consideran elementos de primera
  clase si:
	- Puede ser guardado en variables
	- Puede ser enviado como argumento en funciones
	- Puede ser usado como valor de retorno
	- Tiene identidad propia

## Tipos de lenguajes de programación
- Por su compilación
	- Compilado. Convierte el código fuente en código binario para que sea entendido y ejecutado por
	  la computadora
	- Interpretado. Existe un intérprete que lee el código fuente y lo traduce en binario en tiempo
	  de ejecución.
		- JIT (Just In Time). Compilar en tiempo de ejecución
- Por su paradigma
	- Multiparadigma. Compatible con múltiples formas de trabajo
	- Estructurado. Programa que ejecuta instrucciones de forma secuencial
	- Programación Orientada a Objetos. Separa el programa en entidades y las acciones que son
	  capaces de realizar. Sus pilares son la abstracción, encapsulamiento, herencia y polimorfismo.
	  Una clase es el molde con el que se crean los objetos, a la acción de crear un objeto de una
	  clase se le llama *instanciar*, un objeto es una instancia de una clase.
	- Funcional. Todo es una función, deben existir datos de entrada y datos de salida
	- Reactiva. El programa reacciona de acuerdo a la interacción que realice el usuario. Con el
	  framework Rx se brinda la posibilidad de trabajar con este paradigma en distintos lenguajes
	- Otro grupo de clasificación es:
		- Imperativa. Se define paso a paso como debe ejecutarse un programa
		- Declarativa. Se indica al sistema lo que se quiere hacer pero no se sabe como lo realiza
- Por su próposito
	- General (GPL). Se puede desarrollar cualquier aplicación y resolver cualquier problema.
	- Específico (DSL - Domain Specific Language). Lenguaje que fue creado para un uso en
	  particular. Por ejemplo, SQL
- Por su nivel de abstracción
	- Alto nivel. Lenguaje con sintaxis más fácil de entender por el humano. Se ejecuta sobre la
	  capa de abstracción de software
	- Mediano nivel. Lenguaje que es entendible por los humanos pero con una sintaxis que permite
	  una interacción muy cercana con el SO y hardware. Lenguaje C
	- Bajo nivel. Lenguaje que se comunica y manipula el hardware. Ensamblador y máquina
- Por su tipado
	- No tipados. En su sintaxis no se especifica el tipo de dato al declarar una variable, la
	  reserva de memoria se realiza de forma dinámica (infiere su valor). Por lo regular son
	   débilmente tipados (se puede sobrescribir el tipo de dato de una variable ya declarada)
	- Tipados. Se establece su tipo de dato en tiempo de programación y no puede almacenar valores
	  con otros tipos de dato (fuertemente tipado). Existen lenguajes que, aunque no se defina el
	  tipo de dato en tiempo de programación, una vez que se inicialice, no podrá almacenar datos de
	  otros tipos


## Áreas de la programación
- Desarrollo WEB
	- Frontend
	- Backend
	- Fullstack
	- Administrador de base de datos
	- Administrador de servidores
- Desarrollo movil
	- Nativo (Android o Apple)
	- Multiplataforma. A partir de tecnologías web o un lenguaje intermedio, crear una aplicación
	  movil para los diferentes sistemas operativos móviles
	- PWA. A partir de tecnologías web, una aplicación que funcione de forma offline y capaz de
	  utilizar las APIs del celular
- Desarrollo de escritorio. Para SO de computadoras
- Videojuegos
	- Consola
	- PC
	- Movil
- Realidad virtual (inmerción total de un escenario) y aumentada (agregar elementos virtuales en la
  realidad)
- Sistemas operativos, embebidos, IoT
- Seguridad informática
	- Ofensiva. Hacking ético (white hat), detecta vulnerabilidades
	- Defensiva. A nivel de infraestructura, configurar hardware y software; a nivel de desarrollo,
	  buenas prácticas de programación
- Machine learning, deep learning, data science, big data, visión por computadora
- Cloud computing
	- IaaS. Infraestructura como servicio
	- PaaS. Plataforma como servicio
	- SaaS. Software como servicio
	- BaaS. Backend como servicio
	- DaaS. Escritorio como servicio
	- FaaS. Funciones como servicio


## Tecnicismos
- *Hardcoding*. Mala prática en la que se incrustan datos (comunmente configuraciones) en lugar de
  obtenerlos de una fuente de datos. En consecuencia, toda futura modificación tendrá un alto costo
- *Debugging*. Proceso de identificar y depurar el código de bugs (errores)
- *Workaround*. Solución temporal ante un problema o limitación en el sistema hasta su corrección
  definitiva
- *Build*. Versión funcional de un software que icluye todas las características del producto final
- *Release*. Lanzamiento de una versión de un software, se identifica con números como v1.2.0
- *Deploy*. Proceso de lanzar una versión nueva del software al servidor
- *Refactorizar*. Mejora en el código fuente para mejorar su escalabilidad o legibilidad
- *Issue*. Es un asunto por resolver, como arreglar un bug, una mejora en el sistema o una tarea
  pendiente
- *Testing*. Consiste en probar la calidad del sistema. Puede ser a nivel de código, funcinalidad,
  rendimiento, etc. Pueden realizarse de forma manual o automatizada
- *Rollback*. Se revierten los últimos cambios del sistema, volviendo a la última versión estable
- *Code review*. Ayuda prestada entre desarrolladores para revisar en conjunto el código realizado,
  aportan ideas, se discuten bugs, mejoras y más
- *Workspace*. Grupo de archivos que contienen los recursos necesarios y permiten al desarrollador
  trabajar con ellos como una unidad
- *Enviroment*. Ambiente, entorno de trabajo donde el desarrollador obtiene los servicios necesarios
  para desarrollar software
- *CLI*. Interfaz de línea de comandos, se utiliza para intercatuar con software y con el SO
- *REPL*. Acrónimo que signica Read, Eval, Print, Loop, es un entorno por consola que permite
  ejecutar intrucciones y/o comandos
- *Shell*. Término usado en informática para referirse a un intérprete de comandos. Mediante
  instrucciones que aporta el intérprete, el usuario puede comunicarse con el kernel y por
  extensión, ejecutar dichas órdenes, así como herramientas que le permiten controlar el
  funcionamiento del sistema
- *Bash*. Acrónimo de Bourne-again shell, es un intérprete de órdenes, es un superconjunto de sh
  (Bourne Shell es un programa informático cuya función consiste en interpretar órdenes basadas en
   POSIX. Incorpora características como control de procesos, redirección de entrada/salida, listado
  y lectura de ficheros, protección, comunicaciones y un lenguaje de órdenes para escribir programas
  por lotes o “scripts”)
- *Stringfy*. Método con el que un objeto o valor se convierte en una cadena de texto JSON
- *Serialización*. Proceso de convertir un tipo de dato A a un tipo de dato B a través de un flujo
  de red o un flujo hacia un archivo
- *ORM*. acrónimo de Object Relational Mapping, es una técnica de programación para convertir datos
  entre el sistema de tipos utilizado en un lenguaje de programación orientado a objetos y la
  utilización de una base de datos relacional como motor de persistencia
- *Hooking*. Técnicas utilizadas para alterar o aumentar el comportamiento de un sistema operativo,
  de aplicaciones o de otros componentes de software interceptando llamadas de función, mensajes o
  eventos pasados entre componentes de software.
- *Hardening o endurecimiento*. Es el proceso de asegurar un sistema reduciendo sus vulnerabilidades
  o agujeros de seguridad, para los que se está más propenso cuanto más funciones desempeña
- *Ofuscación*. Se refiere a hacer ilegible el código sin afectar su funcionalidad. Las técnicas
  utilizadas para ocultar el código de esta manera varían considerablemente. Abarcan desde la
  sustitución de nombres legibles en el código por alternativas difíciles de descifrar (ofuscación
  de nombre) hasta la modificación de la estructura lógica del código para hacerlo menos predecible
  y rastreable (ofuscación de flujo de control). Otra técnica consiste en la conversión de
  expresiones aritméticas y lógicas simples en equivalentes complejas (ofuscación aritmética).
	- Al sustituir todos los nombres de las variables y de las funciones por nombres de una sola
	  letra, es prácticamente imposible comprender el código del programa. En ocasiones, también se
	  utilizan ofuscadores de este tipo con el propósito de reducir el tamaño del código fuente
- *Encriptación* Garantiza que el código y los datos de la aplicación no se puedan acceder mientras
  la aplicación está en reposo. El código encriptado es descifrado inmediatamente cuando se ejecuta
  la aplicación, lo que garantiza que funcione según lo previsto. Para ser efectiva, la encriptación
  debe aplicarse en varias capas. Las técnicas de encriptación esenciales incluyen la encriptación
  de cadenas, encriptación de clases, encriptación de asset y encriptación de recursos.
- *ETL - Extract, Transform and Load*. Proceso que permite a las organizaciones mover datos desde
  múltiples fuentes, reformatearlos y limpiarlos, y cargarlos en otra base de datos, *data mart*, o
  *data warehouse* para analizar, o en otro sistema operacional para apoyar un proceso de negocio.
- *Capa de servicio*, *de dominio*, *de aplicación*, *de negocio*. En arquitectura de software y
  dependiendo el autor, se refiere a la sección del proyecto donde se encuentra el código fuente que
  es la razón de existir de la aplición (solución de software)
- SLA (acuerdo de nivel de servicio). Acuerdo entre el proveedor y el cliente que define las
  métricas cuantificables, como el tiempo de actividad, tiempo de respuesta y las responsabilidades
- SLO (objetivo de nivel de servicio). Define un valor objetivo de una métrica en particular durante
  un periodo de tiempo determinado. Un ejemplo real de un SLO es un 99,99 % de tiempo de actividad
  durante 30 días, se mide el tiempo de inactividad que experimenta el servicio durante un mes para
  asegurar de que sea inferior a 4.32 minutos
- SLIs (Indicador de nivel de servicio). Ees la métrica utilizada para determinar si el SLO se est
  cumpliendo o no. Es el valor medido de la métrica descrita en el SLO en un momento dado. Para
  cumplir con el SLA, el valor del SLI siempre debe cumplir o superar el valor del SLO

## Buenas prácticas
- Variables
	- Nombrar las va. con sentido (que sean autodescriptivas) que indiquen el dato que está
	  almacenando. ¡No nos cobran por caracter!
	- Convención (notación) de nombres para variables:
		- *Camel Case*. Combina las palabras directamente, sin usar ningún símbolo, estableciendo
		  que la primera letra de cada palabra esté en mayúscula: `miVariable` (Lower Camel Case),
		   `DatoNombre` (Upper Camel Case)
		- *Snake Case*. Combina las palabras usando un guión bajo `_` como nexo: `mi_variable`
		- *Kebab Case*. Combina las palabras usando un guión `-` como nexo. Las letras están en
		  minúscula. Es el estándar que se usa en la creación de URLs: `mi-variable`
		- *Notación Húngara*. Cuando se tienen arreglos de datos o el mismo dato con diferentes
		  tipos, se puede identificar con un prefijo en el nombre de la va. haciendo referencia a
		  dicho tipo: `lstPersonas` - lista de personas, `arrPersonas` - arreglo de personas,
		  `iNumero` - Numero entero, `sNumero` - Numero como texto
		- En caso de utilizar constantes, nombrarlas con mayúsculas (*Upper Case* \+ *Snake Case*) o
		  con algún prefijo (*Upper Case* \+ *Notación Húngara*)
	- Evitar usar o tener demasiadas variables globales
	- Recomendación: declarar las va. a utilizar al principio de la función
- Funciones
	- Tener en promedio en el bloque de código aproximadamente 20 instrucciones
	- Tener un nombre descriptivo de lo que hace la función
	- Dedicarse a un único objetivo. Si se requiere lógica adicional a lo que indica que realiza la
	  función, utilizar otra función. Estas funciones adicionales se recomienda colocar debajo de la
	  función que las invoca
	- Evitar anidar demasiadas sentencias de control condicional, se vuelve poco legible el códig
- Dcoumentar
	- Evitar comentarios o redundantes. Si la va./función ya tiene un nombre descriptivo no es
	  necesario comentar a que hace referencia
	- Evitar bloques de código. Tener código comentado mezclado con código funcional vuelve ilegible
	  la comprensión de este


## Versionamiento Semántico (VerSem)
Divide el número de cada versión en tres segmentos numéricos, que tienen el propósito de indicar el
estado y la compatibilidad de una pieza de software: `cambiosMayores.características.parches`
- *La parte más pequeña o el segmento de los parches*. Este número se usa para indicar que no se
  está introduciendo nueva funcionalidad en ella. Comúnmente se usa cuando se corrigen errores
  dentro de esta o cualquier otro cambio que no modifique la apariencia "externa" de una API. Este
  número puede cambiar con rapidez a medida que se resuelven errores o casos excepcionales en el
  código.
- *Segmento de los cambios menores o características*. Se usa para indicar que se le ha añadido
  funcionalidad nueva a la biblioteca pero que nada de lo anterior dejará de funcionar de la manera
  en la que ya lo hace. Es decir, mientras que la apariencia exterior de la biblioteca versionada ha
  cambiado, lo que antes se conectaba con ella, puede seguir haciéndolo sin problema. Si la versión
  menor cambia, el número de parches debe ser reestablecido a 0.
- *Componente de cambios mayores o de ruptura*. Se emplea para indicar cambios tanto externos como
  internos que resultan en hacer que el software no sea compatible con versiones anteriores. Se
  llama *de ruptura* puesto que si la persona que usa una biblioteca actualiza descuidadamente la
  versión, probablemente encontrará muchos errores y cosas inservibles en su código.

### Especificación de Versionado Semántico
En el documento original se usa el **RFC 2119** para el uso de las palabras *MUST*, *MUST NOT*,
*SHOULD*, *SOULD NOT* y *MAY*. Para que la traducción sea lo más fiel posible, MUST se traduce como
el verbo *deber en presente* (DEBE, DEBEN), *SHOULD* como el verbo *deber en condicional* (DEBERÍA,
DEBERÍAN) y el verbo *MAY* como el verbo *PODER*.
1. El software que use Versionado Semántico DEBE declarar una API pública. Esta API puede ser
  declarada en el código mismo o existir en documentación estricta. De cualquier manera, debería ser
  precisa y completa.
1. Un número normal de versión DEBE tomar la forma X.Y.Z donde X, Y, y Z son enteros no negativos.
  X es la versión “major”, Y es la versión “minor”, y Z es la versión “patch”. Cada elemento DEBE
  incrementarse numéricamente en incrementos de 1.
	- Por ejemplo: 1.9.0 -> 1.10.0 -> 1.11.0.
1. Una vez que un paquete versionado ha sido liberado (release), los contenidos de esa versión NO
  DEBEN ser modificadas. Cualquier modificación DEBE ser liberada como una nueva versión.
1. La versión major en cero (0.y.z) es para desarrollo inicial. Cualquier cosa puede cambiar en
  cualquier momento. El API pública no debiera ser considerada estable.
1. La versión 1.0.0 define el API pública. La forma en que el número de versión es incrementado
  después de este release depende de esta API pública y de cómo esta cambia.
1. La versión patch Z (x.y.Z | x > 0) DEBE incrementarse cuando se introducen solo arreglos
  compatibles con la versión anterior. Un arreglo de bug se define como un cambio interno que
  corrige un comportamiento erróneo.
1. La versión minor Y (x.Y.z | x > 0) DEBE ser incrementada si se introduce nueva funcionalidad
  compatible con la versión anterior. Se DEBE incrementar si cualquier funcionalidad de la API es
  marcada como deprecada. PUEDE ser incrementada si se agrega funcionalidad o arreglos considerables
  al código privado. Puede incluir cambios de nivel patch. La versión patch DEBE ser reseteada a 0
  cuando la versión minor es incrementada.
1. La versión major X (X.y.z | X > 0) DEBE ser incrementada si cualquier cambio no compatible con
  la versión anterior es introducida a la API pública. PUEDE incluir cambios de niver minor y/o
  patch. Las versiones patch y minor DEBEN ser reseteadas a 0 cuando se incrementa la versión major.
1. Una versión pre-release PUEDE ser representada por adjuntar un guión y una serie de
  identificadores separados por puntos inmediatamente después de la versión patch. Los
  identificadores DEBEN consistir solo de caracteres ASCII alfanuméricos y el guión. Las versiones
  pre-release satisfacen pero tienen una menor precedencia que la versión normal asociada.
	- Ejemplos: 1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7, 1.0.0-x.7.z.92.
1. La metadata de build PUEDE ser representada adjuntando un signo más y una serie de
  identificadores separados por puntos inmediatamente después de la versión patch o la pre-release.
  Los identificadores DEBEN consistir sólo de caracteres ASCII alfanuméricos y el guión. Los
  meta-datos de build DEBIERAN ser ignorados cuando se intenta determinar precedencia de versiones.
  Dos paquetes con la misma versión pero distinta metadata de build se consideran la misma versión.
	- Ejemplos: 1.0.0-alpha+001, 1.0.0+20130313144700, 1.0.0-beta+exp.sha.5114f85.
1. La precedencia DEBE ser calculada separando la versión en major, minor, patch e identificadores
  pre-release en ese orden (La metadata de build no figuran en la precedencia). Las versiones major,
  minor, y patch son siempre comparadas numéricamente. La precedencia de pre-release DEBE ser
  determinada comparando cada identificador separado por puntos de la siguiente manera: los
  identificadores que solo consisten de números son comparados numéricamente y los identificadores
  con letras o guiones son comparados de acuerdo al orden establecido por ASCII. Los identificadores
  numéricos siempre tienen una precedencia menor que los no-numéricos.
	- Ejemplo: 1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0.


## Sobre paradigmas

### Funcional
- Centrado en funciones, son ciudadanos de primera clase.
- Función de orden superior. Pueden recibir o retornar funciones.
- Principales operaciones: *map* (transformación de un valor a otro), *reduce* (acumulación de
  elementos), *filter* (criterios de elegibilidad  de elementos de una colección para introducirlos
  en otra)
- Utiliza recursividad en lugar de iteración
- No existe la mutabilidad de una variable asignada declarada dentro de un bloque de código
- No almacena estados. Al llamar a una función multiples veces con las mismas entrdas siempre
  devolverá los mismos resultados, estos no se verán influenciados por condiciones externas o
  estados almacenados previamente. También se le conoce como *transparencia referencial*,
- Útil en procesamiento paralelo
- Suelen ser declarativo: se le dice al programa que hacer pero no como

### Reactiva
- Útil en procesos asíncronos, flujo asíncronos de datos
- Una forma de implementar el patrón de diseño Observer
- Obsevables. Flujos de datos, añade suscriptores al flujo de datos
- Observadores. Módulos que consumen los flujos de datos. Implementan 3 métodos: reaccionar al
  siguiente valor, reaccionar a un error, reaccionar al informe de término del flujo de datos

## Cuando refactorizar
- Refactorizar después de 3 implementaciones de un mismo código. Posteriormente se utiliza el patrón
  DRY. Útil con equipos de desarrollo pequeños
- Evaluación de costos operacionales: La refactorización...
	1. ¿... Hará que la funcionalidad a implementar se implemente más rápido (inclyendo la
	  refactorización)?
	1. ¿... Permitirá corregir errores más rápido?
	1. ¿Errores triviales toman días en resolveerse por la complejidad del código? ¿Sería mejor una
	  re implementación?
	1. ¿El equipo entederá la refactorización?
	1. ¿... Hará que consigas más clientes?
	1. ¿... Mejorará el rendimiento de la app de una manera notable? Si el rendimiento no es
	  problema, desctar la refactorización
	- Si la respuesta a todas las preguntas es "no", considerar no proceder con la refactorización
- Se deben tener razones de peso u obtener un beneficio para realizarla
- Se deben tener pruebas automáticas preparadas previamente, con una covertura del 100% para evitar
  introducir fallas en el sistema


## Deuda Tecnica
- Definición: Inherente al desarrollo de software cuando su ciclo no se rige por estándares. No es
  un defecto visible por lo que muchas veces no es fácil de detectar. Surge como consecuencia de la
  urgencia de desarrollo dejando de lado la calidad, y la acumulación de estos defectos generan
  intereses.
- Ejemplos
	- Alta complejidad en código fuente
	- Falta de pruebas de integración o automatizadas
	- Fragmentos de código o módulos duplicados
	- Lanzar un producto rápido
	- Reparar un bug
- Causas
	- Falta de gestión en el proceso de calidad del software
	- Presión por lanzar el producto al mercado
	- Falta de documentación y comunicación entre desarrolladores
	- No utilización de patrones de diseño o arquitecturas de software
- Costos
	- Más desarrolladores para cumplir con los objetivos de desarrollo
	- Más tiempo en el desarrollo por no haber considerado los componentes que la contienen
	- Pérdida de clientes por el bajo performance de la aplicación
	- Falta de productividad
- Prevención
	- No realizar soluciones complejas a problemas sencillos
	- No utilizar arquitecturas poco escalables
	- Utilizar control de versiones
	- Documentar los cambios realizados
	- Utilizar estándar dentro del equipo de desarrollo cuando se presenten nuevos requerimientos,
	  bugs, eventualidades y otros elementos del proceso de desarrollo
	- Utilizar metodologías ágiles
- No es posible deshacerse de ella pero sí es posible controlarla, por ello no es algo
  necesariamente malo siempre que exista un plan para pagarla


## Licencias de Software Open Source
- Normalmente en la raiz del proyecto se crea el archivo "LICENSE", que describe que se puede y que
  no se puede hacer con el código fuente del proyecto
- Para elegir una licencia se debe tener en cuenta el alcance que la comunidad puede tener acceso
  con el código o que tan específico se desea ser con estos permisos
- Tipos de licencias
	- **MIT**: Sin ninguna restricción (simple y permisivo), tiene permiso de uso comercial o
	  privado, para modificarlo y distribuirlo, con la condición de que se coloque una copia de la
	  licencia en el código. El autor no se hace responsable del uso que se le dé al código fuente.
	  p.ej. .NET Core, Laravel, Angular
	- **Apache License 2.0**: Pensado cuando se tiene una preocupación por las patentes, tiene
	  permiso de uso comercial o privado, para modificarlo y distribuirlo, el contribuyente tiene
	  uso de las patentes del código, con las condiciones de incluir una copia de la licencia en el
	  código e indicar los cambios realizados. El autor no se hace responsable del uso que se le dé
	  al código fuente, tiene protección de "trademark", es decir, no se puede utilizar el nombre
	  del proyecto/biblioteca en el producto de software que lo utiliza. p.ej. Android, Apache, Swift
	- **GNU GPL v3**: Pensado cuando el objetivo es compartir mejoras en el código y que el proyecto
	  siga siendo abierto. Mismos permisos de Apache License 2.0, con las condiciones que debe
	  mantener el código abierto, utilizar la misma licencia, incluir la licencia del código
	  original, indicar cambios que se hayan producido. El autor no se hace responsable del uso que
	  se le dé al código fuente. p.ej. Gimp
- Para tener un contexto más amplio para seleccionar la licencia que mejor se adapte a las
  necesidades del proyecto, consultar [el siguiente sitio](choosealicense.com)

## Tipos de malware
- **Adware**
- **Scareware**: alerta exagerada para comprar una solución
- **Spyware**
- **Virus**: estropear un equipo, transmitirse a otras computadoras
- **Gusano**: se reproduce sin control hasta llegar al fallo del sistema
- **Troyano**: programa que se disfraza de otro programa, es un modo de transferirse. Buscan abrir
  una puerta trasera
- **Riskware**: usuarios lo instalan propiamente pero pueden ser muy vulnerables por su
  funcionalidad o por como se desarrolló
- **Ransomware**

