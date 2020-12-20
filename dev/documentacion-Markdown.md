# Esto es Markdown

Con el "#" se crean encabezados
# Equivalente a h1
## Equivalente a h2
### Equivalente a h3
#### Equivalente a h4
##### Equivalente a h5
###### Equivalente a h6

---
Con un triple "-", "=", "_", "***" se crean reglas horizontales

---
Con "-", "*", "+" al principio de cada renglón se crean listas desordenadas
- item 1
* item 2
+ item 3

Con "1." se crea una lista ordenada
1. item 1
2. item 2
3. item 3

---
Con ">" al princpio de cada renglón, se crea una cita
> mi vida en una frase
>
>> una cita anidada

---
Con triple "~" o "`" seguido del nombre del lenguaje (se pintan de color), arriba y abajo de un párrafo se crea un bloque de código
~~~go
package main
import "fmt"

func main(){
    fmt.print("hola mundo")
}
~~~
---
Con "_", "*" antes y despúes de una frase

Esto es un _lorem ipsum_ y *no más*

Con doble "_", "*" antes y despúes de una frase se ponen negrillas

**axolote.** Animal endémico del valle de México

Usar ambos énfasis, con triple "_", "*" antes y despúes de una frase
***mira no más***

---
Con "[titulo]""[id]""(link)" se crean enlaces

[indetificate][google]

[ve a google][google]

y con "<>" se encierra un link completo

<http://google.com>

[google]:(google.com)

---
con "`" se escribe código

`<html>` es una etiqueta

---
con "pre" encerrado entre "<>", se crea un texto preformateado
<pre> que ondita
    ya me quiero irr
                otro espacio!
</pre>

---
Con "![texto alt]""[id]""(ruta/img)" se incrustan imagenes

![mi logo][logo]

[logo]:(./logo.png)

---
usando \ se escapan los simbolos que se utilizan para escribir markdown

\* Nota \- no hay\! \- \(no sabemos hasta cuando\)\.

---
Con "---|---|---" se crean tablas!

si se ponen "---:" se alinea hacia la izq

con ":---:" se alinea al centro

num | nombre | calif
:---:|---|:---:
1 | Angel | 8
2 | gogo | 7