# Escenario UNO

Solución primer laboratorio del curso  **Sistema Distribuidos**

**Camilo Penagos Orejuela A00301416 **

## Proceso

 1. **VirtualBox:** El proceso de instalación de virtual box es bastante sencillo, basta con buscar en el navegador, el sitio web oficial de descargar de virtual box y seleccionar el paquete de la plataforma correspondiente. En mi caso descargo el paquete de un **host windows**. Virtual box es un hipervisor liviano, que se instala rápidamente y no presenta dificultades en el proceso de instalación.
 
      <img src ="Imagenes1D/VirtualBox.JPG" height="300" >

2. **CentOS:** El paso siguiente es descargar una maquina virtual CentOS que sea soportada por el hipervisor VirtalBox, para hacer la respectiva instalación de la misma, en este caso la imagen ISO corresponde a **CentOS7**. 
- El primer paso es crear la maquina virtual en VirtualBox

    <img src ="Imagenes1D/crearMV.JPG" height="300" >
    
- Despues se configuran las caracterisitcas de hardware virtual de la maquina, memoria RAM, espacio de disco y  tarjeta de red

- Luego de debe asignar el **controlador** de IDE, que corresponde a la imagen ISO de CentOS7, de esta manera VirtaulBox procede con el boot inicial para crear instalar la maquina virtual 

    <img src ="Imagenes1D/imageniso.JPG" height="200" >
    
 - Posteriormente se debe proceder con la configuracion incial del sistema operativo CentOS, donde se establecen las preferencias de idioma, entrada de texto y el tipo de instalación, en este caso la opcion es **servidor con GUI**, de manera que el sistema operativo tenga una interfaz de usuario y reconozca los comandos de administración e instalación de servicios. El proceso de inslación tarda mas de 30 minutos en completarse correctamente.
 
- Finalmente se configuran el usuario de la maquina virtual y el usuario root para administracion.

- De esta manera tendremos una maquina virtual CentOS7 totalmente configurada y lista para usar.

    <img src ="Imagenes1D/inicio.JPG" height="320" >

3. **Nginx:** El proceso de descarga e instalacion del servidor Nginx no resulta muy complejo, para instalar este servicio en la maquina virtual se debe ejecutar los siguientes comandos, para ello se deben tener permisos de super usuario o root en la maquina.

`sudo yum install epel-release`

Bajar el repositorio 

`sudo yum install nginx`

Bajar el servicio Nginx

`sudo systemctl start nginx`

Iniciar el servidor web en la maquina

`sudo systemctl enable nginx`

Habilitar el servicio en el sistema

`sudo firewall-cmd --permanent --zone=public --add-service=http` 

`sudo firewall-cmd --permanent --zone=public --add-service=https`

`sudo firewall-cmd --reload`

Habilitar el trafico web(http) y web seguro (https) en el firewall de la maquina virtual

- De esta manera se tiene un servidor web configurado

<img src ="Imagenes1D/prueba.JPG" height="320" >

4. **Acceso y red host only:** Para acceder al servidor web(maquina CentOS7) desde el host principal, se procede crear una red **host only**

- Para ello se debe crear un adaptador de red virtual en el *host*. Esto se hace en virtual box, en la pestaña preferencias se crea un nuevo adaptador de red y ademas se configura un servidor **DHCP** para la asignación dinamica de direcciones IP.

<img src ="Imagenes1D/hostonly.JPG" height="280" >

- Luego de debe configurar la preferencia de red para el guest, de manera que se concecte a la red host only. Se espera que al conectarse a la red, obtenga una direccion **IP** otorgada por el servidor DHCP configurado anteriormente.

<img src ="Imagenes1D/ipv4.JPG" height="130" >

- Se verifica que el host Windows, tenga un adaptador de red virtual para conectarse a la red host only

<img src ="Imagenes1D/hostonlyw.JPG" height="200" >

- Por ultimo accedemos desde el host al servidor web alojado en la maquina CentOS7 usando **http://192.168.92.3** y se despliega el index del servidor.


<img src ="Imagenes1D/pruebafinal.JPG" height="300" >


## Dificultades

- La mayor dificultad se presento en el proceso de instalación de **CentOS7**, el proceso de instalacíon es muy lento y resulta engorroso la selección de tantas preferencias de instalación, como configurar los usuarios y el root, entradas de texto, almacenamiento fuente y destino, y demas.

- Configurar la red **host only** presento dificultades, ya que desconocia el proceso de configuración y en un primer intento no habia configurado de manera correcta el adaptador virtual para el host, igualmente el servicio DHCP no funcionaba correctamente , de manera que no lograba que el host Windows y el guest CentOS7 se comunicaran en la red.

## Reflexión

- El mundo actual es cambiante y dinámico, como lo son los negocios, las empresas y sobre todo la tecnología. Por esta razón, las tareas manuales resultan inadecuadas sobre todo para temas de infraestructura de red, ambientes de desarrollo y de pruebas. Estas tareas totalmente manuales, pueden ser un poco más sencillas en la medida que se cuenta con una GUI, pero se traducen en una gran pérdida de tiempo en la instalación, configuración y soporte de los servicios de TI que se despliegan. En este laboratorio, donde solo se necesitaba configurar una maquina virtual y un servicio web en la misma, se evidencio que una tarea al parecer simple puede tomar mucho más tiempo del necesario. Seguramente las tareas de configuración manual pueden ser muy útiles en algunos contentos, pero para las infraestructuras de red y sistemas resultan inadecuadas. Por esta razón se debe buscan automatizas al máximo las tareas, reduciendo el tiempo de ejecución de las mismas y optimizando cada vez más los procesos





