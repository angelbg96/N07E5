# Bases de datos

## NoSQL
### Características
- NoSQL significa: Not Only SQL
- No están basado en tablas y en relaciones como en SQL
- No ser ACID (Atomicidad, Consistencia, Aislamiento, Durabilidad) de transacciones
- Siguen el teorame de CAP (Consitencia, Disponibilidad, tolarancia a la Partición)
- No tener un esquema (schema) formal, es flexible
- Orientadas al desarrollo web
- Orientadas a desarrollos de grandes cantidades de datos (miles de millones de registros)
- Mayor rapidez en lectura de datos
- Se escalan horizantalmente (más nodos/servidores para soportar la carga)
- Para modelar una colección se debe pensar en la vista donde se van a colocar los datos

### Tipos
- Clave - Valor
    - Almacena datos en forma de colección en pares (tipo diccionario)
    - Acceso rápido a la información
    - Son altamente particionales. Permiten segmentar la info. cuando una instancia supera su capacidad máxima
    - Permite escalamiento horizontal
    - Útiles para el manejo de Sesiones, carrito de compras
    - Como ejemplo: Redis, dynamodb, Riak, MemcacheDB
- Documentales
    - Consulta de datos parecidos al formato JSON
    - Cada documento puede tener diferentes propiedaes
    - Útil para administrar contenido como blogs, plataformas de video
    - Como ejemplo: MongoDB, CouchBD
- Grafos
    - Almacena y navega a través de relaciones
    - Sus relaciones no son como SQL, son las conexiones entre nodos
    - Buscar el número de relaciones con un nodo. Seguir el rastro de un nodo cuando se llevó a cabo una acción
    - Útiles para redes sociales, motores de recomendación, prevención de fraudes
    - Como ejemplo: Gremlin, Neo4J, AllegroGraph, 
- Familia de columnas
    - Consta de tablas como en SQL, con la diferencia de que se tiene un subnivel en cada columna para almacenar información específica
    - Una columna puede tener diferentes subcolumnas por cada registro
    - Como ejemplo: Cassandra

## SQL
### Características
- Significa Lenguaje de Consulta Estructurada (Structured Query Language)
- Se debe modelar el esquema/estructura de las tablas y sus relaciones antes de implementarla
- Se escalan verticalmente principalmente (CPU, RAM, SSD)
- Son de rápida escritura
- Útiles para ejecutar consultas de datos complejas (de diferentes tablas y filtros), pero con el costo de tiempo cuando la cantidad de datos es alta
- Utilizan las formas Noramles para mantener la consistencia de los datos

