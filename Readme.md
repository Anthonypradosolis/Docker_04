DOCKER 04


1. Utiliza la imagen de Ubuntu , tag 22 y apoyandote en esta guía sigue sus instrucciones para instalar LAMP en dicho contenedor.


    sudo docker pull ubuntu:22.04

    sudo docker container create -i -t -p 8080:80 --name dam_lamp ubuntu:22.04    

    sudo docker container start --attach -i dam_lamp

    Ahora estamos dentro del contenedor:

    apt update

    apt install -y apache2 apache2-utils

    apt isntall -y mariadb-server mariadb-client

    service mariadb start

    apt install -y php php-mysql libapache2-mod-php
    

2. Utiliza esta guía para instalar wordpress en el contenedor.



3. Comprueba que puedes acceder a wordpress. 
