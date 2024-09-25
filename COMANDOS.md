# Comandos
sudo su - (superusuario)
free -m ( ver memoria)
free --help (ver opciones)
man  (estructura y descripcion con ejemplos, manpage, manual)
grep (buscar ocurrencias o no de algo)
cat (visualización, unión)
ls (lista archivos y subdirectorios)
  - l: Lista en formato detallado (longitud)
  - h: Formato de human-readable (por ejemplo, muestra tamaños en KB, MB, GB)
  - a: Muestra archivos ocultos (con punto inicial)
  - R: Recursivo, muestra contenido de subdirectorio
  - t: Ordena por fecha/modificación
  - S: Ordena por tamaño
pwd (Muestra el directorio actual)
cd (Cambia al directorio especificado)
tree (Muestra el contenido de directorios en forma de árbol)

# Herramientas 

netstat   (muestra información sobre las conexiones activas de red en un sistema)

Nmap    (herramienta de escaneo de red)

__Características__ 
- Escaneo de puertos: Identifica puertos abiertos en servidores remotos.
- Cartografía de red: Mapea redes locales e internacionales.
- Análisis de servicios: Determina qué servicios están ejecutando en puertos abiertos.
- Enumeración: Extrae información sobre sistemas remotos.

__opciones útiles__

-p: Especificar puertos a escanear
-sV: Intentar determinar el servicio en cada puerto
-O: Intentar determinar la dirección MAC del host
-Pn: Ignorar el ping inicial y escanear todos los hosts

tshark (herramienta de análisis de protocolos de red para captura y análisis de tráfico de red)

__Características principales__

- Captura y análisis de paquetes de red en tiempo real.
- Decodificación de múltiples protocolos de red.
- Filtros avanzados para seleccionar datos específicos.
- Exportación de capturas a diversos formatos.

Curl ( herramienta para transferencia de datos)

__Características principales__ 

Transferencia de archivos HTTP, HTTPS, FTP, SFTP, SCP, TELNET, DICT, LDAP, POP3, IMAP, SMTP, RTSP, NNTP, FILE, etc.
Soporte para múltiples protocolos de transferencia simultáneos
Capacidad para enviar y recibir datos en formato JSON, XML, SOAP, etc.
Opciones avanzadas para autenticación, cabeceras personalizadas, seguimiento de cookies, etc.

Algunas opciones incluyen:

-X: Especificar el método HTTP (GET, POST, PUT, DELETE, etc.)
-H: Agregar cabeceras personalizadas
-d: Enviar datos en el cuerpo de la solicitud
-o: Especificar un archivo de salida
-k: Ignorar errores SSL/TLS

Wget  ( es una herramienta de transferencia de archivos por línea de comandos, diseñada originalmente para GNU)

__Características principales__

Transferencia de archivos HTTP, HTTPS, FTP, y otros protocolos
Capacidad para realizar descargas secuenciales o simultáneas
Soporte para resumir descargas interrumpidas
Opciones avanzadas para autenticación, cabeceras, y seguimiento de cookies
Uso de proxies y redirecciones

Algunas opciones incluyen:

-O: Especificar un nombre de archivo de salida
-q: Modo silencioso (sin mensajes de progreso)
-c: Continuar una descarga interrumpida
-k: Convertir URLs relativas a absolutas
-r: Recorrer recursivamente directorios HTML

lsusb (List USB devices) muestra información sobre dispositivos USB conectados al sistema.

__Características principales__

Lista todos los dispositivos USB conectados
Muestra detalles técnicos de cada dispositivo
Indica el estado de los dispositivos (conectados, desconectados)
Uso básico de lsusb
El comando básico para usar lsusb es:

Algunas opciones útiles incluyen:

-v: Muestra información detallada de cada dispositivo
-t: Muestra la jerarquía de dispositivos
-d: Filtra dispositivos por IDVendor o IDProduct

lspci (List PCI devices) muestra información sobre dispositivos PCI y PCIe conectados al sistema.

__Características principales__

Lista todos los dispositivos PCI y PCIe
Muestra detalles técnicos de cada dispositivo
Indica el tipo de dispositivo (CPU, memoria, controladora, etc.)
Uso básico de lspci
El comando básico para usar lspci es:


Algunas opciones útiles incluyen:

-v: Muestra información detallada de cada dispositivo
-nn: Muestra nombres completos de los fabricantes y productos
-xxx: Muestra información extensa de cada dispositivo
