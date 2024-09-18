# Crear VM Vagrant con debian 12 y Vagrantfile personalizado:

- Usar Debian 12 de base.
- Configurar la red como publica.
- Ponerle nombre a la VM
- Usar 2 GBs de RAM, pero si tu PC tiene menos de 4 GBs de RAM, solo usar el 50% de la RAM.
- Crear un disco virtual llamado hd2, y montarlo en /opt/calilegua.
- Actualizar los packages del SO.
- Instalar Docker desde packages deb.
- Probar que Docker esta instalado.
- Ejecutar un container docker con Portainer.


## Resolución en windows:

### 1. Tener instalado vagrant y virtualbox
### 2. Inicializar vagrant en un directorio ya creado

```
vagrant init debian/bookworm64

```
__Esto creará un archivo Vagrantfile que configura una máquina virtual Debian 12.__

### 3. Agregar al Vagrantfile la configuración de red pública (red puenteada)


```
  config.vm.network "public_network"

```
 __Ejecutar vagrant reload y seleccionar la interfaz de red a la cual conectar la máquina virtual por ejemplo si hay más de una opción__

```
 default: Available bridged network interfaces:

1) Realtek PCIe GbE Family Controller
2) Hyper-V Virtual Ethernet Adapter

```
- En este caso seleccionaríamos la opción 1.

__Mostrar la configuración de red e interfaz a la que está configurada como parte de la red pública__

```
ip a

```

### 4. Cambiar nombre a la VM en el Vagrantfile

```
# Asignar nombre a la máquina virtual
  config.vm.hostname = "vagrant-debian12"

```
### 5. Asignar 2GB de ram a la VM

```
   # Asignar 2 GB de RAM (2048 MB) a la máquina virtual

   config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"  
```

### 6. Crear y adjuntar disco en el Vagrantfile después de crear el directorio correspondiente en la VM

```
 # Crear y adjuntar disco virtual
    vb.customize ["createhd", "--filename", "/opt/calilegua/hd2.vdi", "--size", "2048"]
    vb.customize ["storageattach", :id, "--storagectl", "SATA", "--port", "1", "--device", "0", "--type", "hdd", "--medium", "/opt/calilegua/hd2.vdi"]

```

###  7. Actualizar los paquetes

__Actualizar la lista de paquetes__

```
sudo apt update

```

__Actualizar los paquetes instalados__

```
sudo apt upgrade

```
### 8. Instalar Docker desde packages deb ( desde el Vagrantfile)

```
 # automatizar la instalación de Docker 
  
  config.vm.provision "shell", inline: <<-SHELL
   # Verificar si Docker está instalado
  if ! command -v docker &> /dev/null
  then
    echo "Docker no encontrado. Instalando Docker..."
   # Actualizar la lista de paquetes
    apt update
   # Instalar paquetes necesarios para añadir repositorios y claves
    apt install -y apt-transport-https ca-certificates curl gnupg lsb-release
   # Añadir la clave GPG del repositorio de Docker
    curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
   # Añadir el repositorio de Docker a la lista de fuentes de APT
    echo "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
   # Volver a actualizar la lista de paquetes con el nuevo repositorio
    apt update
   # Instalar Docker
    apt install -y docker-ce docker-ce-cli containerd.io
  else
    echo "Docker ya está instalado."
  fi
SHELL
end

```
### 9. Automatizar la ejecución de un contenedor Docker con Portainer

__Modificar el Vagrantfile para incluir el contenedor de Portainer__

```
# Ejecutar contenedor de Portainer
    docker run -d -p 9000:9000 --name portainer \
      -v /var/run/docker.sock:/var/run/docker.sock \
      -v portainer_data:/data \
      portainer/portainer-ce# Ejecutar contenedor de Portainer
    docker run -d -p 9000:9000 --name portainer \
      -v /var/run/docker.sock:/var/run/docker.sock \
      -v portainer_data:/data \
      portainer/portainer-ce
```

__Agregar el usuario vagrant al grupo docker:__

```
sudo usermod -aG docker vagrant

```

Reiniciar la sesión para que los cambios surtan efecto
```
exit
```
volver a conectar y verifica si el usuario vagrant está en el grupo docker:

```
groups

```

__Verificar Permisos del Socket de Docker__

Asegurarse de que el socket de Docker (/var/run/docker.sock) tiene los permisos correctos:

```
ls -l /var/run/docker.sock
```
__Deberías ver algo similar a:__

```
srw-rw---- 1 root docker 0 Sep 17 12:34 /var/run/docker.sock

```
- De esa manera, el socket debe estar accesible por el grupo docker.

__Verificar IP__

```
ip addr show

```

__Ejecutar el Comando de Docker__

- Una vez agregado el usuario al grupo docker y reiniciado la sesión, ejecutar  el comando para iniciar el contenedor de Portainer:

```
docker run -d -p 9000:9000 --name portainer \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data \
  portainer/portainer-ce

```
- Luego de  que se encuentre el contenedor de portainer en ejecución podemos ingresar la ip mas el puerto para ingresar a portainer

__Ejemplo:__

```
192.168.2.50:9000

```

__Si se agota el el tiempo de espera de tu instancia en Portainer. Volver a habilitarlo reiniciando Portainer__

```
docker restart portainer

```

__verificar que esté funcionando correctamente con el siguiente comando:__

```
docker ps

```
