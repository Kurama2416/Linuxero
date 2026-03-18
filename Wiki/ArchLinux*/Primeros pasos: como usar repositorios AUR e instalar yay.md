# Primeros pasos en ArchLinux: Como usar los repositorios AUR e instalar yay

Tal vez mientras descargabas la imagen de ArchLinux te habras dado cuenta de dos pestañas, uno llamado "packgages" y otro llamado "AUR" y tal vez no hayas entendido nada en caso de que hayas entrado




Si has venido de otras distribuciones de linux sabras que cada distribucion centraliza su propio almacen de aplicaciones 

Este tipo de repositorio no se puede acceder desde la paqueteria pacman o desde la tienda de aplicaciones, este usa un manejador diferente de paquetes especial para AUR, existen 4 alternativas, pero para no caer en confusiones esta guia te enseñara a instalar y usar `yay` como un experto.

### Paso 1: requisitos

para instalar yay se necesitan de los siguientes paquetes todos se instalan via terminal usando este comando

```sh
sudo pacman -S --needed git base-devel
```
*donde `--needed` significa que si el paquete esta instalado y actualizado entonces lo ignore y siga al siguiente requisito*

**PROTIP:** *Puedes aprender este y mas comandos en nuestra guia [Gestores paquetes](www.startpage.com)*

### Paso 2: Instalacion

Una vez cumplido el requisito comenzamos a instalar, primero descargamos los archivos de yay desde el [repositorio oficial de yay en AUR](https://aur.archlinux.org/packages/yay-bin)

```sh
git clone https://aur.archlinux.org/yay-bin.git
```

ahora descargado el paquete entramos a su carpeta desde terminal  

```sh
cd yay-bin
```  
y dentro de la carpeta comenzamos a armar el paquete e instalarlo  
```sh
makepkg -si
```
La instalacion debe de comenzar de inmediato, deberia aparecerte algo como esto, escribes `S` en la pregunta para instalarlo. NO necesita permisos root  

![imagen]()  

si todo te ha salido bien (como en esta imagen de ejemplo) entonces ya estas listo para usar el repositorio AUR

![Imagen]()  

### Paso 3: primer uso de yay y el repositorio AUR

Para probar que todo se hizo bien probaremos en instalar una aplicacion usando los repositorios AUR con estos sencillos pasos

#### paso 3.1: visita la pagina de ArchLinux AUR

en tu navegador ingresa a *





#### usar yay

ahora que he elegido mi aplicacion entonces usamos el siguiente comando

```sh
yay -S brave-bin
```


