# Linuxero · La terminal ya no muerde

[![Sitio](https://img.shields.io/badge/Leer%20online-kurama2416.github.io%2FLinuxero-f97316?style=flat-square)](https://kurama2416.github.io/Linuxero/)
[![Último commit](https://img.shields.io/github/last-commit/Kurama2416/Linuxero?style=flat-square&label=%C3%BAltima%20actualizaci%C3%B3n)](https://github.com/Kurama2416/Linuxero/commits/main)
[![Licencia](https://img.shields.io/badge/Licencia-CC%20BY%204.0-lightgrey?style=flat-square)](LICENSE)
[![Estrellas](https://img.shields.io/github/stars/Kurama2416/Linuxero?style=flat-square&label=estrellas)](https://github.com/Kurama2416/Linuxero/stargazers)

**Comandos esenciales y soluciones a errores comunes en Linux, explicados en español y pensados para quien está empezando.**

👉 **[Leer la wiki online](https://kurama2416.github.io/Linuxero/)**: es la forma más cómoda de consultarla, con buscador, menú por secciones y botón para copiar comandos.

<!-- Añade aquí una captura del sitio, por ejemplo: ![Vista de la wiki](docs/captura.png) -->

## Índice

- [Para quién es](#para-quién-es)
- [Empieza aquí](#empieza-aquí)
- [Qué encontrarás](#qué-encontrarás)
- [Comandos esenciales](#comandos-esenciales)
- [Gestores de paquetes](#gestores-de-paquetes)
- [Errores comunes](#errores-comunes)
- [Distribuciones cubiertas](#distribuciones-cubiertas)
- [Qué viene](#qué-viene)
- [Cómo usarlo sin conexión](#cómo-usarlo-sin-conexión)
- [Contribuir](#contribuir)
- [Colaboradores](#colaboradores)
- [Licencia](#licencia)
- [Contacto](#contacto)

## Para quién es

Para quien quiere usar Linux sin preocuparse: si nunca abriste una terminal, si migras desde Windows o si ya la usas pero siempre acabas buscando el mismo comando. Cada explicación va al grano, con ejemplos que puedes copiar y pegar.

> [!WARNING]
> Antes de tocar particiones, borrar archivos o ejecutar comandos con `sudo`, haz una copia de seguridad de lo que no quieras perder. Si un comando no lo entiendes, búscalo aquí o pregunta antes de ejecutarlo.

## Empieza aquí

Si es tu primera vez, te sugerimos este orden:

1. **Aprende lo básico:** revisa los [comandos esenciales](#comandos-esenciales) de más abajo y la [guía completa de comandos](Wiki/Linux%20General/comandos_linux.md).
2. **Instala programas:** entiende cómo funcionan los [gestores de paquetes](#gestores-de-paquetes).
3. **Cuando algo falle:** consulta los [errores comunes](#errores-comunes).

🚧 Estamos preparando una guía para elegir distribución, instalar Linux paso a paso y configurarlo después. Puedes ver lo que viene en [Qué viene](#qué-viene).

## Qué encontrarás

| Tema | Contenido | Dónde |
| ---- | --------- | ----- |
| Comandos | Guía de comandos de Linux con uso básico, opciones y ejemplos | [`comandos_linux`](Wiki/Linux%20General/comandos_linux.md) |
| Paquetes | Cómo instalar, actualizar y eliminar software en cada distribución | [`gestores_paquetes`](Wiki/Linux%20General/gestores_paquetes.md) |
| Errores | Soluciones a problemas frecuentes | [`errores_linux`](Wiki/Ubuntu/errores_linux.md) |

## Comandos esenciales

Los diez que más vas a usar. El semáforo te indica cuánto cuidado necesitas:

| Comando | Qué hace | Riesgo |
| ------- | -------- | ------ |
| `ls` | Lista archivos y carpetas | 🟢 Seguro |
| `cd` | Cambia de carpeta | 🟢 Seguro |
| `pwd` | Muestra en qué carpeta estás | 🟢 Seguro |
| `touch` | Crea un archivo vacío | 🟢 Seguro |
| `mkdir` | Crea una carpeta | 🟢 Seguro |
| `cp` | Copia archivos o carpetas | 🟡 Puede sobrescribir |
| `mv` | Mueve o renombra | 🟡 Puede sobrescribir |
| `chmod` | Cambia permisos | 🟡 Evita `chmod -R 777` |
| `chown` | Cambia el propietario | 🟡 Con `-R` puede romper permisos |
| `rm` | Elimina archivos (no hay papelera) | 🔴 Borra para siempre, cuidado con `rm -r` y `rm -rf` |

💡 Añade `-i` a `cp`, `mv` y `rm` para que pregunte antes de sobrescribir o borrar.

📌 Para opciones y ejemplos de cada uno: [`comandos_linux`](Wiki/Linux%20General/comandos_linux.md).

## Gestores de paquetes

Instalar programas cambia según la distribución:

| Acción | Ubuntu / Debian | Fedora | Arch Linux |
| ------ | --------------- | ------ | ---------- |
| Actualizar el sistema | `sudo apt update && sudo apt upgrade` | `sudo dnf upgrade` | `sudo pacman -Syu` |
| Buscar un paquete | `apt search nombre` | `dnf search nombre` | `pacman -Ss nombre` |
| Instalar un paquete | `sudo apt install paquete` | `sudo dnf install paquete` | `sudo pacman -S paquete` |
| Eliminar un paquete | `sudo apt remove paquete` | `sudo dnf remove paquete` | `sudo pacman -R paquete` |
| Instalar un archivo descargado | `sudo apt install ./archivo.deb` | `sudo dnf install ./archivo.rpm` | `sudo pacman -U archivo.pkg.tar.zst` |

📌 Más detalle: [`gestores_paquetes`](Wiki/Linux%20General/gestores_paquetes.md).

## Errores comunes

| Error | Distribución | Qué hacer |
| ----- | ------------ | --------- |
| **No se encuentra el paquete** | Ubuntu, Fedora, Arch | Actualiza la lista de paquetes (`sudo apt update` en Ubuntu), revisa que el nombre esté bien escrito y búscalo con `apt search`, `dnf search` o `pacman -Ss` |
| **Permiso denegado** | Todas | Mira los permisos con `ls -l`. Usa `sudo` solo si entiendes qué hace el comando. No recurras a `chmod 777` |
| **El Wi-Fi no funciona** | Ubuntu, Fedora | Reinicia el servicio de red: `sudo systemctl restart NetworkManager` |

📌 Lista completa, con la hora desajustada con Windows y la instalación de `.deb`: [`errores_linux`](Wiki/Ubuntu/errores_linux.md).

## Distribuciones cubiertas

| Distribución | Estado | Versión probada |
| ------------ | ------ | --------------- |
| Ubuntu / Debian | ✅ Cubierta | _por completar_ |
| Fedora | 🚧 En progreso | _por completar_ |
| Arch Linux | 🚧 En progreso | _por completar_ |

## Qué viene

- [ ] Guía para elegir distribución e instalar Linux paso a paso (USB booteable, probar sin instalar, instalar junto a Windows)
- [ ] Primeros pasos después de instalar: actualizaciones, drivers, códecs, Flatpak y copias de seguridad
- [ ] Tabla de equivalencias: «si usabas X en Windows, usa Y en Linux»
- [ ] Glosario para principiantes
- [ ] Comandos separados por tema
- [ ] Errores para Fedora y Arch
- [ ] Hoja de trucos en PDF
- [ ] Buscador en toda la wiki

## Cómo usarlo sin conexión

Si prefieres tenerlo en tu equipo:

```bash
git clone https://github.com/Kurama2416/Linuxero.git
cd Linuxero
python3 -m http.server 8000
```

Luego abre `http://localhost:8000` en tu navegador. El servidor es necesario porque el visor carga los documentos con `fetch`, y los navegadores lo bloquean al abrir `index.html` directamente.

También puedes leer los archivos `.md` de la carpeta `Wiki/` con cualquier editor de texto.

## Contribuir

¡Toda ayuda cuenta, incluso corregir un error!

- **Sin saber Git:** abre un [issue](https://github.com/Kurama2416/Linuxero/issues) contando qué falla, qué falta o qué comando te gustaría ver. También puedes editar un archivo directamente desde GitHub con el icono del lápiz.
- **Con Git:**
  1. Haz un fork del repositorio.
  2. Crea una rama: `git checkout -b solucion-nueva`
  3. Haz tus cambios y un commit: `git commit -m "Añadir nueva solución"`
  4. Envía un pull request.

Si añades una solución, indica en qué distribución y versión la probaste.

## Colaboradores

Gracias a quienes hacen posible este proyecto:

- [Kurama2416](https://github.com/Kurama2416) _(creador)_
- [Bomba0429](https://github.com/Bomba0429)


## Licencia

Los textos de este proyecto están bajo la licencia **Creative Commons Attribution 4.0 International (CC BY 4.0)**. Puedes compartirlos y adaptarlos citando la fuente. Consulta el archivo [`LICENSE`](LICENSE) o la [licencia oficial](https://creativecommons.org/licenses/by/4.0/deed.es).

## Contacto

¿Preguntas o sugerencias? Abre un [issue](https://github.com/Kurama2416/Linuxero/issues) o escribe a [Kurama2416](https://github.com/Kurama2416).

---

⭐ **Si Linuxero te ayudó, dale una estrella al repositorio.** Así llega a más gente que está empezando.
