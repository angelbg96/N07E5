# comandos VIM

## Modos de trabajo
- `esc` para salir del modo de trabajo actual
    * Regresa al modo _Normal_
- __Normal__
    * Navegar por el documento o ejecutar comandos para la edición del documento
- __Inserción__
    * Modificar el archivo
    * `i` para ingresar
- __Visual__
    * Hacer una selección de contenido sin usar el cursor
    * `v` para ingresar
    * Se puede navegar con las teclas `H` , `J` , `K` , `L`
    * Para salir se utiliza algún comando para copiar o cortar o con `esc`

---
## Comandos prácticos
- `vim`
    * Inicia el editor
    * `vim archivo.ext`
        + Abre el archivo indicado con el editor
- `:q`
    * Salir del documento
    * `:q!`
        + Forzar salida del documento
- `:w`
    * Guardar cambios
    * `:wq`
        + Guardar y salir el documento
- `H` , `J` , `K` , `L`
    * Teclas de navegación, moverse por el documento
    * `H` : a la izquierda
    * `J` : abajo
    * `K` : arriba
    * `L` : a la derecha
- `:edit rutaArchivo.ext`
    * Abrir archivo indicado
- `w`
    * Cursor salta al principio de la siguiente palabra
- `e`
    * Cursor salta al final de la siguiente palabra
- `b`
    * Retorna el cursor al principio de la palabra anterior
- `numero + letraNavegacion`
    * Mueve el curor _X_ número de posiciones de acuerdo a la tecla de navegación presionada
    * `8k` : 8 filas arriba
    * `32h` : 32 caracteres a la derecha
- `f + letraBuscar`
    * Busca y mueve el cursor a la palabra más próxima que contenga la letra indicada __sobre la misma línea__
- `0`
    * Ubicarse al principio de la línea
- `$`
    * Ubicarse al final de la línea
- `*`
    * Buscar coincidencias sobre la palabra en la que se esté posicionado y se coloca en la coincidencia más próxima
- `%`
    * Se mueve enter el `(` `)` de apertura y cierre
- `gg`
    * Cursor hasta inicio de documento
- `G`
    * Cursor al final del documento
- `numero + G`
    * Ir a la _X_ línea indicada
    * `2G` , `15G` , `20G`
- `u`
    * Deshace el último cambio realizado
- `o`
    * Inserta una nueva línea despúes del renglón donde se está posicionado y entra al modo _INSERTAR_
- `O`
    * Inserta línea antes de la posición actual y entra al modo _INSERTAR_
- `x`
    * Elimina el caracter donde esté ubicado
- `X`
    * Elimina el caracter de la izquierda de donde esté posicionado
- `r + letra`
    * Sustituye la letra donde está posicionado el cursor por la letra indicada
- `d`
    * Elimina toda una palabra desde la letra donde está ubicado
- `dw`
    * Elimina palabra desde donde está posicionado hasta el inicio de la siguiente palabra
- `dd`
    * Manda a portapapeles la línea donde se haya posicionado
- `p`
    * Pega contenido que se mandó a portapapeles
- `yy`
    * Copia toda una línea
- `numero + yy`
    * Copia _X_ cantidad de líneas a partir de su posición
    * `4yy` , `12yy`
- numero + dd
    * Corta _X_ cantidad de líneas desde su posición
    * `2dd` , `8dd`
- `.`
    * Repite el último comando ejecutado
- `/palabra`
    * Buscar palabra y el cursor se mueve a la coincidencia más próxima
    * Si existe más de una coincidencia
        + `n` : desplazarse a la siguiente coincidencia
        + `N` : desplazarse a la coincidencia anterior
    * __NOTA__ : Se pueden usar _RegEx_ para realizar la búsqueda!
- `:%s/caracteresAsustituir/nuevosCaracteres/g`
    * Sustituye los nuevos caracteres en las coincidencias con los caracteres que se están buscando
    * `%s` : substituir
    * `/g` : global, en todo eldocumento se buscarán las coincidencias, si no está, lo busca solamente en la línea donde se encuentra posicionado