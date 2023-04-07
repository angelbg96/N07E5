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

### Indices
- *CBO* (Cost Based Optimizer - Optimizador basado en costes) : Elemento importante en un gestor de BD y la causa del porque en ocasiones no se utiliza el indice
- Un índice es una estructura diferente dentro de la base de datos. Requiere su propio espacio en disco y contiene una copia de los datos de la tabla. Eso significa que un *índice es una redundancia*. Crear un índice no cambia los datos de la tabla; solamente establece una nueva estructura de datos que hace referencia a la tabla. De hecho, un índice de base de datos se parece mucho a un índice de un libro: ocupa su propio espacio, es redundante y hace referencia a la información actual almacenada en otro lugar.
- Para asegurarnos que las consultas que hagamos utilicen realmente los índices existe un parámetro de base de datos que se llama `optimizer_index_cost_adj`. Con ayuda de este parámetro podemos hacer que las decisiones de acceso del optimizador hacia los datos favorezcan el uso de índices antes que del uso de FTS. Oracle recomienda una formula para asignarle un valor a este parámetro (por defecto está en 100):
~~~ SQL
-- Habilitar estadísticas de consultas:
set autotrace traceonly;

-- optimizer_index_cost_adj = Costo FTS de la consulta/Costo con hint usando el índice*100
alter session set optimizer_index_cost_adj = 34;
~~~
- Como Observación es bastante común observar el valor de `optimizer_index_cost_adj` entre 20 y 30 en las bases de datos. Es importante recalcar que el DBA siempre debe *optimizar sus resultados en base a las lecturas más que por el costo*. Recordemos que el Costo es un valor que Oracle representa para un plan de ejecución, es algo así como un puntaje. El verdadero afinamiento debe estar orientado a las estadisticas que te entrega el plan como por ejemplo los *consistent gets*.

