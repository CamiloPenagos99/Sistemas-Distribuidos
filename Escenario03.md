### Julián Santiago Tauta Chaparro - A00022232
### Camilo Penagos Orejuela - A00301416
### Santiago José Narváez Prado - A00027544

# Escenario 03
###### En este escenario se hará uso de lo aprendido anteriormente para implementar una aplicación web que haga uso de una base de datos, el sistema debe permitir insertar y listar datos de una tabla en la base de datos. La aplicación debe ser desplegada en un servidor web y la base de datos en un servidor aparte.

#### Recursos usados:
###### - Virtual-box
###### - ISO de Ubuntu 18.04
###### - Vagrant
###### - Ansible
###### - NodeJS
###### - MongoDB
###### - Express

### Procedimiento:

###### 1. En primer lugar, con ayuda de NodeJS se implementó la pagina web. Se implementó tanto el cliente como el servidor.

*La aplicación web se encuentra en el siguiente repositorio: https://github.com/julianstauta/W1Scenary3

###### 2. Después, se procedió a configurar el archivo VagrantFile así como se muestra en la siguiete imagen:


###### 3. Paso a seguir, se configuró Ansible para establecer como servicio la base de datos, la cual corresponde a MongoDB. La configuración de Ansible se muestra a continuación:


###### 4. Se procedió a crear unos archivos adicionales:
###### 4.1 Se creó un archivo Host, el cual contiene el nombre y las direcciones de los dos host, es decir, la base de datos y el servidor de la aplicación web., el cual será usado por Ansible.
###### 4.2. Es necesario crear un archivo llamado mongodb.conf para poder establecer la configuración inicial de la base de datos.

###### 5. Se procede a ejecutar el sistema distribuido
###### 5.1. Se ejecuta el comando 'vagrant up' en la consola de comandos, ubicado en el directorio raíz del proyecto.

### Uso del sistema
###### 1. Se ingresa al navegador y se escribe la dirección http://192.168.56.3:1024
###### 2. Se agrega un nombre en la barra que dice 'Add name' y se presiona el botón 'Add'

###### 3. Como se observa, el nombre se agregó de manera exitosa, y también se puede eliminar, dando clic en el boton del tarro de basura.

### Dificultades
###### 1. Se encontró un bug con Vagrant, el cual no permitía avanzar despues de que saliera el mensaje SSH auth method: private key, debido a que se quedaba congelada la ejecución. Por esta razón, se decidió reinstalar Vagrant y actualizarlo.
###### 2. El formato del archivo .yml para la configuracion de ansible es bastante estricto entonces tocaba manipularlo con mucho cuidado.
###### 3. Tanto vue como express no exponen sus servicios en ips especificas por defecto, por tanto al comienzo no lograbamos hacer que se comuncaran remotamente, sin embago encontramos la manera de configurar la ip y el puerto que queriamos para poder lograr esto.

