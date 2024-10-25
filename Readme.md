DOCKER 04


1. Utiliza la imagen de Ubuntu , tag 22 y apoyandote en esta guía sigue sus instrucciones para instalar LAMP en dicho contenedor.

    
    Con este comando descargamos la imagen de ubuntu 22.04:

    sudo docker pull ubuntu:22.04

    Con este comando creamos el contenedor dam_lamp con la imagen de arriba y añadimos los puertos

    sudo docker container create -i -t -p 8080:80 --name dam_lamp ubuntu:22.04    

    Con este comando arrancamos el contenedor y entramos en el:

    // --attach: adjunta la salida estandar y de error del contenedor al terminal actual,

    // permitiendo ver la salida del contenedor en tiempo real.

    // -i: mantiene la entrada estandar abierta, lo que permite 

    // interactuar con el     contenedor.

    sudo docker container start --attach -i dam_lamp

    Con este comando instalamos los paquetes necesarios para LAMP, todo dentro del contenedor:
    Seguimos los pasos de la guía:
    apt update

    apt install -y apache2 apache2-utils

    apt isntall -y mariadb-server mariadb-client

    service mariadb start

    mysql_secure_installation
<details >  
    root@107384a620ee:/# mysql_secure_installation

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user. If you've just installed MariaDB, and
haven't set the root password yet, you should just press enter here.

Enter current password for root (enter for none):
OK, successfully used password, moving on...

Setting the root password or using the unix_socket ensures that nobody
can log into the MariaDB root user without the proper authorisation.

You already have your root account protected, so you can safely answer 'n'.

Switch to unix_socket authentication [Y/n] n
... skipping.

You already have your root account protected, so you can safely answer 'n'.

Change the root password? [Y/n] y
New password:
Re-enter new password:
Sorry, you can't use an empty password here.

New password:
Re-enter new password:
Sorry, you can't use an empty password here.

New password:
Re-enter new password:
Sorry, you can't use an empty password here.

New password:
Re-enter new password:
Password updated successfully!
Reloading privilege tables..
... Success!


By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] y
... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] y
... Success!

By default, MariaDB comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] y
- Dropping test database...
  ... Success!
- Removing privileges on test database...
  ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] y
... Success!

Cleaning up...

All done!  If you've completed all of the above steps, your MariaDB
installation should now be secure.

Thanks for using MariaDB!
</details>

    apt install -y php php-mysql libapache2-mod-php
    
    echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php

    service apache2 start    

    Esto desde el navegador:

    http://localhost:8080
    http://localhost:8080/info.php
  
![Apache](Fotos/ubuntu.png)

![Apache](Fotos/fotophp.png)

2. Utiliza esta guía para instalar wordpress en el contenedor.



3. Comprueba que puedes acceder a wordpress. 
