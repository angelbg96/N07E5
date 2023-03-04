# Maven
- Es una herramienta de gestión de dependencias de software de Java
- La estructura con que crea el proyecto es estándar, cualquier IDE puede abrir y trabajar con el proyecto
- Tiene un repositorio de dependencias de donde las descarga
- Descarga las dependencias que le indiquen de forma automática de forma automática
- Viene de forma embebida en IDE's de desarrollo como en Eclipse, NetBeans, Intelij IDEA

## Requerimientos
- Se debe instalar en PC (en Spring viene embebido)
- Crear 2 va. de entorno (*M2_HOME* y *MAVEN_HOME*) y referenciar a donde se instaló
- En variable *PATH* agregar una nueva referencia *%M2_HOME%/bin*

## Primeros pasos
- Revisar en consola si se reconoce el comando `mvn --version`
- Para crear un nuevo proyecto desde Maven, se utiliza el comando:
	- `mvn` 
    - `archetype:generate` : crear un nuevo proyecto, antes era *create*
    - `-DgroupId=nombre.nombre.nombre` : Estrcutura que va a tener el proyecto, lo va a diferenciar de otros proyectos!
    	- La convención dice que si tu app es *app.dominio.com*, tu *groupId* será invertido *com.dominio.app*
    - `-DartifactId=nombreId` : Nombre del compilado del proyecto (JAR o WAR)
    - `-DarchetypeArtifactId=maven-archetype-tipoProyecto` : Crear el proyecto según la estructura que se requiera
    	- `archetype` : un proyecto Java simple
        - `webapp` : una aplicación web
    - Al dar Enter, se puede cambiar el número de la versión
    - Pregunta para confirmar si los campos con los que se creó el proyecto son correctos, de ser así, escribir *Y*
    - `-DinteractiveMode=false` : Crea el proyecto sin hacer las preguntas mencionadas anteriormente
    
## Compilando
- Para compilar el proyecto se usa el comando `mvn compile`, el cual creará los binarios del código fuente Java y los pondrá en un directorio llamado *target*
- Para empaquetar el proyecto se usa `mvn package`, genera el compilado JAR o WAR
- Para limpiar el directorio *target*, se utiliza `mvn clean`
- Para limpiar los archivos que genera el IDE Eclipse para manejar el proyecto se usa `mvn eclipse:clean`
- Para ejecutar el proyecto `java -cp nombreJar.jar paquete.paquete.App` : Indicar el paquete donde se encuentra el método `main()`

## Archivo pomp.xml
- Project Object Model
- Archivo de descripción que indica como Maven realiza la compilación y empaquetamiento de la app
- Tiene la descripción de algunas propiedades
- En la sección `dependencies` , se agregan las librerías que se requieren en el proyecto
- En la sección `build` está la descripción que utiliza Maven para compilar el proyecto

### Scope de las dependencias
- **compile** : Por defecto, disponible en el classpath del proyecto
- **provided** : Similar a *compile*, indica que se espera que una JDK o contenedor provee la librería en tiempo de ejecución
- **runtime** : La librería no es necesaria en tiempo de compilación pero sí para la ejecución
- **test** : La librería es utilizada para fines de pruebas
- **system** : Similar a *provided*, excepto que se debe indicar el JAR de forma más explícita
- **import** : Dependencias de tipo *pom*

### Sección properties
- Se especifica la versión del JDK con el que se está escribiendo el código fuente `maven.compiler.source` y con el que se va a compilar `maven.compiler.target`

#### Perfiles
- Crear un perfil para diferentes entornos: desarrollo, producción, qa, etc
- En la sección `properties` declarar el nombre del perfil. Recomendación que sea lo más descriptivo posible
	- `<nombreVar> valor </nombreVar>`
	- p.ej. `<env>environment</env>`
    - Esta sección se enlaza con los archivos de propiedades que se estén definidos en el directorio resources
    - Se puede crear una sección `build` con una subsección filtros de la siguiente manera
    	- `filters` dentro especificar
        - `filter` = src/main/resources%{nombreVar}.properties
        - Al momento de compilar el proyecto, solamente tomará en cuenta el archivo properties que corresponda con el perfil indicado
    - En la sección `profiles` especificar los perfiles de como se desea compilar el proyecto
    	- `profile` dentro especificar
        - `id` = idPerfil
        - `properties` dentro especificar la variable del perfil para compilar el archivo de propiedades correspondiente
        	- `nombreVar` = valorVar.perfil
        - Puede tener su propia sección de `build` para compilar pugins específicos de ese perfil
- Ejecutar con el IDE
	- *Run As* > *Maven Build* y se selecciona el perfil específico con el que se desea compilar
- Ejecutar desde línea de comandos
	- `mvn -P idPerfil package`
	

## Comando install
- Generar una dependencia de un proyecto con otro
- El proyecto que se quiere exportar, se le aplica un `clean` y luego `mvn install`
- El proyecto se instala en el directorio de dependencias que ha descargado/instalado Maven
- En el *pomp* del proyecto que desea consumir o utilizar el otro proyecto, se especifica la nueva dependencia:
	- `dependency` dentro especificar
    - `groupId` = groupDelPryecto
    - `artifactID` = nombreDelArtefacto
    - `version` = versionDelProyectoAImportar
- Si se realizan cambios en el proyecto a exportar y se cambia la versión del proyecto, se debe volver a ejecutar el `mvn install`

## Varios archivos *pomp*
- Para tener una configuración específica en cada archivo
- Ejecutar en IDE
	- *Run As* > *Maven Build* en *goals* escribir **-f nombrePomp.xml**
    - Seguido, especificar la acción que se quiere hacer **install** / **package**
- Ejecutar desde línea de comandos
	- Realizar primero un *clean*
    - `mvn -f nombrePomp.xml accion`
    - *accion* : puede ser un *package* o *install*

## Dependencias transitorias
- Son aquellas dependencias que requiere una librería que se declara en el *pomp*
- p.ej. jUnit requiere 3 dependencias para funcionar

## Excluir dependencias
- Útil cuando se está buscando la razón de algún conflicto o implementación de un requerimiento
- Si se da un `ctrl + click` en el *groupId* o en *artifactId* de una dependecia, se revisa el archivo *pomp* donde se ven detalles de la depedencia y de sus dependencias transitorias
- Para excluir una dependencia en la sección `dependencies` escribir dentro de la sección `depency` específica
	- `exclusions` dentro especificar
    - `exclusion` dentro espeficar
    - `groupId` = group.subdependencia
    - `artifactId` = idSubDependencia

## Documentación
- En la carpeta *target* se crea un stio web donde se documenta las dependencias que contiene el proyecto
- En el archivo *pomp.xml* agregar en la sección `build` el plugin `site`
- En ventana de comandos ejecutar `mvn site`
- Si se quiere que esa documentación esté en varios idiomas (internacionalización), dentro de la sección `plugin` de *site* agregar
	- `configuration` dentro especificar
    - `locales` = en, es, fr
    - Se ponen todos los idiomas que se quiera mostrar la documentación separados por comas
- Existe un plugin para agregar documentación del JavaDoc
