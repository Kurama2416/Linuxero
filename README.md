# Comandos básicos de ubuntu
### Problema de la hora con windows (dualbot)
Si tenemos windows junto con linux y nuestra hora se desconfigura, lo que tenemos que hacer para solucionarlo es usar este comando: 

    sudo timedatectl set-local-rtc 1

Este comando configura el sistema para que utilice la hora local en vez de UTC.

### Instalar paquetes .deb
Si queremos instalar un paquete en .deb debe usar este comando:

    sudo dpkg -i nombre.deb

