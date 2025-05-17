# Linuxero - Soluciones y comandos para Linux

![Linux](https://img.shields.io/badge/Linux-General-blue?style=flat-square&logo=linux)
![Estado](https://img.shields.io/badge/Estado-Activo-brightgreen?style=flat-square)
![Licencia](https://img.shields.io/badge/Licencia-CC%20BY%204.0-lightgrey?style=flat-square)

Repositorio dedicado a recopilar comandos útiles y soluciones a problemas comunes en diferentes distribuciones de Linux como Ubuntu, Fedora y más. 🚀

---

## 📌 Índice
- [Instalación y Uso](#instalación-y-uso)
- [Comandos Generales](#comandos-generales)
- [Gestores de Paquetes](#gestores-de-paquetes)
- [Errores y Soluciones](#errores-y-soluciones)
- [Contribuir](#contribuir)
- [Colaboradores](#colaboradores)
- [Licencia](#licencia)
- [Contacto](#contacto)

---

## ⚙️ Instalación y Uso
Para utilizar las soluciones de este repositorio, puedes clonar el proyecto en tu máquina local con:

```fish
    git clone https://github.com/Kurama2416/Linuxero.git
    cd Linuxero
```

Luego, accede a la documentación o ejecuta los scripts según tu necesidad.

---

## 🖥️ Comandos Generales
Lista de comandos básicos que funcionan en la mayoría de las distribuciones de Linux:

```fish
ls        # Listar archivos y directorios
cd        # Cambiar de directorio
pwd       # Mostrar el directorio actual
cp        # Copiar archivos o directorios
mv        # Mover o renombrar archivos o directorios
rm        # Eliminar archivos o directorios
touch     # Crear un archivo vacío
mkdir     # Crear un nuevo directorio
chmod     # Cambiar permisos de archivos
chown     # Cambiar propietario de archivos
```
📌 **Para más detalles, revisa [`comandos_linux`](Wiki/Linux%20General/comandos_linux.md)**

---

## 📦 Gestores de Paquetes
Los comandos de instalación de paquetes varían según la distribución:

| Comando | Ubuntu/Debian | Fedora | Arch Linux |
|---------|--------------|--------|------------|
| Actualizar sistema | `sudo apt update && sudo apt upgrade` | `sudo dnf update` | `sudo pacman -Syu` |
| Instalar paquete | `sudo apt install paquete` | `sudo dnf install paquete` | `sudo pacman -S paquete` |
| Eliminar paquete | `sudo apt remove paquete` | `sudo dnf remove paquete` | `sudo pacman -R paquete` |

📌 **Para más detalles, revisa [`gestores_paquetes`](Wiki/Linux%20General/gestores_paquetes.md)**

---

## ❌ Errores y Soluciones
Aquí encontrarás una lista de errores comunes y sus soluciones en varias distribuciones de Linux.

| Error | Distribución | Solución |
|--------|--------------|-----------|
| **Error: No se encuentra el paquete** | Ubuntu, Fedora, Arch | Verificar conexión y actualizar con el gestor de paquetes correspondiente |
| **Error: Permiso denegado** | Todas | Usar `sudo` antes del comando o cambiar permisos con `chmod` |
| **Error: Wi-Fi no funciona** | Ubuntu, Fedora | Reiniciar `NetworkManager` con `sudo systemctl restart NetworkManager` |

📌 **Para ver la lista completa, revisa [`errores_linux`](Wiki/Ubuntu/errores_linux.md)**

---

## 🤝 Contribuir
Si tienes soluciones adicionales, ¡puedes contribuir!

1. Haz un fork del repositorio.
2. Crea una nueva rama: `git checkout -b solucion-nueva`
3. Realiza tus cambios y haz un commit: `git commit -m 'Añadir nueva solución'`
4. Envía un pull request.

---

## 👥 Colaboradores
Agradecimientos especiales a quienes han contribuido a este proyecto:
- [Kurama2416](https://github.com/Kurama2416) *(Creador del repositorio)*
- [Bomba0429](https://github.com/Bomba0429)

---

## 📝 Licencia
Este proyecto está licenciado bajo la licencia **Creative Commons Attribution 4.0 International (CC BY 4.0)**. Puedes consultar más detalles en el archivo [`LICENSE`](LICENSE) o en la página oficial de [Creative Commons](https://creativecommons.org/licenses/by/4.0/).

---

## 📧 Contacto
Si tienes preguntas o sugerencias, puedes contactarme en mi perfil de GitHub: [Kurama2416](https://github.com/Kurama2416).

---

⭐ **Si este repositorio te ha sido útil, no olvides darle una estrella!** ⭐
