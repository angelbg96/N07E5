# Tipos de Archivos de Configuración

- `xml`
- `json`
- `properties`
    - Archivo con propiedades clave - valor, utilizado principalmente en aplicaicones Java
    ~~~ bash
    nombre=valor
    # esto es un comentario
    ~~~ 
- `env`
    - Archivo para establecer variables de entorno que utilizará alguna aplicación
    - Suelen ser archivos ocultos, es decir se nombran `.env`
    - Sintaxis:
    ~~~ bash
    nombre=valor
    # esto es un comentario
    ~~~ 
- `ini`
    - Archivos recurrentemente utilizados en sistema Windows y algunas aplicaciones Linux
    - Compuestos por:
        - Secciones: permiten agrupar parámetros relacionados, sintaxis: `[nombreGrupo]`
        - Parametros: primero se define el nombre del parámetro y después su valor: `parametro=valor`
    ~~~
    [grupo]
    parametro=valor
    parametro2=0
    ; esto es un comentario
    ~~~
- `yaml`
    - Se pronuncia *yamel*
    - Suelen nombrarse con extensión `.yml` o `.yaml`
    - Utilizan sintaxis `llave: valor`. Si una llave u objeto tuviera propiedades, estas se deben representar con una identación, y a su vez si estas tuvieran más propiades, deben tener su respectiva identación por cada subnivel de propiedades.
    - Listas. Grupo de propiedades de una llave
    - Sintaxis:
    ~~~ yaml
    objeto:
        numero: 0
        texto: 'lorem ipsum'
        texto2: lorem ipsum
        lista1: ['texto1', "texto2"]
        lista2:
            - texto1
            - texto2
        subojeto: {prop1:2, prop2:"texto"}
        texto_largo: |
            todo lo siguiente se representa

            como valor de la propiedad indicada
    # esto es un comentario
    ~~~
