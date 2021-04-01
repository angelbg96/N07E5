# Bases de datos

## NoSQL
- Clave - Valor
    * Almacena datos en forma de colección en pares (tipo diccionario)
    * Acceso rápido a la información
    * Son altamente particionales. Permiten segmentar la info. cuando una instancia supera su capacidad máxima
    * Permite escalamiento horizontal
    * Útiles para el manejo de Sesiones, carrito de compras
    * Como ejemplo: Redis
- Documentales
    * Consulta de datos parecidos al formato JSON
    * Cada documento puede tener diferentes propiedaes
    * Útil para administrar contenido como blogs, plataformas de video
    * Como ejemplo: MongoDB
- Grafos
    * Almacena y navega a través de relaciones
    * Sus relaciones no son como SQL, son las conexiones entre nodos
    * Buscar el número de relaciones con un nodo. Seguir el rastro de un nodo cuando se llevó a cabo una acción
    * Útiles para redes sociales, motores de recomendación, prevención de fraudes
    * Como ejemplo: Gremlin
- Familia de columnas
    * Consta de tablas como en SQL, con la diferencia de que se tiene un subnivel en cada columna para almacenar información específica
    * Una columna puede tener diferentes subcolumnas por cada registro
    * Como ejemplo: Cassandra

## SQL

