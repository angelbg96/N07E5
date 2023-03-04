# Expresiones Regulares
- Son utilizadas para encontrar un patrón de búsqueda en una secuencia de caracteres
- Las regex suelen tener una sintaxis específica y un conjunto de metacaracteres dependiendo del lenguaje que las implementa, por ejemplo PCRE (Perl-Compatible Regular Expressions) es un estándar definido por el lenguaje de programación Perl, a partir del cual muchas otras implementaciones se han basado en otros lenguajes.

## Operaciones básicas
- **Alternación.** Se define por un pipe ` | ` y reprensar un *or* lógico, le indica al patrón que existe una coincidencia entre cualquiera de los elementos que aparezcan a sus lados
    ~~~ js
    patron1 | patron2
    ~~~
- **Cuantificación.** Se usa para especificar la cantidad de ocurrencias de determinado elemento. Cuenta con varios operadores:
    * ` ? ` indica que el elemento que la antecede puede aparecer cero o una sola vez
        ~~~ js
        patron?
        ~~~
    * ` * ` indica que el elemento que la antecede puede repetirse 0 o más veces
        ~~~ js
        patron*
        ~~~
    * ` + ` parecido al operador estrella(*), solo que en este caso debe existir al menos una ocurrencia del elemento que la precede
        ~~~ js
        patron+
        ~~~
    * `{n, m}` indica el rango de ocurrencias permitido en el patrón, con la posibilidad de que sea igual a N ocurrencias, mayor a N número de ocurrencias o que esté entre N y M ocurrencias
        ~~~ yaml
        N coinicdencias: patron{n}
        más de N coincidencias: patron{n,}
        entre N y M coincidencias: patron{n, m}
        ~~~
- **Agrupación.** Se utilizan los paréntesis `( )`, y sirve para agrupar una secuencia de caracteres o de patrones de búsqueda. Se complementa muy bien con las primeras dos operaciones
    ~~~ yaml
    Ejemplo 1: carateres(patron1|patron2)
    Ejemplo 2: caracteres(patron)*
    Ejemplo 3: caracteres(patron1|patron2)+
    ~~~


## Caracteres
### Rangos de caracteres
- Se utilizan `[ ]` como contenedor, se buscan patrones que contengan alguno de los caracteres especificados dentro del rango
- `a-z` caracteres del alfabeto en minúscula, también existe su equivalente en mayúsculas
- `A-z` caracteres del alfabeto sin importar mayúsculas y mínusculas
- `0-9` caracteres numéricos del cero al nueve
- `À-ÿ` caracteres del alfabeto con tildes, virgulillas, diéresis, acentos circunflejos, etc
- Operador ` ^ ` dentro y al principio del rango, indica que se buscarán todas las coincidencias excepto las indicadas en el rango, es un *not* lógico
~~~ yaml
vocales: [aeiou]
impares: [13579]
extremos del alfabeto: [^h-t]
de 1 a 7: [1-7]
consonantes: [^aeiou]
~~~

### Metacaracteres
- ` . ` indica cualquier caracter pero solo uno
- `\w` solo letras del alfabeto, equivalente a `[a-z]`
- `\W` niguna letra del alfabeto, equivalente a `[^a-z]`
- `\d` solo digitos, equivalente a `[0-9]`
- `\D` ningún número, equivalente a `[^0-9]`
- `\s` solo espacios, saltos de líena y tabulaciones
- `\S` no coincidir con espacios
- `\A`*patron* encontrar un patrón al principio de la cadena
- *patron*`\Z` encontrar un patrón al final de la cadena

### Caracteres de escape
Se usa la barra invertida ` \ ` para mostrar caracteres especiales como tabuladores `\t`, saltos de línea `\n`, caracteres unicode `\u0020` y para representar caracteres que son parte de la sintaxis de RegEx como `[ ( . * + - ? }`


## Delimitadores
- `^`*patron* para encontrar un patrón al principio de la secuencia de carateres
- *patron*`$` para encontrar un patrón al final de la secuencia de carateres
- `^`*patron*`$` la secuencia de carateres debe cumplir exactamente con el patrón de búsqueda


## Modificadores o banderas
- `g`: Global, busca más coincidencias (no sólo la primera) en toda la secuencia de caracteres
- `i`: Insensitive, no distingue entre mayúsculas y minúsculas

