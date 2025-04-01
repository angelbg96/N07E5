# Excel


## Menu de opciones

### Inicio
- *Portapapeles*. copiar, diferentes opciones de pegado y opción para copiar formato (estilos
  visuales de presentación de una celda).
- *Número*. Formato de presentación con el que se visualiza una celda, se puede elegir un formato
  General (default), de texto, de fecha, de moneda, porcentaje, etc.
- *Estilos*. Dar diseño a una celda o grupos de celdas. El más interesante es la opción *estilo*
  *condicional*. en la que se configuran reglas para que una celda se muestre de algún color de
  acuerdo a su contenido.


### Fórmulas
- *Biblioteca de funciones*. Listado de funciones ordenadas por categoría, si se hace hover sobre
  alguna formula se obtiene una breve descripción de su finalidad.
- *Nombres definidos*. Se gestionan los nombres de grupos de celdas a los que se puede hacer
  referencia con un nombre personalizado, cada tabla creada obtiene un nombre por default.
- *Auditoría de fórmulas*. Herramientas para testear celdas que contengan funciones


### Datos
- *Obtener y transformar datos*. Importar datos de diferentes fuentes como un documento CSV, base
  de datos, servicio web, de una tabla en excel o un rango de celdas.
- *Herramientas de datos*. Herramientas para distribuir texto en celdas, quitar duplicados, rellenar
  celdas automaticamente y validar datos.


### Revisar
- *Revisión*. Para verificar ortografía, sinónimos y estadísticas del libro actual.
- *Comentarios* | *Notas*. Agregar un comentario a una celda o grupo de celdas y Notas.
- *Proteger*. Posibilidad de restringir la edición de una hoja, de todo el libro o de rangos.


-------------------------
## Operadores
- Aritmeticos: + , - , * , / , ^ (Potencia) , % (porcentaje)
- De comparación: > , < , <= , >= , <> (Distinto de)
- Concatenación: "texto1" & "texto2"
- Lógicos: si(prueba, valor_verdadero, valor_falso), y(prueba1, prueba2, pruebaN),
  o(prueba1, prueba2, pruebaN), no(valor)
- Comodines para texto: 
    - `*` Cualquier secuencia de caracteres : "\*letras" (termina con letras), "letras\*"
      (empieza con letras), "\*letras\*" (Contiene las letras)
    - `?` Cualquier caracter, pero solo uno
    - `~` Escapar asteriscos y signo de interrogación "letras~?"
    - `""` Sin contenido (Vacio)
    - `"<>"` Cualquier contenido de texto

## Referencias
- Relativa. Al indicar alguna operación con una celda o rangos de celdas y se copia la operación a
  lo largo de las filas y/o columnas, se incrementarán estas también. Por default se utiliza esta
  refencia (`A5`, `B3:C7`, etc)
- Absoluta. Al copiar una operación con una celda a lo largo de filas/columnas, la referencia a
  dicha no cambiará con el incremento entre filas o columnas. Sintaxis: `$columna$numero`, etc
- Mixta. Se puede dejar fija solo una parte de la referencia hacia la celda o rango de celdas, el
  signo `$` se antepone a la izquierda del nombre de la celda o del número de columna si se desea
  fijar alguna de las dos coordenadas
    - Fijar fila: `columna$numero`
    - Fiajr columna: `$columnaNumero`

-------------------------
## Formulas utiles
- Texto
    - `= espacios("texto")` : Quita todos los dobles espacios extra que se encuentren en el texto
    - `= concat("texto1", "texto2")` : Concatena las cadenas de texto especificadas o celdas con texto
    - `= unircadenas("delimitador", ignoraVacios, "texto1", "texto2",)` : Concatena las cadenas de
      texto especificadas, entre cada texto se colocará la secuencia de caracteres como delimitador,
      con *ignoraVacios* que es de tipo booleano, se define si se consideran o no las celdas vacias
    - `= texto("valor", "formato")` : Convierte un número con un formato especiicado, útil para
      representar fechas y horas
    - `= formulatexto(celda)` : Muestra la formula escrita en la celda señalada
    - `= izquierda("texto", num_caracteres)` | `= derecha("texto", num_caracteres)` : Extrae la
      cantidad de caracteres indicada del texto desde el pricipio|final
    - `= extrae("texto", posicion_ini, num_caract)` : Extrae la cantidad de caracteres espeficada a
      partir de la pisición inicial
    - `= largo("texto")` : Obtener la longitud de caracteres del texto
- Fechas
    - Las fechas se expresan en números enteros de días a partir del 01/01/1900
    - Las horas se expresan en decimales a partir de las 00:00:00 hrs
    - `= HOY()` : Retorna la fecha del día actual
    - `= AHORA()` : Retorna la fecha y hora del día actual
    - `= sifecha(fechaInicial, fechaFinal, "Unidad")` : Retorna la diferencia entre la fecha de
      inicio y la final. Si la fecha de inicio es mayor que la de fin, retorna *#NUM*. Unidad puede
      tener los siguientes valores:
        - Y : Diferencia de años completos
        - M : Diferencia de meses completos
        - D : Diferencia en días completos
        - YM : Diferencia en meses de las fechas. Los días y años son omitidos en el cálculo
        - YD : Diferencia en días de las fechas. Los días y años son omitidos en el cálculo


