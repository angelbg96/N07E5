# Vagrant

## Antecedents
- Herramienta de software open source que simplifica el trabajo de ejecución y gestión de VM, es un
*gestor de entornos*
- A partir de programación, se pueden tener entornos replicables de forma muy rápida
- No proporciona Interfaz gráfica, todo es por CLI

### Conceptos
- *Boxes*: Imágenes de disco (SO)
- *Vagranfile*: Archivo que interpreta Vagrant y contiene las definición de las VM. Contiene un
Lenguaje Específico de Dominio (DSL) de Ruby
- *Interfaz común*: Dispone de una herramienta de línea de comandos para gestionar las VM fácilmente
y desde un mismo lugar
- *Virtualización*: Soporta virtualización con VirtualBox, Hyper-V, Docker. Se puede extender a
LibVirt, VMWare, AWS con plugins

### Proceso de uso
- En página de [Vagrant](https://app.vagrantup.com/boxes/search?provider=virtualbox), buscar el Box
de la distro a utilizar y con el Hipervisor que se disponga p.ej. VirtualBox
- Tener el hipervisor en ejecución
- Consultar [comandos y configuraciones](https://developer.hashicorp.com/vagrant/docs)

## Comandos
- `vagrant plugin list` : Revisar plugins de vagrant instalados (debería estar VirtualBox)
- `vagrant plugin install vagrant-virtualbox` : Instalar plugin de virtualBox para Vagrant
- `vagrant plugin install vagrant-vbguest` : Instalar herramientas de virtualBox
- `vagrant box add "SO/tag"` : Descarga la imagen ISO del SO especificado
	- `--force` : Forza la descarga de la imagen
	- `--box-version x.y.z` : Especifica la versión a utilizar del Box
- `vagrant init SO/tag` : Crea un *vagrantfile* en el directorio actual para gestionar la VM

**NOTA**: Todos los comandos se deben ejecutar al mismo nivel del *Vagranfile*
- `vagrant up` : Levantar VM
    - Se crea una carpeta *.vagrant* para gestionar la VM
    - Para regresar al estado inicial de la WM se borra la carpeta *.vagrant*
    - `--provision` : Forza a aplicar el provsionamiento configurado
- `vagrant ssh` : Accede a la VM
- `vagrant halt` : Dar de baja la VM
- `vagrant destroy --force` : Destruye la VM
- `vagrant provision` : Resincroniza configuración de aprovisionamiento sin reiniciar VM
- `vagrant reload` : Reinicia VM para cargar nuevas configiguraciones
    - `--provision` : Forza a aplicar el provsionamiento configurado
    - `--provision-with povis1,provis2` : Forza a aplicar las configuraciones de los provisionadores
    indicados

## Configuraciones
~~~ ruby
Vagrant.configure("2") do |config| # Default
    config.vm.box = "ubuntu/focal64"       # SO  a utilizar
    config.vm.box_version = "20230719.0.0" # Version especifica del Box

    # Definir hostname para la VM
    config.vm.hostname = "hostname"

    # Redireccionar puertos Host - VM
    config.vm.network "forwarded_port", guest: 80, host: 8080

    # Utilizar IP del adaptador de red
    config.vm.network "public_network", use_dhcp_assigned_default_route: true

    # Parametrizar recursos
    config.vm.provider "virtualbox" do |vb|
        vb.name = "vm_nombre"
        vb.memory = 1024
        vb.cpus = 2
    end

    # Instalar Puppet
    config.vm.provision "shell", inline <<-SHELL
        apt-get update -y
        # Mas comandos bash para aprovisionar
    SHELL



end
~~~
