# Desarrollo de Scripts bash

- Su extensión es _.sh_ y debe tener permisos de ejecución
- El script debe incluir un "shebang line" como su primera línea, debe comenzar con los caracteres `#!` y debe especificar la ruta en la que se encuentra el intérprete. Si se usa bash es `#!/bin/bash`. Si se usa `#!/bin/sh`, esto es un enlace simbólico que apunta al intérprete configurado por default (suele ser bash)
- Alto manejo de las entradas y salidas estándar _stdin_, _stdout_, _stderr_
- Cada instrucción en una línea
- Respetar la sintaxis descrita para un correcto funcionamiento


## Variables
Para realizar asignaciones :
- `nombreVar='valor'` | \`valor\` : Asigna texto. Con las comillas invertidas se escapan mejor comillas simples y dobles
- `nombreVar="valor"` : Asigna texto, si hay una variable, la referencia a un directorio o un fichero, interpreta su valor
- `nombreVar=$(comando)` | `nombreVar=`\`comando\` : Asigna el valor que retorna el comando
- `nombreVar=n` | `let nombreVar=n` : Asignar un valor numérico. Recomendable usar _let_
- `export nombreVar` : Exporta el valor de la variable como va de entorno

Para utilizarla : 
- `comando $nombreVar`
- `otraVar="valor $nombreVar"`

## Arrays
- `nombreArr=(elem1 elem2 elem3)` | `declare -a nombreArr=(elem1 elem2 elem3)` : Declaración del array definiendo sus elementos
- `${nombreArr[@]}` | `${nombreArr[*]}` : mostrar todos los elementos del array
- `${nombreArr[i]}` : De esta forma se acceden al elemento 'i' del aray, si se desea modificar se asigna el nuevo valor como cualquier otra variable
- `${!nombreArr[*]}` : Se obtienen los índices de todos los elementos del array
- `${#nombreArr[*]}` : Se obtiene el tamaño del array, si se sustituye '*' por algún índice, se obtiene la longitud del elemento en esa posición
- Si se desea asignar rangos de caracteres se utilizan las expresiones : `nombreArray=( {A..Z} {a..z} {0..9} )`
- `nombreArr=(`\`comando\``)` : Asignar resultado de la ejecución de un comando en un array
- `nombreArr+=(elem5 eleme6)` : Agregar nuevos elementos al array
- `arr1=(${arr1[*]} ${arr2[*]} elemX elemY)` : Agregar todos los elementos de un array dentro de otro, además de agrear elementos independientes en la misma expresión
- `unset nombreArr[i]` : Eliminar del array el elemento del indice 'i'. Si no se especifica el índice, se borra todo el array

## Operaciones

### Numericas
- Son envueltas por `$((operaciones))`
- Soporta `+`, `-` , `*`, `/`, `%` (resto), ** (potenciación)
- Aplicables entre literales y variables numéricas
~~~ bash
var1=$((8*7))
var2=$((3 ** $var1%2))
~~~

### Texto
- Son envueltas por `${operaciones}`
- `${#cadena}` : Longitud de una cadena
- `${cadena,,}` : Convertir una cadena a minúsculas
- `${cadena,}` : Convertir la primera letra de una cadena a minúsculas
- `${cadena^^}` : Convertir una cadena a mayúsculas
- `${cadena^}` : Convertir la primera letra de una cadena a mayúsculas
- Extraer una parte de la cadena `${cadena:posición:longitud}`
    * `${cadena:0:1}` : Primer caracter del contenido de la cadena
    * `${cadena:7}` : Desde la posición 7 al final de la cadena
    * `${cadena: -4}` : Últimos 4 caracteres de la cadena. __IMPORTANTE__ notar el espacio antes del número negativo
    * `${cadena: -4:2}` : Desde los últimos 4 caracteres de la cadena, extrae los primeros 2. __IMPORTANTE__ notar el espacio antes del número negativo
- Borrar subcadenas. Se pueden utilizar con `*` al principio, intermedio o final
    * `${cadena#subcadena}` : Borra la coincidencia más corta de subcadena desde el principio de cadena
    * `${cadena##subcadena}` : Borra la coincidencia más larga de subcadena desde el principio de cadena
    * `${cadena%subcadena}` : Borra la coincidencia más corta de subcadena desde el final de cadena
    * `${cadena%%subcadena}` : Borra la coincidencia más larga de subcadena desde el final de cadena
- Reemplazar subcadena
    * `${cadena/buscar/reemplazar}` : Sustituye la primera coincidencia de buscar con reemplazar
    * `${cadena//buscar/reemplazar}` : Sustituye todas las coincidencias de buscar con reemplazar
    * `${cadena/buscar}` : Quitar la primera aparición de una subcadena en una cadena
    * `${cadena//buscar}` : Quitar todas las apariciones de una subcadena en una cadena


## Entrada y Salida de datos
- `echo mensaje` | `echo "mensaje"` : Envia texto a la salida estándar, se puede redirigir a _stderr_
- `read var1 var2 varN` : Obtiene el texto ingresado desde la línea de comandos. Si se ingresan más de un dato, se separan por espacios desde el _prompt_
- `exit` : Comando para terminar la ejeción del programa


## Ejecutar con parámetros
- `./programa.sh param1 param2 paramN` :Cada parámetro se separa por un espacio
- `$n` : Para utilizar los parámetros dentro del programa se utiliza la notación de variables, donde n=0, 1, 2, ..., N
    * Cada número positivo hace referencia al número de párametro
    * la variable `$0` hace referencia al parámetro cero y su valor es el nombre del programa ejecutable


## Validaciones de variables
- Con estructura condicional if :
~~~ bash
if [ condiciones ]; then
    comandos
elif [ condiciones ]; then
    comandos
else
    comandos
fi
~~~

- Con estructura condicional switch (Case) :
~~~ bash
case $var in
    caso1)
        comandos;;
    otroCaso)
        comandos;;
    *)
        comandos;;
