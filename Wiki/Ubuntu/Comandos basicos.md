# Comandos básicos de ubuntu
*mantenedor de la guia: Kurama2416*

### Problema de la hora con windows (dualbot)
Si tenemos windows junto con linux y nuestra hora se desconfigura, lo que tenemos que hacer para solucionarlo es usar este comando:

    sudo timedatectl set-local-rtc 1

Este comando configura el sistema para que utilice la hora local en vez de UTC.

### Instalar paquetes .deb
Si queremos instalar un paquete en .deb debe usar este comando:

    sudo dpkg -i nombre.deb

### Problema de actualización de paquetes
Si tenemos problemas con unos paquetes que no se actualizan con el comando `sudo apt upgrade` para ello haremos lo siguiente:

Instalaremos primero la herramienta para gestionar paquetes de forma segura, usaremos el siguiente comando:

    sudo apt install aptitude

Una vez instalado, usaremos el siguiente comando para actualizar los paquetes de forma segura que nos hiciera falta:

    sudo aptitude safe-upgrade
