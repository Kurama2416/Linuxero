# Manejo basico de la paqueteria Fedora (DNF)
*mantenedor de la guia: Bomba0429*

Una particularidad en estas distribuciones de Fedora es el cambio de manejo de repositorios. En vez de usar ``apt`` como en las distribuciones basadas en ubuntu/debian, este usa ``dnf``, a pesar del cambio de paqueteria no debes preocuparte, el uso de esta paqueteria es muy parecido al ``apt`` y en esta guia te mostrare los comandos basicos para poder usar fedora como si nada

## Instrucciones:

1. Abrir una terminal
2. ejecutar alguno de los siguientes comandos

## Instalar / Desinstalar aplicaciones

- Actualizar paquetes del sistema / actualizar sistema

````> sudo dnf update````

- Instalar un paquete del repositorio

````> sudo dnf install <nombreaplicacion>````

ejemplo: `> sudo dnf install vlc`

- Instalar paquete desde un directorio

NOTA: Primero debes de dirigirte al directorio donde se localiza el paquete y dando clic derecho en un espacio en blanco, selecciona la opcion "abrir terminal aqui / abrir una ventana de terminal aqui"

````> sudo dnf install ./nombrepaquete.rpm````

- Desinstalar / Eliminar un paquete instalado

````> sudo dnf remove <nombrepaquete>````


## comandos utiles


