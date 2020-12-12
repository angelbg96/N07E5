# Excel


## Menu de opciones

### Inicio
- _Portapapeles_. copiar, diferentes opciones de pegado y opción para copiar formato (estilos visuales de presentación de una celda).
- _Número_. Formato de presentación con el que se visualiza una celda, se puede elegir un formato General (default), de texto, de fecha, de moneda, porcentaje, etc.
- _Estilos_. Dar diseño a una celda o grupos de celdas. El más interesante es la opción _estilo condicional_, en la que se configuran reglas para que una celda se muestre de algún color de acuerdo a su contenido.


### Fórmulas
- _Biblioteca de funciones_. Listado de funciones ordenadas por categoría, si se hace hover sobre alguna formula se obtiene una breve descripción de su finalidad.
- _Nombres definidos_. Se gestionan los nombres de grupos de celdas a los que se puede hacer referencia con un nombre personalizado, cada tabla creada obtiene un nombre por default.
- _Auditoría de fórmulas_. Herramientas para testear celdas que contengan funciones


### Datos
- _Obtener y transformar datos_. Importar datos de diferentes fuentes como un documento CSV, base de datos, servicio web, de una tabla en excel o un rango de celdas.
- _Herramientas de datos_. Herramientas para distribuir texto en celdas, quitar duplicados, rellenar celdas automaticamente y validar datos. Esta última, es de acuerdo con algún criterio de valdiación, donde se puede utilizar algunos criterios preestablecidos, elegir datos de una lista desplegable o personalizarlos con funciones (da la posibilidad de mostrar un mensaje de ayuda y un mensaje de error).


### Revisar
- _Revisión_. Para verificar ortografía, sinónimos y estadísticas del libro actual.
- _Comentarios_ | _Notas_. Agregar un comentario a una celda o grupo de celdas y Notas en la hoja actual.
- _Proteger_. Posibilidad de restringir la edición de una hoja, de todo el libro o de rangos.




-------------------------
## Ejemplos de usos prácticos
- `= indice(matriz, coincidir(valor, rangoCeldasCol, 0),  numCol)` : Busca dentro de la tabla (matriz) el dato indicado (valor) dentro de una columna de tabla y retorna la celda de interés
- `= indice(matriz, coincidir(valorX, rangoCeldasCol, 0), coincidir(valorY, rangoCeldasFil, 0))` : Busca dentro de la tabla (matriz) el dato indicado (valorX) dentro de una columna de tabla que coincida también con el valor de una fila (ValorY) en un rango de filas (rangoCeldasFil)
- `= buscarx(valor, rangoBusqueda, rangoResultado, , 0, 1)` : Busca dentro de una columna (rangoBusqueda) el dato indicado (valor) y retorna el valor de la celda de interés (rangoResultado)
- `= nombreHoja!$celda` | `= nombreHoja!$celdaIni:celdaFin` : Hacer referencia a una celda o grupo de celdas de la hoja especificada
- `= '[libro]nombre Hoja!celda'`: Hacer referencia a una celda de otro libro, se abre un cuadro de diálogo para seleccionar un libro. Las comillas se colocan cuando el nombre de la hoja lleva espacios
- Referencias a tablas
    * `= nombreTabla` : Hace referencia a todos los datos de la tabla (matriz)
    * `= nombreTabla[nombreCol]` : Hace referencia al grupo de celdas de la columna indicada
    * `= nombreTabla[@]` : Hace referencia al rango de celdas de la fila actual cuando la operación es en alguna fila dentro del rango que ocupa el tamaño de tabla
    * `= nombreTabla[@nombreCol]` : Hace referencia a una columna de l fila actual
    * `= nombreTabla[#datos]` : Hace referencia al contenido de la tabla (matriz)




