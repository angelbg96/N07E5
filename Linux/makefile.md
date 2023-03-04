# Make

Es un comando que permite ejecutar comandos a partir de *reglas* escritas en un archivo que debe ser nombrado como *makefile*. Está orientado a la compilación de archivos 

## Makefile

### Reglas
Tienen la siguiente sintaxis:
~~~ yaml
nombreRegla: dependencias
    orden
~~~
- `nombreRegla` : U objetivo, identifica el proceso a realizar. Puede ser el nombre de un archivo a obtener
- `dependencias` : O requisitos, son los archivos necesarios para llevar a cabo el procedimiento.
    - Se separan por espacios, si son demasiados requisitos, se pueden poner en varias líneas escapando el salto de línea con `\` al final de cada renglón
- `orden` : O instrucciones, es un comando o grupos de comandos a ejecutar. **NOTA** : antes del comando debe exitir una tabulación

Si una regla requiere de otras reglas para ejecutarse, primero se van a ejecutar esas reglas sin importar el orden de como se hayan escrito

### Variables
Se pueden definir variables para reutilizar y optimizar la escritura de argumentos de comandos o parámetros de la regla. Se definen al principio del archivo
- `nombreVar = valor` : Creación de una variable. Si más adelante se cambia su valor y si hay otras variables que utilizan dicha variable, también se verán afectadas por esta actualización
- `nombreVar := valor` : Creación de una variable de expansión simple, cuando utiliza una variable que después muta, no se verá afectada
- `$(nombreVar)` : Con esta sintaxis se utiliza la variable en la regla
- *Make* reconoce el nombre de algunas variables, y por ende, entiende de que compilación se trata
    - `CC` | `CXX` : Va. que sus valores son `gcc` y `g++` respectivamente, son utilizadas para compilar archivos de programación `C` y `C++`
    - `CFLAGS` | `CPPFLAGS` : Va. cuyo valor sirve para representar parametros de los comandos `gcc` y `g++`, respectivamente
    - `$^` : Va. que reprenta la lista de los requisitos de la regla. Es útil si todos los requisitos son utilizados como parametros en un comando
    - `$@` : Va. que representa el objetivo de la regla. Si el nombre de la regla se llama igual que el archivo que se busca obtener, se puede utilizar como parámetro en el comando
    - Para conocer más variables se puede consultar la [documentación del comando make](https://www.gnu.org/software/make/manual/make.html#Automatic-Variables)

### Otros aspectos
- Cuando se ejecuta este comando, es capaz de reconocer que reglas son necesarias para ejecutarse (recompilación) y cuales otras no lo necesitan (archivos actuales), mediante la comparación de las fechas de modificación, si el archivo objetivo es más antiguo que el archivo requerido, entonces ejecuta la regla
- Para escribir líneas de comentarios, el primer caracter debe ser `#`
- Se pueden incluir otros *makefiles* al archivo actual, para ello se usa `include ruta/makefile`
    - Debe escribirse antes de las reglas
- Se pueden creanr *phony rules*, es decir, una regla fictisia con la cual se van a ejecutar las instrucciones indicadas en la regla. Un uso muy práctico es limpiar los archivos intermedios generados para obtener el archivo final

## Comando
- `make` : Ejecuta la primer regla que se haya escrito
- `make nombreRegla` : Ejecuta la regla especificada

## Ejemplo de un makefile
~~~ yaml
OBJS = main.o testing.o business.o model.o view.o \
controller.o windows.o
CFLAGS = -g -Wall

include ../../dev/controllers/makefile

all: programa

# Esta regla compila el programa principal
programa: $(OBJS)
    gcc -o $@ $(OBJS)
%.o: %.c
    gcc $(CFLAGS) -c $< -o $@

otro.o: otro.c example.h
    $(CC) $(CFLAGS) -c $^ $@

clean:
    rm -f $(OBJS)
~~~