-------------------------
## Ejemplos de Formulas para usos prácticos
- Encontrar texto en una celda
    - `= esnumero(hallar("caracteres", celda))` : Encuentra la secuencia de caracteres en la celda
      indicada. Si existe, retorna la posición del texto donde fue encontrado, si no lo encuentra
      retorna error *#VALOR*. Es *case insensitive_
    - `= esnumero(encontrar("caracteres", celda))` : Encuentra la secuencia de caracteres en la
      celda indicada. Si existe, retorna la posición del texto donde fue encontrado, si no lo
      encuentra retorna error *#VALOR*. Es *case sensitive*
- Busqueda de datos en una tabla
    - `= indice(matriz, coincidir(valor, rangoCeldasCol, 0),  numCol)` : Busca dentro de la tabla
      (matriz) el dato indicado (valor) dentro de una columna de tabla y retorna la celda de interés
    - `= indice(matriz, coincidir(valorX, rangoCeldasCol, 0), coincidir(valorY, rangoCeldasFil, 0))` :
      Busca dentro de la tabla (matriz) el dato indicado (valorX) dentro de una columna de tabla que
      coincida también con el valor de una fila (ValorY) en un rango de filas (rangoCeldasFil)
    - `= buscarx(valor, rangoBusqueda, rangoResultado, , 0, 1)` : Busca dentro de una columna
      (rangoBusqueda) el dato indicado (valor) y retorna el valor de la celda de interés
      (rangoResultado)
- Referencias
    - `= nombreHoja!$celda` | `= nombreHoja!$celdaIni:celdaFin` : Hacer referencia a una celda o
      grupo de celdas de la hoja especificada
    - `= '[libro]nombre Hoja!celda'`: Hacer referencia a una celda de otro libro, se abre un cuadro
      de diálogo para seleccionar un libro. Las comillas se colocan cuando el nombre de la hoja
      lleva espacios
- Referencias a tablas
    - `= nombreTabla` : Hace referencia a todos los datos de la tabla (matriz)
    - `= nombreTabla[nombreCol]` : Hace referencia al grupo de celdas de la columna indicada
    - `= nombreTabla[@]` : Hace referencia al rango de celdas de la fila actual cuando la operación
      es en alguna fila dentro del rango que ocupa el tamaño de tabla
    - `= nombreTabla[@nombreCol]` : Hace referencia a una columna de l fila actual
    - `= nombreTabla[#datos]` : Hace referencia al contenido de la tabla (matriz)
- Referencias personalizadas
    - En menú Fórmulas, administrador de nombres se puede crear una nueva etiqueta que haga
      referencia a una celda o a un rango de celdas, incluso al nombre de una columna de una tabla
    - Es util cuando se quiere realizar alguna validación utilizando una formula para personalizar
      el criterio. Otra forma de hacerlo sería con la formula `indirecto("tabla[columna]")`, no es
      muy recomendado si existen muchos valores, ya que *indirecto* recalcula cada que Excel lo hace


-------------------------
## Dar presentación a la hoja de calculo
- Estilo condicional
    - Sirve para colorear celdas que cumplan con algún criterio, este puede ser que sea mayor a
      cierta cantidad, que contenga determinado texto, sean mayores al promedio, mayor a una fecha,
      datos duplicados, los datos más grandes o menores, o seguir un criterio de acuerdo a una
      formula que se introduzca
    - Para colorear filas, se debe seleccionar toda la matriz de datos a aplicar los estilos y
      utilizar una formula para establecer la condición a cumplir. p.ej.
      `= ESNUMERO(HALLAR("texto",rangoBusqueda))`
- Validación de datos
    - De acuerdo con algún criterio de validación, donde se puede utilizar algunos criterios
      preestablecidos como permitir datos mayores/menores a un número entero o decimal, una fecha,
      una hora, cierta longitud de texto, elegir datos de una lista desplegable o personalizarlos
      con funciones
    - Da la posibilidad de mostrar un mensaje de ayuda y un mensaje de error en caso de no cumplir
      con el criterio preestablecido
    - Si se decide utilizar una lista, se deben seleccionar el rango de celdas donde se encuentran
      los datos o personalizar una referencia a los datos p.ej. `= Etiq_miLista`
    - Si se elige la opción personalizada, se deben colocar las funciones en las que se vuelve
      partícipe la celda a evaluar. Debe retornar un valor lógico (Verdadero, Falso)


-------------------------
## Casos de uso
- Validar registros duplicados
    - Formato condicional con fórmula: `CONTAR.SI(L_numeros, $celda2) > 1`
        - Se debe utilizar una lista de nombres de la columna de interés
        - La primer celda hace referencia a la columna de interés
    - Validación de datos con fórmula: `+ CONTAR.SI(L_numeros, $celda2) = 1`
        - Se debe utilizar una lista de nombres de la columna de interés
        - Opcional: colcoar un mensaje personalizado de error
- Colocar iconos en celdas con formato condicional
    - Crear una tabla con valores 1 y 0, seleccionar las celdas y establecer un formato de celdas
      personalizada: `"si";;"no"`
    - Crear tabla donde se van a utilizar los iconos y a los campos donde van a estar, establecer el
      mismo formato de celda personalizado. Opcionalmente utilizar validación de datos a partir de
      lista con los datos de la tabla anterior
    - Con el formato condicional y al ser números los verdaderos valores, establecer un icono para
      algo afirmativo y otro para algo negativo. Seleccionar la casilla para que solo se muestre
      el icono
- Al trabajar con columnas desbordadas
    - `Fun(celda#)` : La funcion va a operar con todas las celdas secundarias


