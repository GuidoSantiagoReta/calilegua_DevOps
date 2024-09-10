# calilegua_DevOps

## Repositorio para alojar las prácticas DevOps del curso de HedySoftware

### Herramientas:
- VirtualBox.
- debian12.
- vagrant boxes (para descargar la distro correspondiente).
- CI / CD ( github actions, gitlab).
- ansible.
  

### Descargar e instalar vagrant en windows

- Descargar el instalador: https://developer.hashicorp.com/vagrant/install
### Configurar un proyecto Vagrant con Debian 12:

- Crear una carpeta para el proyecto Vagrant:
- Abrir el terminal (CMD o PowerShell)
- Crear una carpeta para tu proyecto:
  
```
mkdir debian12-vagrant
cd debian12-vagrant
```
- Inicializar Vagrant con Debian 12

```
vagrant init debian/bullseye64
```
- Esto creará un archivo Vagrantfile que configura una máquina virtual Debian 12 (nombre clave Bullseye)

## Modificar el archivo Vagrantfile (opcional):

- Abrir el archivo Vagrantfile en un editor de texto si deseas hacer cambios, como ajustar la cantidad de RAM o procesadores:
```
Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus = 2
  end
end
```
- Iniciar la máquina virtual:

Para descargar la caja de Debian 12 y crear la máquina virtual, ejecutar:

```
vagrant up
```
__Vagrant descargará la imagen de Debian 12 y la lanzará en VirtualBox.__

- Acceder a la máquina virtual:

- Una vez que la máquina esté en ejecución, puedes acceder a ella con:
  
```
vagrant ssh

```
- Finalizar la sesión:
- Para detener la máquina virtual, usa el siguiente comando:

```
vagrant halt
```
Para destruir la máquina virtual si ya no la necesitas:

```
vagrant destroy
```
