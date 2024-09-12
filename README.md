# Calilegua_DevOps

## Repositorio para alojar las prácticas DevOps del curso de HedySoftware

### Herramientas:
- VirtualBox.
- debian.
- vagrant boxes (para descargar la distro correspondiente).
- CI / CD ( github actions, gitlab).
- ansible.
  

# Descargar e instalar vagrant en windows

- Descargar el instalador: https://developer.hashicorp.com/vagrant/install
  
### Configurar un proyecto Vagrant con Debian:

- Crear una carpeta para el proyecto Vagrant:
- Abrir el terminal (CMD o PowerShell)
- Crear una carpeta para tu proyecto:
  
```
mkdir debian11-vagrant
cd debian11-vagrant
```
- Inicializar Vagrant con Debian 11

```
vagrant init debian/bullseye64
```
- Esto creará un archivo Vagrantfile que configura una máquina virtual Debian  (nombre clave Bullseye)

## Modificar el archivo Vagrantfile (opcional):

__Abrir el archivo Vagrantfile en un editor de texto si deseas hacer cambios, como ajustar la cantidad de RAM o procesadores:__
```
Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus = 2
  end
end
```
__Iniciar la máquina virtual:__

__Para descargar la caja de Debian 11 y crear la máquina virtual, ejecutar:__

```
vagrant up
```
__Vagrant descargará la imagen de Debian 11 y la lanzará en VirtualBox.__

- Acceder a la máquina virtual:

  __Una vez que la máquina esté en ejecución, puedes acceder a ella con:__
  
```
vagrant ssh

```
- Finalizar la sesión:
  __Para detener la máquina virtual, usa el siguiente comando:__

```
vagrant halt
```
__Para destruir la máquina virtual si ya no la necesitas:__

```
vagrant destroy
```
## Iniciar conexión ssh dentro de virtualbox
- Si la maquina virtual no te toma el usuario y contraseña vagrant a través de cmd por ssh podés cambiar la contraseña del usuario para solucionar este problema

__Cambiar la contraseña del usuario vagrant:__
- Conectate a la VM usando vagrant ssh.
- Cambia la contraseña con:
  
```
sudo passwd vagrant
```
- Ingresa la nueva contraseña y luego usa esa nueva contraseña para iniciar sesión desde la interfaz gráfica de VirtualBox.
- Con estos pasos ya vas a tener acceso por ssh tambíen dentro de tu maquina virtual en virtualbox

## Configurar interfaz gráfica para la maquina virtual en virtual box:

- Revisa si en tu archivo Vagrant tienes habilitada la interfaz gráfica de VirtualBox. Si no, podés habilitarla en tu archivo de configuración Vagrantfile:
  
```
config.vm.provider "virtualbox" do |vb|
  vb.gui = true
end

```
__Captura del Vagranfile__
![vagrantfilecptura](https://github.com/user-attachments/assets/4ca857e4-b023-4436-be0b-09b15d8f7467)


__Instalar el entorno de escritorio en Debian__
 - Instalar GNOME ( es uno de los entornos más completos y es la opción predeterminada para muchas distribuciones de Linux, incluida Debian).


__Desde tu sesión SSH o la consola de VirtualBox, ejecuta:__

```
sudo apt update
sudo apt install -y task-gnome-desktop

```
__Reinicia la máquina virtual__

```
vagrant halt
vagrant up

```
__Iniciar la interfaz gráfica__
Después de instalar el entorno de escritorio y configurarlo, reinicia la máquina para cargar la GUI:

```
sudo reboot

```
__Captura de la conexión SSH, vagrantfile y VM corriendo en windows:__


![vagrant completo](https://github.com/user-attachments/assets/f9f163ea-9c8c-41d8-a617-58830d480087)

# Descargar e instalar vagrant en Ubuntu

__Instalación de Vagrant__

```
sudo apt install vagrant

```
__Configuración para Debian__
- Crear una carpeta para el proyecto Vagrant:
- Abrir el terminal.
- Crear una carpeta para tu proyecto:
  
```
mkdir debian12-vagrant
cd debian12-vagrant

```

__inicializar el proyecto Vagrant:__


```
vagrant init bento/debian-12   //Bento es una forma sencilla de obtener la imagen de máquina virtual preconfigurada y lista para usar con Vagrant 

```

__Ejecutar la máquina virtual:__

```
vagrant up

```
__Conectar a la máquina virtual:__

```
vagrant ssh

```

