# Maven
- Es una herramienta de gestión de dependencias de software de Java
- La estructura con que crea el proyecto es estándar, cualquier IDE puede abrir y trabajar con el proyecto
- Tiene un repositorio de dependencias de donde las descarga
- Descarga las dependencias que le indiquen de forma automática de forma automática
- Viene de forma embebida en IDE's de desarrollo como en Eclipse, NetBeans, Intelij IDEA

## Requerimientos
- Se debe instalar en PC (en Spring viene embebido)
- Crear 2 va. de entorno (_M2\_HOME_ y _MAVEN\_HOME_) y referenciar a donde se instaló
- En variable _PATH_ agregar una nueva referencia _%M2_HOME%/bin_

## Primeros pasos
- Revisar en consola si se reconoce el comando `mvn --version`
- Para crear un nuevo proyecto desde Maven, se utiliza el comando:
	* `mvn` 
    * `archetype:generate` : crear un nuevo proyecto, antes era _create_
    * `-DgroupId=nombre.nombre.nombre` : Estrcutura que va a tener el proyecto, lo va a diferenciar de otros proyectos!
    	+ La convención dice que si tu app es _app.dominio.com_, tu _groupId_ será invertido _com.dominio.app_
    * `-DartifactId=nombreId` : Nombre del compilado del proyecto (JAR o WAR)
    * `-DarchetypeArtifactId=maven-archetype-tipoProyecto` : Crear el proyecto según la estructura que se requiera
    	- `archetype` : un proyecto Java simple
        - `webapp` : una aplicación web
    * Al dar Enter, se puede cambiar el número de la versión
    * Pregunta para confirmar si los campos con los que se creó el proyecto son correctos, de ser así, escribir _Y_
    * `-DinteractiveMode=false` : Crea el proyecto sin hacer las preguntas mencionadas anteriormente
    
## Compilando
- Para compilar el proyecto se usa el comando `mvn compile`, el cual creará los binarios del código fuente Java y los pondrá en un directorio llamado _target_
- Para empaquetar el proyecto se usa `mvn package`, genera el compilado JAR o WAR
- Para limpiar el directorio _target_, se utiliza `mvn clean`
- Para limpiar los archivos que genera el IDE Eclipse para manejar el proyecto se usa `mvn eclipse:clean`
- Para ejecutar el proyecto `java -cp nombreJar.jar paquete.paquete.App` : Indicar el paquete donde se encuentra el método `main()`

## Archivo pomp.xml
- Project Object Model
- Archivo de descripción que indica como Maven realiza la compilación y empaquetamiento de la app
- Tiene la descripción de algunas propiedades
- En la sección `dependencies` , se agregan las librerías que se requieren en el proyecto
- En la sección `build` está la descripción que utiliza Maven para compilar el proyecto

### Scope de las dependencias
- __compile__ : Por defecto, disponible en el classpath del proyecto
- __provided__ : Similar a _compile_, indica que se espera que una JDK o contenedor provee la librería en tiempo de ejecución
- __runtime__ : La librería no es necesaria en tiempo de compilación pero sí para la ejecución
- __test__ : La librería es utilizada para fines de pruebas
- __system__ : Similar a _provided_, excepto que se debe indicar el JAR de forma más explícita
- __import__ : Dependencias de tipo _pom_

### Sección properties
- Se especifica la versión del JDK con el que se está escribiendo el código fuente `maven.compiler.source` y con el que se va a compilar `maven.compiler.target`

#### Perfiles
- Crear un perfil para diferentes entornos: desarrollo, producción, qa, etc
- En la sección `properties` declarar el nombre del perfil. Recomendación que sea lo más descriptivo posible
	* `<nombreVar> valor </nombreVar>`
	* p.ej. `<env>environment</env>`
    * Esta sección se enlaza con los archivos de propiedades que se estén definidos en el directorio resources
    * Se puede crear una sección `build` con una subsección filtros de la siguiente manera
    	+ `filters` dentro especificar
        + `filter` = src/main/resources%{nombreVar}.properties
        + Al momento de compilar el proyecto, solamente tomará en cuenta el archivo properties que corresponda con el perfil indicado
    * En la sección `profiles` especificar los perfiles de como se desea compilar el proyecto
    	+ `profile` dentro especificar
        + `id` = idPerfil
        + `properties` dentro especificar la variable del perfil para compilar el archivo de propiedades correspondiente
        	- `nombreVar` = valorVar.perfil
        + Puede tener su propia sección de `build` para compilar pugins específicos de ese perfil
- Ejecutar con el IDE
	* _Run As_ > _Maven Build_ y se selecciona el perfil específico con el que se desea compilar
- Ejecutar desde línea de comandos
	* `mvn -P idPerfil package`
	

## Comando install
- Generar una dependencia de un proyecto con otro
- El proyecto que se quiere exportar, se le aplica un `clean` y luego `mvn install`
- El proyecto se instala en el directorio de dependencias que ha descargado/instalado Maven
- En el _pomp_ del proyecto que desea consumir o utilizar el otro proyecto, se especifica la nueva dependencia:
	* `dependency` dentro especificar
    * `groupId` = groupDelPryecto
    * `artifactID` = nombreDelArtefacto
    * `version` = versionDelProyectoAImportar
- Si se realizan cambios en el proyecto a exportar y se cambia la versión del proyecto, se debe volver a ejecutar el `mvn install`

## Varios archivos _pomp_
- Para tener una configuración específica en cada archivo
- Ejecutar en IDE
	* _Run As_ > _Maven Build_ en _goals_ escribir __-f nombrePomp.xml__
    * Seguido, especificar la acción que se quiere hacer __install__ / __package__
- Ejecutar desde línea de comandos
	* Realizar primero un _clean_
    * `mvn -f nombrePomp.xml accion`
    * _accion_ : puede ser un _package_ o _install_

## Dependencias transitorias
- Son aquellas dependencias que requiere una librería que se declara en el _pomp_
- p.ej. jUnit requiere 3 dependencias para funcionar

## Excluir dependencias
- Útil cuando se está buscando la razón de algún conflicto o implementación de un requerimiento
- Si se da un `ctrl + click` en el _groupId_ o en _artifactId_ de una dependecia, se revisa el archivo _pomp_ donde se ven detalles de la depedencia y de sus dependencias transitorias
- Para excluir una dependencia en la sección `dependencies` escribir dentro de la sección `depency` específica
	* `exclusions` dentro especificar
    * `exclusion` dentro espeficar
    * `groupId` = group.subdependencia
    * `artifactId` = idSubDependencia

## Documentación
- En la carpeta _target_ se crea un stio web donde se documenta las dependencias que contiene el proyecto
- En el archivo _pomp.xml_ agregar en la sección `build` el plugin `site`
- En ventana de comandos ejecutar `mvn site`
- Si se quiere que esa documentación esté en varios idiomas (internacionalización), dentro de la sección `plugin` de _site_ agregar
	* `configuration` dentro especificar
    * `locales` = en, es, fr
    * Se ponen todos los idiomas que se quiera mostrar la documentación separados por comas
- Existe un plugin para agregar documentación del JavaDoc
