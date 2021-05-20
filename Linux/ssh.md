# Conexión SSH

## Comandos útiles
- `ssh keygen`
    * Crea un certificado local (público y privado)
    * Para ver la llave pública se accede a _.ssh/id\_rsa.pub_
    * En el servidor colocar la llave en el archivo _.ssh/authorized\_keys_
- `ssh –p 22 usuario@ip`
    * Conectarse a servidor
- `ssh-copy-id user@ip:`
    * Copia la key pública de la computadora al archivo _.ssh/autorizhed\_keys_
- `ssh -t user@ip comando`
    * Emula una terminal en el servidor. _Irsi_ es un proceso que ejecuta el protocolo IRS (chat)
- `ssh -D puerto user@ip`
    * Crea un Proxy socks en el puerto definido para usarlo como servidor Proxy
- `ssh -X user@ip`
    * Ejecuta apps con UI en el servidor pero la UI corre desde la computadora local. Se necesita un servidor X (Xqwarts). La app debe estar instalada en el servidor e iniciarla
- `ssh -L ptoLocal:ip2:ptoSvr user@ip1`
    * Llegar al servidor 2 desde el servidor 1 con redirección de puertos
    * Si existe un firewall hacia el servidor 2 con todos los puertos bloqueados, y existe una regla en la que el servidor 1 tiene acceso.
    * El primer puerto es desde la máquina local, el segundo puerto entre la conexión de server 1 y 2
- `ssh -R ptoDest:localhost:ptoSvr usrExt@ipExt`
    * Con el puerto destino crea una conexión entre el servidor externo y el nuestro, a través del puerto de nuestro servidor.
    * Se ejecuta el comando y se hace login desde servidor externo, una vez ahí, se conecta a nuestro servidor con: `ssh usr@localhost -pPtoDest`
