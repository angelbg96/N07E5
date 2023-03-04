# Servidores de aplicaciones Web


## NGINX
- Es open source pero tiene una versión enterprise
- A diferencia de otros servidores que crean un hilo de ejecución cuando llega una petición, NGINX es asíncrono y orientado a eventos
- Directiva: Función que realiza una acción. Están compuestas por un nombre y sus parámetros. Se encuentran dentro de un contexto y ese es su alcance (Scope): `nombreDir "param1" "param2"`
- Contexto: Parte de una estructura de arbol, contiene una o varias directivas
    ~~~ json
    contexto {
        directiva1;
        directiva2;
    }
    ~~~
- Contextos CORE, o globales, afectan todo elcorportamiento del servidor: 
    - `main` : no contiene un cuerpo, todo lo que se configura es main
    - `events` : configurar todo lo referente a las conexiones de usuarios
    - `http` : administrar las peticiones HTTP
    - `server` : configurar virtualhost, puerto a escuchar, archivos de retorno
    - `location` : manipular la petición de los usuarios, redirecciones. Normalmente se encuentra dentro de `server`
    - `upstream` : servidores para realizar balanceo de cargas, proxy reversivo. Se encuentra dentro de `http` y fuera de `server`
    - `mail`
    - `if` : funciona como cualquier condicional, útil para realizar redirecciones
    - entre otros...
- el archivo *nginx.conf* contiene las configuraciones realizadas y por defecto ya existen algunas. Se encuentra dentro del directorio de NGINX
    - `include ruta/nginx/conf.d/*.conf` : Directiva dentro de `http` en la configuración por default, que indica que sean importados todos los archivos de configuracion del directorio *conf.d*, son configuraciones para cada virtualhost
    - Las configuraciones se mantienen en memoria durante la ejecución del servidor
    - El archivo *default.conf*, tiene configuraciones del contexto `server` y `location`. Establece la ruta donde se encuentran los recursos y cual es el archivo index
- `nginx -s reload` : reiniciar el servidor
- `nginx -t` : verificar que todos los archivos de confuración no tienen errores de sintaxis
- Configuración sencilla:
    ~~~ json
    server {
        listen pto; // 80 por default, el 2do parametro indica que es el servidor por default que atiende una petición que no se pueda resolver
        server_name nombre; // localhost por default, se establece el hostname, dominio
        root ruta/directorioWeb; // ruta a la carpeta de recursos
        index index.html index.php index.ext; // Indica los posibles index a tomar
        error_page 400 cod2 codN /ruta/pagina404.html; // indica la pagina de error a un determinado código de error HTTP
    }
    ~~~
    - `error_page 400 = /ruta/pagina404.html;` : sobreescribir la página de error en un determinado virtualhost
- Crear un dominio local
    - linux: Agregar IP y servername al archivo */etc/host*
    - windows: Agrepar IP, TAB, servername al archivo *C:\windows\system32\drivers\etc\host*
    - En el servidor donde está instalado NGINX, agregar cuantos virtualhost se requieran (subdominios, archivos de configuración en directorio *conf.d*), pero solo uno debe tener la directiva `listen pto default_server`, que sirve para indicar que ese host atenderá una solicitud a un subdominio que no se puede resolver o no existe
- Autentificación básica
    - En la configuración del virtualhost default o el de preferencia, dentro del contexto `server` agregar:
    ~~~ json
    location ruta { // ruta del servidor donde se solicitará autentificación
        auth_basic "nombre"; // Nombre representativo del manejo de rutas
        auth_basic_user_file "ruta/.archivoUsers"; // archivo de usuarios y passwords
        root ruta/directorioWeb; // Directorio de respuesta si auth es correcta
    }
    ~~~
- Proxy reversivo
    - Proxy: Intermediario entre usuario y el destino web. El servidor es quién termina de realizar la petición, por lo que es la IP del servidor la que va por HTTP.
    - Proxy reversivo: El proxy recibe una petición de un usuario y la redirecciona a alguno de los servidores web establecidos, posteriormente este envía la respuesta al usuario. Sirve para redirigir cierto trafico a una IP o socket en particular.
    - En la configuraación del virtualhost default o el de preferencia, dentro del contexto `server` agregar:
    ~~~ json
    location ruta { // ruta del servidor que será atendida por otro host
        proxy_pass http:\/\/dominio_puerto/path; // ruta al host que atenderá la petición
    }
    ~~~
- Servir contenido dinámico
    - FastCGI (Interfaz de entrada común): Protocolo que permite interconectar programas e interactuar con un servidor web. El servidor Web ejecuta el script de cierto lenguaje y este retorna el contenido en HTML o cualquier otro recurso mime-type.
    - En la configuración del virtualhost default o el de preferencia, dentro del contexto `server` agregar:
    ~~~ json
    location ~\.php$ { // RegEx que indica que todos las peticiones que terminen con PHP serán atendidas por el FCGI de PHP
        fastcgi_pass unix:rutaCGI_lenguaje/exec; // indica el binario que interpretará la solicitud
        fastcgi_index index.ext; // indica el archivo index del lenguaje en cuestion
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name; // Proporciona como parametros el path de la solicitud y los parámetros de la URL
        include fastcgi_params; // Archivo de constantes con la que se puede obtener información de la solicitud
    }
    ~~~
- Balanceo de cargas
    - Distribuye el tráfico entre los diferentes servidores web configurados en la infraestructura
    - El servidor main actuará como balanceador, la carga la distribuirá hacia alguno de los otros servidores confugurados
    - Tiene [diferentes algoritmos](https://www.nginx.com/blog/choosing-nginx-plus-load-balancing-techniques/) para determinar qué servidor debe ser el que lo debe atender
    - *round_robin*: algoritmo default, por cada petición, el balanceador le entregará la carga al siguiente servidor
    - En la configuración del virtualhost default o el de preferencia, agregar:
    ~~~ json
    upstream nombreBalanceo { // Se le establece un nombre para identificar a este balanceo
        ip_hash; // algoritmo que determina que cuando se inicia una sesión, el servidor que lo atendió seguirá haciéndolo hasta que el usuario cierre la sesión
        server ip weight=valor; // servidor 1, se le ha dado un valor de 3, atiende 3 veces más peticiones que los otros servidores
        server ip; // servidor 2
        server ip; // servidor 3
    }

    server {
        listen 80;
        location / { // cinfigurar todas las peticiones desde raiz
            proxy_pass http:\/\/nombreBalanceo; // Realizar una redirección hacia los servidores
        }
    }
    ~~~ 
- Certificados
    - Uso de certificados SSL o TLS para cifrar la comunicación cliente - servidor
    - En la configuración del virtualhost default o el de preferencia, agregar:
    ~~~ json
    server {
        listen 443 ssl; // indicar el puerto y el tipo de certificado a utilizar
        ssl_certificate ruta/fullchain.pem; // Indica donde se encuentra el certificado
        ssl_certificate_key ruta/privatekey.pem; // llave privada del certificado
        include ruta/options-ssl-nginx.conf; // archivo de configuración con los parámetros para el manejo de SSL

        if($scheme != "https") { // Directiva if, valida que el esquema de la solicitud sea HTTPS
            return 301 https:\/\/$host$request_uri; // Realiza redirección con directiva return, envía el código de repuesta 301 y la URL HTTPS
        }
    }
    ~~~ 

