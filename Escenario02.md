# Escenario 02 

Solución del segundo taller **Sistemas Distribuidos**

**Camilo Penagos Orejuela - A00301416**

**Julián Santiago Tauta Chaparro - A00022232**

**Santiago José Narváez Prado - A00027544**

## Proceso

1. **Maquina Virtual CentOS7:** Para crear la primera maquina virtual con Vagran, es necesario usar la consola de Visual Studio Code. Se unica la ruta (path) del archivo Vagranfile y mediante el comando **vagrant up** se hace efectiva la instalación de la MV en Virtual Box, usando como proovedor **Virtual Box.**

- Este es el archivo vagrant file de configuraicon inicial para nuestra maquina virtual CentOS7

  <img src ="E02/vagranfile1.JPG" height="280" >
  
- Se hace efectiva la creación de la maquina con el comando vagrant up

  <img src ="E02/vagrantup1.JPG" height="70" >
  
- Por ultimo se verifica que la maquina, efectivamente se ha creado y se puede acceder en Virtual Box

<img src ="E02/prueba1.JPG" height="240" >

2. **Acceder por SSH:** Despues de crear la MV, accedemos a ella de manera remota, para poder hacer gestion o tener acceso a la consola. Esto se logra mediante SSH y se hace efectivo con el comando **vagran ssh default** en la consola de Visual, depues de ello se veficia que ya tenemos acceso a la consola de la maquina virtual que hemos creado anteriormente.   


<img src ="E02/ssh.JPG" height="60" >


3. **Destruir un servidor y construir:** Para destruir una MV , se usa el comando **Vagrant destroy** , este detiene la maquina en ejecuccion y destruye todos los recursos y procesos que se crearon durante su ejecucción. Dejando la maquina host como si nunca hubiese creado nunca la maquina virtual. Sin embargo la caja que contiene la imagen de la MV seguira instalada en el host.


  <img src ="E02/destroy.JPG" height="50" >
   
- Se evidencia que la maquina virtual ha sido destruida y no se encuentra en ejecucción.

  <img src ="E02/destruida.JPG" height="70" >
  
- Con el comando **vagrant up** es posible reconstruir la MV y se evidencia que nuevamente se encuentra corriendo con el comando **vagrant status**

  <img src ="E02/reconstruida.JPG" height="70" >


4. **Crear dos servidores:** El siguiente paso es crear dos servidores virtuales, usando la herramienta Vagrant, que permite automatizar el proceso, y mediante un script crear las dos maquinas virtuales, con su configuración inicial. Para ello es necesario un archivo Vagrant file que se ejecute en la consola de Visual.


- Este es el archivo vagrant file de configuracion inicial, para la creacion de los dos servidores.

<img src ="E02/vagranfile2.JPG" height="280" >

- Con el comando **vagrant status** , se evidencia que los dos servidoreshan sido creados y se encuentran corriendo.

<img src ="E02/prueba2.JPG" height="80" >

- Igualmente se puede evidenciar que las maquinas efectivamente han sido creadas en Virtual Box


<img src ="E02/prueba3.JPG" height="220" >


5. **Descargar Ansible:** Esta tecnologia permite aprovisionar maquinas de forma automatizada por medio de scripts, al igual que administrar tareas y procesos de la MV. 

- Para instalar Ansible, se debe instalar **Anaconda**, este software permite bajar el Ansible compatible con Windows 10.

<img src ="E02/Conda.JPG" height="80" >

- Luego, desde la consola de Anaconda, se deben ejecutar los comandos:

`conda install -c conda-forge ansible`

`conda install -c conda-forge/label/cf201901 ansible`

Esto nos va a permitir descargar el Ansible a nuestro host windows para posteriormente aprovisionar los servidores con las aplicaciones.


6. **Aprovisionamiento de los servidores:** Utilizando Ansible se pueden aprovisionar las maquinas virtuales de manera automatizada mediante scripts que permiten hacer la gestion de las aplicaciones o servidios que se instalan en las maquinas. Para uno de los servidores se tendra que aprovisionar un servidor web **Nginx** y el segundo servidor tendra un servidor de base de datos **postgresql.**

- El archivo de configuración inicial Vagrant file, especifica la ruta donde se encuentra el script de ansible, que va a permitir aprovisionar los servidores que se van a crear usando vagrant.Ademas en el archivo de host, se especifica las maquinas virtuales que seran aprovisionadas mediante el script.

<img src ="E02/vagranfile3.JPG" height="240" >


- Se crean las maquinas virtuales, despues de dar Vagrant up al archivo de configuración.

<img src ="E02/Maquinas.JPG" height="270" >



## Problemas:
   
En el desarrollo del taller, se presentaron algunos inconvenientes de incompatibilidad con el sistema operativo Windows. El primer inconveniente fue la descarga del software Ansible, ya que se tuvo que usar la distribución de Anaconda como servidor, para descargar el software. Aunque el proceso de instalación se terminó correctamente, el Vagrant no identifica el aprovisionador Ansible en el sistema operativo, notificando un mensaje de error que el Ansible no está instalado y no es posible aprovisionar las maquinas. Es decir, para hacer el aprovisionamiento de las maquinas se debía hacer desde el mismo Ansible guest, usando el Ansible de cada máquina virtual que ya ha sido creada con Vagrant.

## Reflexión:

La automatización es la forma optima para la configuración, administración y despliegue de maquinas en entornos de producción. La automatizacíon como codigo permite crear y configurar maquinas rapidamente,siendo adecuada para sistemas distribuidos y microservicios. La infraestuctura como codigo permite automatizas, acelerar, integrar y repetir tareas de administración y gestion de TI. Sin embargo la IaC necesita mucha practica para realizar las configuracion correctas y las tareas se ejecuten de manera adecuada. La IaC es propensa a errores de configuracion, incompatbilidad, permisos y ejecucción. Ademas no resulta tan intuitiva como las interfaces graficas o asistentes de instlación. La IaC es optima para ambientes de prueba o produccion donde se requiera automatizar numerosas tareas de gestión y administración de servicios TI.






