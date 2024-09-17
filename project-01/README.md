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