esac
~~~

### Texto
- `[ -z $var ]` : Comprueba que la cadena tenga longitud cero
- `[ -n $var ]` : Comprueba que la cadena tenga una longitud mayor a cero
- `[ $va1 = $va2 ]` : Comprueba que las cadenas sean iguales
- `[ $va1 != $va2 ]` : Comprueba que las cadenas sean diferentes
- `[[ $va1 < $va2 ]]` | `[ $va1 /< $va2 ]` : Comprueba que _va1_ sea menor que _va2_
- `[[ $va1 > $va2 ]]` | `[ $va1 /> $va2 ]` : Comprueba que _va1_ sea mayor que _va2_

### Númericas
- `[ $n1 -eq $n2 ]` : Comprueba que los números sean iguales
- `[ $n1 -ne $n2 ]` : Comprueba que los números sean diferentes
- `[ $n1 -ge $n2 ]` : Comprueba que el primer número sea mayor o igual que el segundo
- `[ $n1 -gt $n2 ]` : Comprueba que el primer número sea mayor que el segundo
- `[ $n1 -le $n2 ]` : Comprueba que el primer número sea menor o igual que el segundo
- `[ $n1 -lt $n2 ]` : Comprueba que el primer número sea menor que el segundo

### Archivos
- `[ -e $var ]` : Comprueba que el archivo existe en el sistema
- `[ -s $var ]` : Comprueba si existe y no está vacío
- `[ -w $var ]` : Comprueba si existe y es escribible
- `[ -r $var ]` : Comprueba si existe y se puede leer
- `[ -x $var ]` : Comprueba si existe y es ejecutable
- `[ -d $var ]` : Comprueba si existe y es un directorio
- `[ -f $var ]` : Comprueba si existe y es un fichero
- `[ -O $var ]` : Comprueba si existe y es propiedad del usuario actual
- `[ -G $var ]` : Comprueba si existe y el grupo predeterminado es el mismo que del usuario actual
- `[ file $f1 -nt file $f2 ]` : Comprueba que el primer archivo es más nuevo que el segundo
- `[ file $f1 -ot file $f2 ]` : Comprueba que el primer archivo es más antiguo que el segundo

### Variables especiales
- `$?` : Valor que devuelve la ejecución de un comando. 1 si falló, 0 si se ejecutó correctamente
~~~ bash
comando param1 param2

if [ $? -eq 0 ]; then
    echo Comando exitoso
else
    echo Comando fallo
fi
~~~
- `$1` – `$9` : Los primeros nueve argumentos que se pasan a un script en Bash
- `$#` : El número de argumentos que se pasan a un script
- `$@` : Todos los argumentos que se han pasado al script
- `$$` : ID del proceso del script
- `$USER` : Nombre del usuario que ha ejecutado el script
- `$HOSTNAME` : Hostname de la máquina en la que se está ejecutando el script
- `$SECONDS` : Tiempo transcurrido desde que se inició el script, contabilizado en segundos
- `$RANDOM` : Devuelve un número aleatorio cada vez que se lee esta variable
- `$LINENO` : Tndica el número de líneas que tiene el script

### Operadores lógicos
- `[[ condicion1 && condicion2 ]]` | `[ condicion1 -a condcion2 ]` : Operador lógico AND
- `[[ condicion1 || condicion2 ]]` | `[ condicion1 -o condcion2 ]` : Operador lógico OR
- `[[ ! condicion ]]` : Niega el resultado de la condición


## Bucles

### For
- Ciclo iterativo indexado
~~~ bash
for ((i=0; i<= 10; i++)); do
    comandos
done
~~~

- Recorrer una lista, cadena de texto cuyo _split_ son los espacios
~~~ bash
lista="A 1 B 2 texto 3"

for item in $lista; do
    comandos $item
done
~~~

### While
- Como ciclo iterativo indexado, es ejecutado mientras se cumpla la condición
~~~ bash
contador=0

while [ $contador -lt 10 ]; do
    comandos
    let contador=contador+1
done
~~~

### Until
- Similar a _while_, pero se va a ejecutar mientras la condición sea falsa
~~~ bash
contador=0

until [ $contador -gt 10 ]; do
    comandos
    let contador=contador+1
done
~~~

### Select
- Para crear menú de opciones
~~~ bash
opciones="saludar reir salir"

select opc in $opciones; do
    if [ opc = "saludar" ]; then
        comandos
    elif [ opc = "reir" ]; then
        funcion param1 param2
    elif [ opc = "salir" ]; then
        exit
    else
        echo mensaje
    fi
done

~~~


## Funciones
- Estructura
~~~ bash
function nombreFX() {
    comandos
}
~~~
- Usando `nombreFX`
- Si requiere parámetros : `nombreFX param1 param2 paramN`, Utilizando los parámetros dentro de la función, se utilizan con la notación de variables indexadas ($1, $2, $3)


## Debug
- `bash -v script.sh` : Ver el resultado detallado del script línea a línea
- `bash -x script.sh` : Desplegar la información de los comandos que son utilizados, capturando su entrada y salida

