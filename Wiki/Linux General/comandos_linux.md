
### Administración de Archivos y Directorios

La gestión de archivos y directorios es una tarea clave en el uso de la terminal en Linux. A través de estos comandos, es posible navegar por la jerarquía del sistema, organizar información y manipular datos de manera eficiente. A continuación, se presentan los comandos esenciales para esta categoría.

---

## 1. `ls` – Mostrar el Contenido de un Directorio

El comando `ls` (list) permite listar los elementos dentro de una carpeta, mostrando archivos y subdirectorios. Es la herramienta principal para visualizar qué hay en una ubicación específica.

**Uso básico**

```fish
ls [opciones] [directorio]
```

**Opciones**

- `-a`, `--all` → Muestra todos los archivos, incluyendo los ocultos (los que empiezan con .).

- `-l` → Muestra el formato largo con detalles (permisos, propietario, grupo, tamaño y fecha).

- `-h`, `--human-readable` → Junto con -l, muestra los tamaños en formato legible (KB, MB, GB).

- `-t` → Ordena los archivos por fecha de modificación (los más nuevos primero).

- `-S` → Ordena los archivos por tamaño (de mayor a menor).

- `-r`, `--reverse` → Invierte el orden de clasificación.

- `-R`, `--recursive` → Lista el contenido de todos los subdirectorios de forma recursiva.

- `-i` → Muestra el número de inodo de cada archivo.

- `-d` → Muestra información del directorio en lugar de su contenido.

- `-1` → Muestra un archivo por línea.

**Ejemplos**

```fish
ls -lah              # Muestra todos los archivos con detalles y tamaños legibles
ls -lt               # Ordena por fecha de modificación, más recientes primero
ls -R /etc           # Lista recursivamente todo el contenido de /etc
ls -i archivo.txt    # Muestra el número de inodo del archivo
```
---

## 2. `cd` – Cambiar de Directorio

El comando `cd` (change directory) es la herramienta fundamental para desplazarse a través de la estructura de carpetas del sistema.

**Uso básico**

```fish
cd [directorio]
```

**Opciones**

- El comando `cd` no tiene opciones directas, pero acepta rutas absolutas y relativas.

**Ejemplos**

```fish
cd /var/log          # Cambia al directorio /var/log
cd ..                # Sube un nivel en la jerarquía (va al directorio padre)
cd ~                 # Te lleva directamente a tu carpeta personal (home)
cd -                 # Regresa al directorio anterior donde te encontrabas
cd                   # Sin argumentos, también lleva al home del usuario
cd Documentos        # Cambia al subdirectorio Documentos (ruta relativa)
```
---

## 3. `pwd` – Mostrar la Ruta del Directorio Actual

El comando `pwd` (print working directory) sirve para confirmar tu ubicación exacta dentro del sistema de archivos, mostrando la ruta absoluta desde la raíz.

**Uso básico**

```fish
pwd [opciones]
```

**Opciones**

- `-P` → Muestra la ruta física real, resolviendo enlaces simbólicos.

- `-L` → Muestra la ruta lógica (con enlaces simbólicos). Es el comportamiento por defecto.

**Ejemplos**

```fish
pwd                  # Muestra la ruta actual, ej: /home/usuario/proyectos
pwd -P               # Muestra la ruta real si estás en un enlace simbólico
```
---

## 4. `tree` – Visualizar Directorios en Forma de Árbol

El comando `tree` muestra la estructura de carpetas y archivos de forma gráfica y jerárquica, similar a un árbol invertido.

**Uso básico**

```fish
tree [opciones] [directorio]
```

**Opciones**

- `-a` → Muestra también archivos ocultos (los que comienzan con .).

- `-d` → Muestra solo los directorios.

- `-L` [nivel] → Limita la profundidad del árbol al nivel especificado.

- `-f` → Muestra la ruta completa de cada archivo.

- `-p` → Muestra los permisos de cada archivo o directorio.

- `-u` → Muestra el nombre del propietario.

- `-g` → Muestra el nombre del grupo propietario.

- `-h` → Muestra los tamaños en formato legible.

- `-D` → Muestra la fecha de la última modificación.

- `-C` → Colorea la salida según el tipo de archivo.

**Ejemplos**

```fish
tree -L 2            # Muestra el árbol con profundidad máxima de 2 niveles
tree -d              # Muestra solo los directorios, sin archivos
tree -p -u /home     # Muestra permisos y propietarios en /home
tree -a -C           # Muestra todo con colores
```
---

## 5. `stat` – Información Detallada de un Archivo

El comando `stat` proporciona una radiografía completa del archivo, exponiendo metadatos como permisos, fechas de acceso y modificación, tamaño y más información que otros comandos omiten.

**Uso básico**

```fish
stat [opciones] [archivo]
```

**Opciones**

- `-f` → Muestra el estado del sistema de archivos, no del archivo.

- `-c`, `--format` → Extrae datos específicos usando secuencias de formato.

- `-t`, `--terse` → Muestra la información en formato conciso.

- `-L` → Sigue enlaces simbólicos y muestra información del archivo apuntado.

**Formatos útiles con `-c`**

- `%a` → Permisos en formato octal.

- `%A` → Permisos en formato legible (rwxr-xr-x).

- `%U` → Nombre del propietario.

- `%G` → Nombre del grupo.

- `%y` → Fecha y hora de la última modificación.

- `%s` → Tamaño en bytes.

- `%n` → Nombre del archivo.

**Ejemplos**

```fish
stat script.sh               # Muestra toda la información del archivo
stat -c "%a %U %G" archivo   # Permisos en octal, propietario y grupo
stat -c "%y %s" config.conf  # Solo fecha de modificación y tamaño
stat -f /home                # Información del sistema de archivos de /home
```
---

## 6. `mkdir` – Crear un Directorio

El comando `mkdir` (make directory) se utiliza para crear carpetas nuevas. Es la herramienta base para organizar cualquier estructura de trabajo en el sistema.

**Uso básico**

```fish
mkdir [opciones] nombre_directorio
```

**Opciones**

- `-p`, `--parents` → Crea toda una ruta de directorios. Si las carpetas intermedias no existen, las crea automáticamente sin dar error.

- `-v`, `--verbose` → Muestra un mensaje de confirmación por cada directorio creado.

- `-m`, `--mode` → Establece los permisos en el momento de la creación (en formato octal).

    - **755:** Dueño tiene todos los permisos (rwx), otros solo lectura y ejecución (r-x). Es el estándar.

    - **700:** Solo el dueño puede ver y entrar (privado).

    - **777:** Acceso total para todo el mundo (poco seguro, evitar).

- `-Z` → Establece el contexto de seguridad SELinux por defecto para el nuevo directorio.

**Ejemplos**

```fish
mkdir proyectos              # Crea un solo directorio
mkdir -p proyectos/python/app # Crea la ruta completa de varios niveles
mkdir -m 700 carpeta_privada  # Crea una carpeta restringida solo para el dueño
mkdir -v nuevo                # Crea la carpeta y muestra confirmación
```
---

## 7. `rmdir` – Eliminar Directorios Vacíos

El comando `rmdir` (remove directory) borra carpetas, pero solo si están completamente vacías. Es una medida de seguridad para evitar la pérdida accidental de datos.

**Uso básico**

```fish
rmdir [opciones] directorio
```

**Opciones**

- `-p`, `--parents` → Elimina el directorio y sus padres si estos también quedan vacíos tras el borrado.

- `-v`, `--verbose` → Confirma visualmente cada directorio que ha sido eliminado con éxito.

- `--ignore-fail-on-non-empty` → No devuelve un estado de error si el directorio contiene archivos (simplemente no lo borra).

**Ejemplos**

```fish
rmdir carpeta_vacia           # Borra el directorio si está vacío
rmdir -p proyecto/temp         # Borra 'temp' y también 'proyecto' si queda vacía
rmdir -v cache/                # Borra la carpeta confirmando la acción
```
---

## 8. `rm` – Eliminar Archivos o Directorios

El comando `rm` (remove) permite borrar elementos de forma definitiva. Al ser una herramienta crítica, sus opciones de seguridad y confirmación son vitales.

**Uso básico**

```fish
rm [opciones] archivo|directorio
```

**Opciones**

- `-r`, `-R`, `--recursive` → **Recursivo:** Obligatorio para borrar una carpeta junto con todo su contenido.

- `-f`, `--force` → **Forzado:** Ignora archivos inexistentes y nunca pide confirmación al usuario.

- `-i` → **Interactivo:** Pregunta antes de cada eliminación (la opción más segura).

- `-I` → Pregunta una sola vez antes de borrar más de tres archivos o al realizar un borrado recursivo.

- `-v`, `--verbose` → Muestra el nombre de cada archivo conforme va siendo eliminado del sistema.

- `-d`, `--dir` → Elimina directorios vacíos (alternativa a rmdir).

- `--preserve-root` → Evita que se borre accidentalmente el directorio raíz / (activado por defecto).

- `--no-preserve-root` → Permite borrar / (extremadamente peligroso, no usar).

**Ejemplos**

```fish
rm archivo.txt                # Borra un solo archivo
rm -r carpeta/                # Borra una carpeta y todo su contenido
rm -rf carpeta_vieja/         # Borra todo el contenido de una carpeta sin preguntar (¡cuidado!)
rm -i *.jpg                   # Borra todas las imágenes JPG pidiendo confirmación
rm -v documento.txt           # Borra y muestra confirmación
```
---

## 9. `cp` – Copiar Archivos o Directorios

El comando `cp` (copy) duplica elementos. Sus opciones avanzadas permiten gestionar versiones de archivos y preservar metadatos de seguridad.

**Uso básico**

```fish
cp [opciones] origen destino
```

**Opciones**

- `-r`, `-R`, `--recursive` → **Recursivo:** Copia directorios completos con su estructura interna.

- `-p`, `--preserve` → **Preservar:** Mantiene los atributos del archivo original, como permisos, propietario, grupo y marcas de tiempo.

- `-i`, `--interactive` → Pregunta al usuario antes de sobrescribir un archivo existente.

- `-f`, `--force` → Si el archivo de destino no se puede abrir, lo elimina y lo vuelve a intentar.

- `-u`, `--update` → Solo realiza la copia si el origen es más reciente que el destino.

- `-v`, `--verbose` → Muestra información detallada de la operación.

- `-a`, `--archive` → Copia recursivamente preservando todo (permisos, enlaces, etc.). Equivalente a `-dpR`.

- `-l`, `--link` → Crea enlaces duros en lugar de copiar.

- `-s`, `--symbolic-link` → Crea enlaces simbólicos en lugar de copiar.

- `-b`, `--backup` → Si el archivo de destino ya existe, crea una copia de seguridad del antiguo antes de copiar el nuevo.

**Ejemplos**

```fish
cp archivo.txt copia.txt       # Copia un archivo con nuevo nombre
cp -r proyectos/ respaldo/     # Copia todo un directorio recursivamente
cp -p config.conf config.bak   # Copia el archivo manteniendo metadatos originales
cp -i *.pdf Documentos/         # Copia PDFs preguntando antes de sobrescribir
cp --backup nota.txt /docs/     # Copia y crea un respaldo si ya existía el archivo
```
---

## 10. `mv` – Mover o Renombrar Archivos

El comando `mv` (move) desplaza archivos de ubicación o cambia su nombre. Es extremadamente eficiente ya que no mueve datos físicamente si el destino es el mismo disco.

**Uso básico**

```fish
mv [opciones] origen destino
```

**Opciones**

- `-v`, `--verbose` → Informa detalladamente de cada movimiento o cambio de nombre realizado.

- `-i`, `--interactive` → Pregunta antes de sobrescribir archivos que ya existan en el destino.

- `-n`, `--no-clobber` → Impide que se sobrescriba cualquier archivo que ya exista en el destino.

- `-u`, `--update` → Mueve el archivo solo si el origen es más reciente que el del destino.

- `-f`, `--force` → No pregunta antes de sobrescribir (predeterminado cuando se usa sin -i).

- `-b`, `--backup` → Crea una copia de seguridad de cualquier archivo de destino que vaya a ser reemplazado.

- `-t`, `--target-directory` → Permite mover varios orígenes a un destino específico.

**Ejemplos**

```fish
mv antiguo.txt nuevo.txt       # Cambia el nombre del archivo
mv archivo.txt Documentos/      # Mueve un archivo a un directorio
mv *.mp3 ~/Musica/              # Mueve todos los MP3 al directorio Musica
mv -u *.jpg Imagenes/           # Mueve solo las imágenes nuevas o actualizadas
mv -b config.php /servidor/     # Mueve y respalda la versión previa del servidor
```
---

## 11. `touch` – Crear Archivos Vacíos o Modificar Marcas de Tiempo

El comando `touch` se utiliza principalmente para crear archivos nuevos y vacíos. Sin embargo, su función técnica es cambiar las marcas de tiempo (acceso y modificación) de los archivos existentes.

**Uso básico**

```fish
touch [opciones] archivo
```

**Opciones**

- `-a` → Cambia únicamente la hora de acceso del archivo.

- `-m` → Cambia únicamente la hora de modificación del archivo.

- `-c`, `--no-create` → No crea el archivo si no existe; solo actualiza la fecha si el archivo ya está presente.

- `-t` → Permite especificar una fecha y hora personalizada (formato [[CC]YY]MMDDhhmm[.ss]).

- `-d`, `--date` → Usa una cadena de fecha descriptiva (ej: "next Sunday").

- `-r`, `--reference` → Utiliza la marca de tiempo de un archivo de referencia en lugar de la hora actual.

**Ejemplos**

```fish
touch nuevo_script.sh           # Crea un archivo vacío si no existe
touch -c inexistente.txt        # No crea nada si el archivo no está
touch -t 202601011200 nota.txt  # Cambia la fecha al 1 de enero de 2026 a las 12:00
touch -d "yesterday" archivo    # Cambia la fecha al día de ayer
touch -r origen.txt destino.txt # Aplica la fecha de origen.txt a destino.txt
touch -a -m archivo.txt         # Actualiza ambas marcas de tiempo (acceso y modificación)
```
---

## 12. `ln` – Crear Enlaces (Duros o Simbólicos)

El comando `ln` (link) crea vínculos entre archivos. Existen dos tipos: los enlaces duros (hard links) que son entradas adicionales al mismo inodo, y los enlaces simbólicos (soft links) que apuntan a la ruta de otro archivo, similares a accesos directos.

**Uso básico**

```fish
ln [opciones] objetivo nombre_enlace
```

**Opciones**

- `-s`, `--symbolic` → Crea un enlace simbólico (el método estándar para accesos directos).

- `-f`, `--force` → Elimina un archivo de destino previo con el mismo nombre para forzar la creación del enlace.

- `-i`, `--interactive` → Pregunta antes de eliminar archivos de destino existentes.

- `-n`, `--no-dereference` → Si el destino es un enlace a un directorio, lo trata como un archivo normal.

- `-v`, `--verbose` → Muestra el nombre de cada archivo conforme es enlazado.

- `-b` → Crea una copia de seguridad de los archivos de destino existentes.

- `-t`, `--target-directory` → Especifica el directorio donde colocar los enlaces.

**Ejemplos**

```fish
ln -s /var/www/html sitio_web   # Crea un enlace simbólico a la carpeta del servidor
ln -sf /ruta/nueva enlace_viejo # Sobrescribe un enlace existente de forma forzada
ln archivo.txt enlace_duro      # Crea un enlace físico (duro) al mismo inodo
ln -s /usr/bin/python python3   # Crea un enlace simbólico a un ejecutable
```
---

## 13. `alias` – Crear Alias de Comandos

El comando `alias` permite crear atajos o nombres personalizados para comandos más complejos o utilizados frecuentemente. Estos alias viven en la sesión actual de la terminal.

**Uso básico**

```fish
alias [nombre]='comando'
```

**Opciones**

- Sin opciones específicas, pero se usa para definir nuevos alias.

- `-p` → Muestra todos los alias definidos actualmente en la sesión.

**Ejemplos**

```fish
alias ll='ls -la'                          # Crea un alias para listar archivos con detalles
alias ..='cd ..'                            # Atajo para subir un nivel
alias instalar='sudo apt install'           # Para sistemas Debian/Ubuntu
alias -p                                     # Muestra todos los alias definidos
alias rm='rm -i'                             # Hace que rm siempre pregunte antes de borrar
```
---

## 14. `unalias` – Eliminar Alias Existentes

El comando `unalias` elimina alias que hayan sido definidos previamente con el comando `alias`.

**Uso básico**

```fish
unalias nombre_alias
```

**Opciones**

- `-a` → Elimina **todos** los alias definidos en la sesión actual.

- `-p` → Muestra los alias actuales (similar a `alias -p`).

**Ejemplos**

```fish
unalias ll                                   # Elimina el alias 'll'
unalias -a                                    # Elimina TODOS los alias definidos
unalias rm                                    # Elimina el alias de rm si fue modificado
```
---

## 15. `history` – Mostrar Historial de Comandos

El comando `history` muestra la lista de comandos ejecutados anteriormente en la terminal, permitiendo recuperar y reutilizar comandos sin tener que escribirlos nuevamente.

**Uso básico**

```fish
history [opciones]
```

**Opciones**

- `-c` → Limpia (borra) todo el historial de la sesión actual.

- `-d` [offset] → Elimina una entrada específica del historial.

- `-a` → Agrega las líneas de la sesión actual al archivo de historial.

- `-w` → Escribe el historial actual en el archivo de historial.

- `-r` → Lee el archivo de historial y lo agrega al historial actual.

**Ejemplos**

```fish
history                                    # Muestra todos los comandos ejecutados
history 20                                 # Muestra los últimos 20 comandos
!!                                         # Ejecuta el último comando
!100                                       # Ejecuta el comando número 100 del historial
!grep                                      # Ejecuta el último comando que comenzó con grep
history -c                                  # Borra todo el historial
```
---

## 16. `man` – Consultar el Manual de un Comando

El comando `man` (manual) muestra la documentación oficial de los comandos, incluyendo su sintaxis, opciones, ejemplos y más información detallada.

**Uso básico**

```fish
man [opciones] [comando]
```

**Opciones**

- `-k` [palabra] → Busca comandos relacionados con una palabra clave.

- `-f` [comando] → Muestra una breve descripción del comando.

- `-a` → Muestra todas las páginas del manual que coinciden con el nombre.

- `-w` → Muestra la ubicación física del archivo de manual.

- `-P` [visor] → Especifica qué programa usar para ver el manual (ej: less, more).

**Ejemplos**

```fish
man ls                                       # Abre el manual del comando ls
man -k "copy"                                # Busca comandos relacionados con copiar
man -f ls                                     # Muestra descripción breve de ls
man 5 passwd                                  # Muestra la sección 5 (archivos) de passwd
```
---

## 17. `help` – Ayuda Interna de Comandos de Shell

El comando `help` muestra información de ayuda para los comandos incorporados en la shell (built-in commands), aquellos que son parte del intérprete y no programas externos.

**Uso básico**

```fish
help [opciones] [comando]
```

**Opciones**

- `-d` → Muestra una breve descripción del comando.

- `-m` → Muestra la ayuda en formato similar a man page.

- `-s` → Muestra solo la sintaxis del comando.

**Ejemplos**

```fish
help cd                                       # Muestra ayuda del comando interno cd
help -d echo                                   # Muestra descripción breve de echo
help -s alias                                   # Muestra solo la sintaxis del comando alias
help                                            # Muestra todos los comandos internos disponibles
```
---

### Visualización y Procesamiento de Texto

Linux ofrece un poderoso conjunto de herramientas para visualizar, filtrar y transformar archivos de texto. Estos comandos son fundamentales para analizar logs, procesar datos y manipular información de manera eficiente desde la terminal. Desde la visualización simple hasta la edición avanzada con expresiones regulares, esta categoría cubre las herramientas esenciales para trabajar con texto.

---

## 18. `cat` – Mostrar el Contenido de un Archivo

El comando `cat` (concatenate) muestra el contenido completo de uno o más archivos en la salida estándar. Es la herramienta más básica para visualizar archivos pequeños.

**Uso básico**

```fish
cat [opciones] [archivo]
```

**Opciones**

- `-n` → Numera todas las líneas (incluyendo las líneas en blanco).

- `-b` → Numera solo las líneas que no están vacías.

- `-s` → Suprime líneas en blanco repetidas (muestra una sola línea vacía en lugar de varias).

- `-E` → Muestra un símbolo `$` al final de cada línea.

- `-T` → Muestra los tabuladores como `^I`.

- `-A` → Equivalente a `-vET` (muestra todos los caracteres no imprimibles).

**Ejemplos**

```fish
cat archivo.txt                              # Muestra el contenido del archivo
cat -n archivo.txt                            # Muestra el contenido con números de línea
cat -s archivo.txt                            # Comprime múltiples líneas en blanco
cat archivo1.txt archivo2.txt > combinado.txt # Une dos archivos en uno nuevo
```
---

## 19. `head` – Mostrar las Primeras Líneas de un Archivo

El comando `head` muestra las primeras líneas de un archivo, por defecto las 10 primeras. Es útil para echar un vistazo rápido al inicio de archivos grandes.

**Uso básico**

```fish
head [opciones] [archivo]
```

**Opciones**

- `-n`, `--lines` [N] → Muestra las primeras N líneas.

- `-c`, `--bytes` [N] → Muestra los primeros N bytes del archivo.

- `-q`, `--quiet` → No muestra los encabezados con el nombre del archivo (cuando se procesan múltiples archivos).

- `-v`, `--verbose` → Siempre muestra los encabezados con el nombre del archivo.

**Ejemplos**

```fish
head archivo.txt                              # Muestra las primeras 10 líneas
head -n 20 archivo.txt                         # Muestra las primeras 20 líneas
head -c 100 archivo.txt                         # Muestra los primeros 100 bytes
head -n 5 archivo1.txt archivo2.txt             # Muestra 5 líneas de cada archivo
```
---

## 20. `tail` – Mostrar las Últimas Líneas de un Archivo

El comando `tail` muestra las últimas líneas de un archivo, por defecto las 10 últimas. Es especialmente útil para monitorear archivos de log en tiempo real.

**Uso básico**

```fish
tail [opciones] [archivo]
```

**Opciones**

- `-n`, `--lines` [N] → Muestra las últimas N líneas.

- `-c`, `--bytes` [N] → Muestra los últimos N bytes del archivo.

- `-f`, `--follow` → Sigue el archivo en tiempo real, mostrando nuevas líneas a medida que se añaden.

- `-F` → Similar a `-f`, pero también funciona si el archivo es rotado (recreado).

- `-q`, `--quiet` → No muestra encabezados con el nombre del archivo.

- `-v`, `--verbose` → Muestra encabezados con el nombre del archivo.

**Ejemplos**

```fish
tail archivo.txt                               # Muestra las últimas 10 líneas
tail -n 50 archivo.txt                          # Muestra las últimas 50 líneas
tail -f /var/log/syslog                         # Sigue el log del sistema en tiempo real
tail -n 20 -f app.log                           # Muestra las últimas 20 líneas y sigue
```
---

## 21. `less` – Navegación Interactiva por Archivos

El comando `less` permite visualizar archivos de texto de forma interactiva, con capacidad de desplazamiento hacia adelante y atrás, búsqueda y navegación eficiente. Es ideal para archivos grandes.

**Uso básico**

```fish
less [opciones] [archivo]
```

**Opciones**

- `-N` → Muestra números de línea.

- `-S` → Corta las líneas largas en lugar de ajustarlas (útil para archivos con columnas).

- `-i` → Ignora mayúsculas/minúsculas en las búsquedas.

- `-F` → Si el archivo cabe en una pantalla, se comporta como cat.

- `-R` → Muestra los colores ANSI (útil para logs con colores).

- `-p` [patrón] → Comienza en la primera ocurrencia del patrón.

**Comandos de navegación dentro de less**

- `Espacio` o `f` → Avanzar una página.

- `b` → Retroceder una página.

- `Enter` → Avanzar una línea.

- `y` → Retroceder una línea.

- `g` → Ir al principio del archivo.

- `G` → Ir al final del archivo.

- `/`[patrón] → Buscar hacia adelante.

- `?`[patrón] → Buscar hacia atrás.

- `n` → Repetir búsqueda en la misma dirección.

- `N` → Repetir búsqueda en dirección opuesta.

- `q` → Salir de less.

**Ejemplos**

```fish
less archivo.txt                               # Abre el archivo para navegación
less -N /var/log/syslog                         # Abre con números de línea
less -S archivo_con_columnas.txt                 # No ajusta líneas largas
less -p "ERROR" app.log                          # Abre y busca "ERROR"
```
---

## 22. `grep` – Buscar Patrones en Archivos

El comando `grep` (global regular expression print) busca patrones de texto dentro de archivos y muestra las líneas que coinciden. Es una de las herramientas más poderosas para filtrar y buscar información.

**Uso básico**

```fish
grep [opciones] patrón [archivo]
```

**Opciones**

- `-i` → Ignora mayúsculas/minúsculas en la búsqueda.

- `-v` → Invierte la selección, muestra líneas que **no** coinciden.

- `-r`, `-R` → Busca recursivamente en directorios.

- `-n` → Muestra el número de línea junto con la línea coincidente.

- `-c` → Cuenta el número de líneas coincidentes en lugar de mostrarlas.

- `-l` → Muestra solo los nombres de archivos que contienen coincidencias.

- `-L` → Muestra solo los nombres de archivos que **no** contienen coincidencias.

- `-w` → Busca la palabra completa (no coincidencias parciales).

- `-x` → Busca líneas completas que coincidan exactamente.

- `-A` [N] → Muestra N líneas después de cada coincidencia.

- `-B` [N] → Muestra N líneas antes de cada coincidencia.

- `-C` [N] → Muestra N líneas antes y después (contexto).

- `-e` → Permite especificar múltiples patrones.

- `-f` → Lee patrones desde un archivo.

- `-E` → Usa expresiones regulares extendidas (egrep).

- `-P` → Usa expresiones regulares estilo Perl (si está disponible).

- `--color` → Colorea las coincidencias.

**Ejemplos**

```fish
grep "error" log.txt                            # Busca "error" en el archivo
grep -i "warning" sistema.log                   # Busca ignorando mayúsculas
grep -r "function" /home/usuario/codigo/        # Busca recursivamente en directorios
grep -n "TODO" *.py                             # Muestra número de línea en archivos Python
grep -c "ERROR" app.log                         # Cuenta cuántas veces aparece ERROR
grep -A 5 -B 5 "exception" trace.log            # Muestra 5 líneas antes y después
grep -e "error" -e "warning" log.txt            # Busca dos patrones diferentes
ps aux | grep firefox                           # Busca procesos relacionados con Firefox
```
---

## 23. `wc` – Contar Líneas, Palabras y Caracteres

El comando `wc` (word count) cuenta líneas, palabras y caracteres en archivos o en la entrada estándar. Es útil para obtener estadísticas rápidas de archivos de texto.

**Uso básico**

```fish
wc [opciones] [archivo]
```

**Opciones**

- `-l`, `--lines` → Muestra solo el número de líneas.

- `-w`, `--words` → Muestra solo el número de palabras.

- `-c`, `--bytes` → Muestra solo el número de bytes.

- `-m`, `--chars` → Muestra el número de caracteres.

- `-L`, `--max-line-length` → Muestra la longitud de la línea más larga.

- `--files0-from=F` → Lee nombres de archivos desde el archivo F, separados por null.

**Ejemplos**

```fish
wc archivo.txt                                  # Muestra líneas, palabras y bytes
wc -l archivo.txt                               # Solo número de líneas
wc -w *.txt                                     # Palabras en todos los archivos .txt
wc -L programa.c                                # Longitud de la línea más larga
cat archivo.txt | wc -l                         # Cuenta líneas usando pipe
grep "error" log.txt | wc -l                    # Cuenta cuántas líneas tienen "error"
```

---

## 24. `sort` – Ordenar Líneas de Texto

El comando `sort` ordena las líneas de archivos de texto según diferentes criterios, como alfabético, numérico o por campos específicos.

**Uso básico**

```fish
sort [opciones] [archivo]
```

**Opciones**

- `-n`, `--numeric-sort` → Ordena numéricamente en lugar de alfabéticamente.

- `-r`, `--reverse` → Invierte el orden (de mayor a menor).

- `-u`, `--unique` → Elimina líneas duplicadas (similar a sort | uniq).

- `-k`, `--key` → Ordena por un campo específico (ej: -k2 para segundo campo).

- `-t`, `--field-separator` → Especifica el separador de campos (por defecto espacio o tab).

- `-h`, `--human-numeric` → Ordena números con sufijos legibles (K, M, G).

- `-f`, `--ignore-case` → Ignora mayúsculas/minúsculas.

- `-b`, `--ignore-leading-blanks` → Ignora espacios al inicio.

- `-o`, `--output` → Escribe el resultado en un archivo en lugar de la salida estándar.

- `-c`, `--check` → Verifica si el archivo ya está ordenado.

- `-m`, `--merge` → Fusiona archivos ya ordenados sin ordenarlos nuevamente.

- `-V`, `--version-sort` → Ordena números de versión de forma natural (v1, v2, v10).

- `-R`, `--random-sort` → Ordena aleatoriamente.

**Ejemplos**

```fish
sort nombres.txt                                 # Ordena alfabéticamente
sort -n numeros.txt                              # Ordena numéricamente
sort -r -n numeros.txt                           # Ordena numéricamente descendente
sort -u lista.txt                                # Ordena y elimina duplicados
sort -t: -k3 /etc/passwd                         # Ordena por el tercer campo (UID) usando : como separador
sort -h archivos.txt                             # Ordena tamaños legibles (2K, 1M, 3G)
sort -k2 -n datos.txt                            # Ordena por segundo campo numérico
sort -V versiones.txt                            # Ordena versiones (1.0, 1.2, 1.10)
sort -R palabras.txt                             # Orden aleatorio
sort archivo.txt -o archivo_ordenado.txt         # Guarda resultado en archivo
```
---

## 25. `uniq` – Eliminar o Contar Líneas Duplicadas Consecutivas

El comando `uniq` (unique) filtra líneas duplicadas adyacentes en un archivo. Normalmente se usa después de `sort` para eliminar todas las repeticiones, ya que solo elimina duplicados consecutivos.

**Uso básico**

```fish
uniq [opciones] [archivo_entrada] [archivo_salida]
```

**Opciones**

- `-c`, `--count` → Cuenta el número de ocurrencias de cada línea.

- `-d`, `--repeated` → Muestra solo las líneas que están duplicadas.

- `-D`, `--all-repeated` → Muestra todas las líneas duplicadas (todas las copias).

- `-u`, `--unique` → Muestra solo las líneas que no están duplicadas.

- `-i`, `--ignore-case` → Ignora diferencias de mayúsculas/minúsculas.

- `-f`, `--skip-fields` → Omite los primeros N campos al comparar.

- `-s`, `--skip-chars` → Omite los primeros N caracteres al comparar.

- `-w`, `--check-chars` → Compara solo los primeros N caracteres.

**Ejemplos**

```fish
uniq archivo.txt                                # Elimina duplicados consecutivos
sort archivo.txt | uniq                          # Elimina todos los duplicados (combinado con sort)
sort archivo.txt | uniq -c                        # Muestra cada línea con su contador
sort archivo.txt | uniq -d                         # Muestra solo líneas duplicadas
sort archivo.txt | uniq -u                          # Muestra solo líneas únicas (no repetidas)
uniq -i archivo.txt                                 # Ignora mayúsculas al comparar
sort -n numeros.txt | uniq                           # Elimina duplicados numéricos
```
---

## 26. `cut` – Extraer Columnas de Texto

El comando `cut` extrae secciones específicas (columnas o campos) de cada línea de un archivo de texto, basándose en delimitadores o posiciones de caracteres.

**Uso básico**

```fish
cut [opciones] [archivo]
```

**Opciones**

- `-f`, `--fields` → Especifica los campos a extraer (ej: -f1, -f1-3, -f2,5).

- `-d`, `--delimiter` → Establece el delimitador de campo (por defecto es TAB).

- `-c`, `--characters` → Extrae caracteres por posición (ej: -c1-5, -c10-20).

- `-b`, `--bytes` → Extrae bytes por posición (similar a -c pero para bytes).

- `--complement` → Extrae todo **excepto** los campos especificados.

- `-s`, `--only-delimited` → No muestra líneas que no contienen delimitador.

- `--output-delimiter` → Especifica el delimitador para la salida.

**Ejemplos**

```fish
cut -f1,3 archivo.txt                                # Extrae campos 1 y 3 (delimitador TAB)
cut -d: -f1 /etc/passwd                              # Extrae nombres de usuario (primer campo con :)
cut -d, -f2-4 datos.csv                              # Extrae campos 2 a 4 de un CSV
cut -c1-10 archivo.txt                               # Extrae los primeros 10 caracteres de cada línea
cut -c5- archivo.txt                                 # Extrae desde el carácter 5 hasta el final
cut -d: -f1,6 --output-delimiter=" | " /etc/passwd   # Salida con delimitador personalizado
cut -f1 --complement archivo.txt                     # Extrae todos los campos excepto el primero
```
---

## 27. `tr` – Transformar o Reemplazar Caracteres

El comando `tr` (translate) traduce, elimina o comprime caracteres desde la entrada estándar. No trabaja directamente con archivos, solo con flujos de texto.

**Uso básico**

```fish
tr [opciones] conjunto1 [conjunto2]
```

**Opciones**

- `-d`, `--delete` → Elimina los caracteres especificados en conjunto1.

- `-s`, `--squeeze-repeats` → Comprime repeticiones consecutivas de caracteres.

- `-c`, `--complement` → Usa el complemento de conjunto1 (todo excepto esos caracteres).

- `-t`, `--truncate-set1` → Trunca conjunto1 al tamaño de conjunto2.

**Ejemplos**

```fish
echo "hola" | tr 'a-z' 'A-Z'                       # Convierte minúsculas a mayúsculas
cat archivo.txt | tr ':' '\t'                      # Cambia : por tabulador
tr -d ' ' < archivo.txt                            # Elimina todos los espacios
echo "texto   con   espacios" | tr -s ' '          # Comprime espacios múltiples a uno solo
tr -cd '[:alnum:]' < archivo.txt                   # Elimina todo excepto letras y números
tr '[:lower:]' '[:upper:]' < min.txt > may.txt     # Convierte archivo completo a mayúsculas
echo "abc123" | tr -d '0-9'                        # Elimina dígitos (resultado: abc)
```
---

## 28. `diff` – Comparar Archivos Línea por Línea

El comando `diff` (difference) compara dos archivos línea por línea y muestra las diferencias entre ellos. Es fundamental para ver cambios en archivos de configuración, código fuente, etc.

**Uso básico**

```fish
diff [opciones] archivo1 archivo2
```

**Opciones**

- `-u`, `-U` → Muestra diferencias en formato unificado (con contexto).

- `-c` → Muestra diferencias en formato de contexto.

- `-i` → Ignora diferencias de mayúsculas/minúsculas.

- `-w` → Ignora espacios en blanco.

- `-b` → Ignora cambios en la cantidad de espacios en blanco.

- `-B` → Ignora líneas en blanco.

- `-r` → Compara recursivamente directorios.

- `-q` → Solo indica si los archivos son diferentes, sin mostrar detalles.

- `-N` → Trata archivos ausentes como vacíos.

- `-y` → Muestra comparación lado a lado en dos columnas.

- `--suppress-common-lines` → Muestra solo las líneas diferentes.

**Ejemplos**

```fish
diff archivo1.txt archivo2.txt                   # Compara dos archivos
diff -u version1.py version2.py                   # Formato unificado (útil para parches)
diff -r dir1/ dir2/                                # Compara directorios recursivamente
diff -q archivo1.txt archivo2.txt                  # Solo indica si son diferentes
diff -y --width=100 archivo1.txt archivo2.txt      # Comparación lado a lado
diff -i -w config.conf config2.conf                 # Ignora mayúsculas y espacios
diff -u archivo1.txt archivo2.txt > cambios.patch   # Genera archivo de parche
```
---

## 29. `tee` – Guardar Salida y Mostrarla al Mismo Tiempo

El comando `tee` lee de la entrada estándar y escribe a la salida estándar y a uno o más archivos simultáneamente. Es como una "T" que divide el flujo de datos.

**Uso básico**

```fish
comando | tee [opciones] [archivo]
```

**Opciones**

- `-a`, `--append` → Añade al final del archivo en lugar de sobrescribirlo.

- `-i`, `--ignore-interrupts` → Ignora señales de interrupción.

- `-p` → Usa pipes de forma más segura con diagnósticos.

**Ejemplos**

```fish
ls -la | tee lista.txt                                  # Muestra resultado y lo guarda en archivo
echo "Hola mundo" | tee saludo.txt                      # Escribe y guarda
ps aux | tee procesos.txt | grep bash                   # Guarda todos los procesos y filtra bash
echo "Nueva línea" | tee -a archivo.txt                 # Añade al final sin borrar contenido
cat /var/log/syslog | tee log_completo.txt | tail -20   # Guarda todo, muestra solo últimas 20 líneas
```
---

## 30. `sed` – Editor de Flujo de Texto

El comando `sed` (stream editor) es un editor de texto no interactivo que realiza transformaciones en flujos de texto. Es extremadamente poderoso para búsqueda, reemplazo, inserción y eliminación de líneas.

**Uso básico**

```fish
sed [opciones] 'script' [archivo]
```

**Opciones**

- `-e` → Añade un script de edición.

- `-f` → Lee script desde un archivo.

- `-i[SUFIJO]` → Edita el archivo directamente (in-place), opcionalmente crea respaldo.

- `-n` → Suprime la salida automática (solo muestra lo que se pide con p).

- `-r` → Usa expresiones regulares extendidas (ERE).

- `-E` → Similar a -r, expresiones regulares extendidas.

- `-s` → Trata múltiples archivos como separados en lugar de continuos.

**Comandos comunes de sed**

- `s/patrón/reemplazo/` → Sustituye patrón por reemplazo (solo primera ocurrencia por línea).

- `s/patrón/reemplazo/g` → Sustituye globalmente (todas las ocurrencias).

- `s/patrón/reemplazo/2` → Sustituye solo la segunda ocurrencia.

- `d` → Elimina líneas.

- `p` → Imprime líneas (usado con -n).

- `i\texto` → Inserta texto antes de la línea.

- `a\texto` → Añade texto después de la línea.

- `c\texto` → Cambia la línea por texto.

- `y/conjunto1/conjunto2/` → Translitera caracteres (como tr).

- `N` → Añade la siguiente línea al espacio de patrón.

- `q` → Sale después de la primera coincidencia.

**Ejemplos**

```fish
sed 's/antiguo/nuevo/' archivo.txt                  # Reemplaza primera ocurrencia por línea
sed 's/antiguo/nuevo/g' archivo.txt                 # Reemplaza todas las ocurrencias
sed -i 's/error/ERROR/g' log.txt                    # Edita el archivo directamente
sed -i.bak 's/error/ERROR/g' log.txt                # Edita y crea respaldo .bak
sed '/^$/d' archivo.txt                             # Elimina líneas vacías
sed -n '/ERROR/p' app.log                           # Muestra solo líneas con ERROR
sed '5d' archivo.txt                                # Elimina la línea 5
sed '2,5d' archivo.txt                              # Elimina líneas 2 a 5
sed '1i\PRIMERA LÍNEA' archivo.txt                  # Inserta texto antes de línea 1
sed 's/  */ /g' archivo.txt                         # Reemplaza múltiples espacios por uno
sed 's/^[ \t]*//' archivo.txt                       # Elimina espacios al inicio de línea
```
---

## 31. `awk` – Procesamiento Avanzado de Texto

El comando `awk` es un lenguaje de programación completo diseñado para procesamiento de texto, especialmente útil para trabajar con datos estructurados en columnas. Permite realizar operaciones complejas con patrones y acciones.

**Uso básico**

```fish
awk [opciones] 'patrón {acción}' [archivo]
```

**Opciones**

- `-F` → Especifica el separador de campos (delimitador).

- `-v` → Define una variable antes de ejecutar el script.

- `-f` → Lee el script desde un archivo.

- `-W` → Activa opciones compatibles o extensiones.

**Variables internas de awk**

- `$0` → La línea completa actual.

- `$1`, `$2`, ... → Campos individuales (por defecto separados por espacio/tab).

- `NR` → Número de registro actual (número de línea).

- `NF` → Número de campos en la línea actual.

- `FS` → Separador de campos de entrada (Field Separator).

- `OFS` → Separador de campos de salida.

- `RS` → Separador de registros de entrada (por defecto nueva línea).

- `ORS` → Separador de registros de salida.

- `FILENAME` → Nombre del archivo actual.

**Ejemplos**

```fish
awk '{print $1}' archivo.txt                       # Imprime el primer campo de cada línea
awk -F: '{print $1}' /etc/passwd                    # Usa : como separador, imprime usuarios
awk '{print $1, $3}' datos.txt                       # Imprime campos 1 y 3
awk '$3 > 50 {print $1}' calificaciones.txt          # Si campo 3 > 50, imprime campo 1
awk '/error/ {print NR, $0}' log.txt                 # Muestra número de línea y línea con "error"
awk 'NR > 1 && NR < 10' archivo.txt                  # Muestra líneas 2 a 9
awk '{sum += $3} END {print "Total:", sum}' ventas.txt  # Suma campo 3 y muestra total
awk 'END {print NR}' archivo.txt                       # Cuenta líneas (como wc -l)
awk '{print $NF}' archivo.txt                           # Imprime el último campo de cada línea
awk 'length($0) > 80' programa.c                        # Muestra líneas con más de 80 caracteres
awk -F: '{print $1, $6}' /etc/passwd | sort            # Usuarios y su home
```
---

## 32. `echo` – Mostrar Texto en Pantalla

El comando `echo` muestra una línea de texto o el valor de variables en la salida estándar. Es uno de los comandos más simples y utilizados en scripts y en la terminal.

**Uso básico**

```fish
echo [opciones] [texto]
```

**Opciones**

- `-n` → No añade nueva línea al final.

- `-e` → Habilita la interpretación de secuencias de escape.

- `-E` → Deshabilita la interpretación de secuencias de escape (predeterminado en algunos sistemas).

**Secuencias de escape (con -e)**

- `\n` → Nueva línea.

- `\t` → Tabulador.

- `\\` → Barra invertida.

- `\a` → Alerta (beep).

- `\b` → Retroceso (backspace).

- `\r` → Retorno de carro.

- `\c` → Suprime la nueva línea final (similar a -n).

- `\e` → Carácter de escape (ASCII 27).

- `\033` → Código octal para escape (usado para colores).

**Ejemplos**

```fish
echo "Hola mundo"                                 # Muestra Hola mundo
echo -n "Sin nueva línea"                         # Sin salto de línea al final
echo -e "Primera línea\nSegunda línea"            # Interpreta \n como nueva línea
echo -e "Columna1\tColumna2\tColumna3"            # Tabulaciones
echo "Mi directorio home es: $HOME"                # Muestra valor de variable
echo -e "\033[31mTexto rojo\033[0m"                # Texto en color rojo
echo $((5+3))                                       # Evalúa expresión aritmética
```
---

## 33. `printf` – Formatear Texto en Pantalla

El comando `printf` formatea y muestra texto con un control más preciso que `echo`, similar al printf de C. Permite especificar el formato exacto de la salida.

**Uso básico**

```fish
printf FORMATO [argumentos]
```

**Especificadores de formato comunes**

- `%s` → Cadena de texto.

- `%d` → Número entero decimal.

- `%f` → Número de punto flotante.

- `%x` → Hexadecimal.

- `%o` → Octal.

- `%c` → Carácter.

- `%b` → Cadena con interpretación de escapes.

- `%e` → Notación científica.

- `%g` → Formato automático (%e o %f, el más corto).

- `%%` → Signo de porcentaje literal.

- `%Ns` → Cadena con ancho mínimo N (justificada a la derecha).

- `%-Ns` → Cadena justificada a la izquierda.

- `%0Nd` → Número con ceros a la izquierda.

- `%.Nf` → Número con N decimales.

**Secuencias de escape**

- `\n` → Nueva línea.

- `\t` → Tabulador.

- `\\` → Barra invertida.

- `\"` → Comillas dobles.

**Ejemplos**

```fish
printf "Hola %s\n" "Mundo"                         # Hola Mundo
printf "Nombre: %s, Edad: %d\n" "Juan" 25           # Nombre: Juan, Edad: 25
printf "%10s %10s\n" "Nombre" "Edad"                # Formato de tabla
printf "%.2f\n" 3.14159                              # 3.14
printf "%08d\n" 42                                    # 00000042
printf "|%-10s|%10s|\n" "Izquierda" "Derecha"        # Columnas alineadas
printf "%b\n" "Texto con \n nueva línea"              # Interpreta escapes
printf "%x\n" 255                                      # ff (hexadecimal)
printf "%o\n" 255                                      # 377 (octal)
```
---

## 34. `zcat` – Mostrar Contenido de Archivos Comprimidos .gz

El comando `zcat` muestra el contenido de archivos comprimidos con gzip (`.gz`) sin necesidad de descomprimirlos primero. Es equivalente a `gunzip -c`.

**Uso básico**

```fish
zcat [opciones] [archivo.gz]
```

**Opciones**

- `-f`, `--force` → Fuerza la descompresión incluso si el archivo no tiene extensión .gz.

- `-c` → Escribe en la salida estándar (por defecto).

- `-l` → Lista información del archivo comprimido.

- `-t` → Prueba la integridad del archivo.

- `-q` → Suprime advertencias.

**Ejemplos**

```fish
zcat archivo.txt.gz                               # Muestra el contenido del archivo comprimido
zcat log.gz | head -20                             # Muestra primeras 20 líneas de un log comprimido
zcat -l archivo.gz                                  # Muestra información del archivo comprimido
zcat *.gz | grep "error"                            # Busca "error" en todos los .gz
zcat archivo.gz | wc -l                              # Cuenta líneas sin descomprimir
```
---

## 35. `zless` – Ver Archivos Comprimidos .gz Paginados

El comando `zless` permite visualizar archivos comprimidos con gzip de forma interactiva, igual que `less` pero para archivos .gz. Descomprime sobre la marcha.

**Uso básico**

```fish
zless [opciones] [archivo.gz]
```

**Opciones**

- Acepta las mismas opciones que `less`.

**Comandos de navegación (igual que less)**

- `Espacio` → Avanzar página.

- `b` → Retroceder página.

- `g` → Ir al principio.

- `G` → Ir al final.

- `/`[patrón] → Buscar hacia adelante.

- `?`[patrón] → Buscar hacia atrás.

- `n` → Repetir búsqueda.

- `q` → Salir.

**Ejemplos**

```fish
zless archivo.txt.gz                              # Abre archivo comprimido para navegación
zless /var/log/syslog.gz                           # Visualiza logs comprimidos
zless -N archivo.gz                                 # Muestra con números de línea
```
---

## 36. `rev` – Voltear Líneas de Texto

El comando `rev` invierte el orden de los caracteres en cada línea de texto, escribiendo cada línea al revés.

**Uso básico**

```fish
rev [opciones] [archivo]
```

**Opciones**

- `-V`, `--version` → Muestra información de versión.

- `-h`, `--help` → Muestra ayuda.

**Ejemplos**

```fish
echo "hola" | rev                                 # aloh
rev archivo.txt                                    # Invierte todas las líneas del archivo
cat datos.txt | rev | cut -c1-5 | rev               # Obtiene últimos 5 caracteres de cada línea
echo "12345" | rev                                   # 54321
```
---

## 37. `column` – Formatear Texto en Columnas

El comando `column` formatea la entrada en múltiples columnas, creando tablas alineadas automáticamente. Es excelente para presentar datos de forma legible.

**Uso básico**

```fish
column [opciones] [archivo]
```

**Opciones**

- `-t`, `--table` → Crea una tabla basada en delimitadores.

- `-s`, `--separator` → Especifica el delimitador (por defecto espacio/tab).

- `-c`, `--columns` → Establece el ancho de la salida en columnas.

- `-x`, `--fillrows` → Llena filas antes que columnas.

- `-o`, `--output-separator` → Especifica separador para la salida.

- `-R`, `--table-right` → Alinea a la derecha las columnas especificadas.

- `-N`, `--table-columns` → Nombra las columnas.

- `-J`, `--json` → Salida en formato JSON.

**Ejemplos**

```fish
column -t archivo.txt                              # Formatea como tabla automática
cat /etc/passwd | column -t -s:                     # Tabla del passwd con separador :
column -t -s, -o " | " datos.csv                     # Cambia separador de , a | 
column -c 80 archivo.txt                             # Formatea en columnas de 80 caracteres
ps aux | column -t                                    # Formatea salida de ps como tabla
echo -e "a 1\nb 2\nc 3" | column -t                   # Crea tabla simple
```
---

## 38. `comm` – Comparar Archivos Ordenados Línea por Línea

El comando `comm` compara dos archivos **ordenados** línea por línea y produce tres columnas: líneas exclusivas del primer archivo, exclusivas del segundo y comunes a ambos.

**Uso básico**

```fish
comm [opciones] archivo1 archivo2
```

**Opciones**

- `-1` → Suprime la columna 1 (líneas solo en archivo1).

- `-2` → Suprime la columna 2 (líneas solo en archivo2).

- `-3` → Suprime la columna 3 (líneas comunes).

- `-i` → Ignora diferencias de mayúsculas/minúsculas.

- `--check-order` → Verifica que los archivos estén ordenados.

- `--nocheck-order` → No verifica orden (por defecto).

- `--output-delimiter` → Especifica separador entre columnas.

**Ejemplos**

```fish
comm archivo1.txt archivo2.txt                    # Muestra tres columnas
comm -12 archivo1.txt archivo2.txt                 # Muestra solo líneas comunes
comm -23 archivo1.txt archivo2.txt                  # Muestra solo líneas en archivo1
comm -13 archivo1.txt archivo2.txt                   # Muestra solo líneas en archivo2
comm -i lista1.txt lista2.txt                         # Ignora mayúsculas
comm --output-delimiter="|" a.txt b.txt               # Usa | como separador
```
---

### Gestión de Usuarios y Permisos

La seguridad en Linux se basa fundamentalmente en la gestión de usuarios, grupos y permisos. Estos comandos permiten administrar quién puede acceder al sistema, qué recursos pueden utilizar y con qué privilegios. Desde la creación de usuarios hasta el control detallado de permisos en archivos, esta categoría es esencial para cualquier administrador de sistemas.

---

## 39. `sudo` – Ejecutar Comandos como Superusuario

El comando `sudo` (superuser do) permite ejecutar comandos con los privilegios de otro usuario, normalmente el superusuario (root), siempre que el usuario tenga los permisos adecuados configurados en `/etc/sudoers`.

**Uso básico**

```fish
sudo [opciones] comando
```

**Opciones**

- `-u` [usuario] → Ejecuta el comando como el usuario especificado (por defecto root).

- `-i` → Inicia una sesión de shell como el usuario destino (similar a su).

- `-s` → Ejecuta un shell con los privilegios del usuario destino.

- `-l` → Lista los privilegios del usuario actual (qué comandos puede ejecutar).

- `-k` → Invalida la caché de contraseñas, fuerza a pedir contraseña en el próximo sudo.

- `-v` → Actualiza la caché de contraseñas sin ejecutar un comando.

- `-b` → Ejecuta el comando en segundo plano.

- `-E` → Preserva las variables de entorno del usuario.

- `-H` → Establece HOME al directorio del usuario destino.

**Ejemplos**

```fish
sudo apt update                                   # Actualiza repositorios (Debian/Ubuntu)
sudo -u www-data touch /var/www/index.html        # Ejecuta como usuario www-data
sudo -i                                            # Inicia sesión como root
sudo -l                                             # Muestra comandos que puedes ejecutar
sudo -u postgres psql                               # Ejecuta psql como usuario postgres
sudo -E comando                                      # Ejecuta preservando entorno
```
---

## 40. `su` – Cambiar de Usuario Temporalmente

El comando `su` (switch user) permite cambiar a otro usuario en la sesión actual. Sin argumentos, cambia al usuario root y solicita su contraseña.

**Uso básico**

```fish
su [opciones] [usuario]
```

**Opciones**

- `-`, `-l`, `--login` → Inicia una sesión de login completa (carga el entorno del usuario).

- `-c` → Ejecuta un comando como el usuario y vuelve.

- `-s` → Especifica un shell diferente al predeterminado.

- `-m`, `-p` → Preserva el entorno actual (no carga el del usuario destino).

- `--session-command` → Ejecuta un comando sin crear una nueva sesión.

**Ejemplos**

```fish
su                                             # Cambia a root (pide contraseña root)
su -                                           # Cambia a root con entorno completo
su - usuario                                    # Cambia a usuario con su entorno
su -c "systemctl restart apache2"               # Ejecuta comando como root y vuelve
su -l juan -c "whoami"                           # Muestra "juan" ejecutando whoami
```
---

## 41. `chmod` – Cambiar Permisos de Archivos o Directorios

El comando `chmod` (change mode) modifica los permisos de lectura (r), escritura (w) y ejecución (x) para archivos y directorios, tanto en modo octal como simbólico.

**Uso básico**

```fish
chmod [opciones] permisos archivo
```

**Modo simbólico**

- `u` → Usuario (propietario).
- `g` → Grupo.
- `o` → Otros.
- `a` → Todos (user+group+others).
- `+` → Añade permisos.
- `-` → Quita permisos.
- `=` → Asigna exactamente esos permisos.
- `r` → Lectura.
- `w` → Escritura.
- `x` → Ejecución.
- `X` → Ejecución solo si es directorio o ya tiene ejecución algún usuario.
- `s` → Setuid/Setgid (bit SUID/SGID).
- `t` → Sticky bit.

**Modo octal**

- `0` → Ningún permiso (---).
- `1` → Solo ejecución (--x).
- `2` → Solo escritura (-w-).
- `3` → Escritura y ejecución (-wx).
- `4` → Solo lectura (r--).
- `5` → Lectura y ejecución (r-x).
- `6` → Lectura y escritura (rw-).
- `7` → Todos los permisos (rwx).

Estructura octal: `chmod UGO archivo` (U=usuario, G=grupo, O=otros)

**Opciones**

- `-R`, `--recursive` → Cambia permisos recursivamente en directorios.

- `-v`, `--verbose` → Muestra información detallada de cada cambio.

- `-c`, `--changes` → Muestra solo cuando se realiza un cambio.

- `-f`, `--silent` → Suprime la mayoría de mensajes de error.

- `--reference` → Usa los permisos de un archivo de referencia.

**Ejemplos**

```fish
chmod 755 script.sh                              # rwxr-xr-x (dueño todo, grupo/otros leer/ejecutar)
chmod 644 archivo.txt                             # rw-r--r-- (dueño leer/escribir, otros solo leer)
chmod 700 carpeta_privada                          # drwx------ (solo dueño)
chmod u+x script.sh                                 # Añade ejecución al dueño
chmod go-w archivo.txt                               # Quita escritura a grupo y otros
chmod a+x script.sh                                   # Todos pueden ejecutar
chmod -R 755 directorio/                               # Cambia recursivamente todo un directorio
chmod u=rwx,g=rx,o=r archivo                           # Simbólico: rwxr-xr--
chmod --reference=modelo.txt destino.txt               # Copia permisos de modelo a destino
```

---

## 42. `chown` – Cambiar Propietario de Archivos o Directorios

El comando `chown` (change owner) cambia el usuario propietario y opcionalmente el grupo de archivos o directorios. Solo root puede cambiar el propietario.

**Uso básico**

```fish
chown [opciones] [usuario][:grupo] archivo
```

**Opciones**

- `-R`, `--recursive` → Cambia propietario recursivamente en directorios.

- `-v`, `--verbose` → Muestra información detallada de cada cambio.

- `-c`, `--changes` → Muestra solo cuando se realiza un cambio.

- `-f`, `--silent` → Suprime la mayoría de mensajes de error.

- `--reference` → Usa el propietario de un archivo de referencia.

- `-h` → Cambia el propietario del enlace simbólico, no del archivo apuntado.

- `--dereference` → Cambia el propietario del archivo apuntado (por defecto).

**Formatos**

- `usuario` → Cambia solo el usuario.

- `usuario:grupo` → Cambia usuario y grupo.

- `:grupo` → Cambia solo el grupo.

- `usuario:` → Cambia usuario y grupo al grupo principal del usuario.

**Ejemplos**

```fish
chown juan archivo.txt                            # Cambia propietario a juan
chown juan:desarrolladores archivo.txt             # Cambia a juan y grupo desarrolladores
chown :www-data /var/www/index.html                 # Cambia solo grupo a www-data
chown -R juan:juan /home/juan/                       # Cambia todo el home recursivamente
chown --reference=modelo.txt destino.txt             # Usa propietario de modelo.txt
chown -h juan enlace_simbolico                        # Cambia propietario del enlace, no del destino
```
---

## 43. `chgrp` – Cambiar Grupo de Archivos o Directorios

El comando `chgrp` (change group) cambia el grupo propietario de archivos o directorios. Es una alternativa específica a `chown :grupo`.

**Uso básico**

```fish
chgrp [opciones] grupo archivo
```

**Opciones**

- `-R`, `--recursive` → Cambia grupo recursivamente en directorios.

- `-v`, `--verbose` → Muestra información detallada de cada cambio.

- `-c`, `--changes` → Muestra solo cuando se realiza un cambio.

- `-f`, `--silent` → Suprime la mayoría de mensajes de error.

- `--reference` → Usa el grupo de un archivo de referencia.

- `-h` → Cambia el grupo del enlace simbólico, no del archivo apuntado.

- `--dereference` → Cambia el grupo del archivo apuntado (por defecto).

**Ejemplos**

```fish
chgrp desarrolladores archivo.txt                  # Cambia grupo a desarrolladores
chgrp -R www-data /var/www/                          # Cambia grupo recursivamente
chgrp --reference=modelo.txt destino.txt             # Usa el grupo de modelo.txt
chgrp -h usuarios enlace                               # Cambia grupo del enlace simbólico
```
---

## 44. `umask` – Consultar o Establecer Permisos Predeterminados

El comando `umask` (user mask) establece la máscara de permisos que determina los permisos por defecto para los nuevos archivos y directorios. Los permisos finales se calculan como: permisos base (666 para archivos, 777 para directorios) menos la máscara.

**Uso básico**

```fish
umask [opciones] [máscara]
```

**Opciones**

- `-S` → Muestra la máscara en formato simbólico en lugar de octal.

- `-p` → Muestra la máscara en formato que puede ser reutilizado como entrada.

**Valores comunes de umask**

- `022` → Archivos: 644 (rw-r--r--), Directorios: 755 (rwxr-xr-x). Es el más común.

- `002` → Archivos: 664 (rw-rw-r--), Directorios: 775 (rwxrwxr-x). Para trabajo en grupo.

- `077` → Archivos: 600 (rw-------), Directorios: 700 (rwx------). Máxima privacidad.

- `000` → Archivos: 666 (rw-rw-rw-), Directorios: 777 (rwxrwxrwx). Sin restricciones (inseguro).

**Ejemplos**

```fish
umask                                           # Muestra máscara actual (ej: 022)
umask -S                                        # Muestra en formato simbólico (u=rwx,g=rx,o=rx)
umask 077                                       # Cambia máscara a 077 (máxima privacidad)
umask 002                                       # Cambia a máscara para trabajo colaborativo
(umask 077; touch archivo_secreto)               # Cambia temporalmente para un comando
```
---

## 45. `useradd` – Crear un Nuevo Usuario

El comando `useradd` crea una nueva cuenta de usuario en el sistema. Es la herramienta de bajo nivel para añadir usuarios (en algunas distribuciones se usa `adduser` que es más amigable).

**Uso básico**

```fish
useradd [opciones] nombre_usuario
```

**Opciones**

- `-c`, `--comment` → Añade un comentario (normalmente el nombre completo).

- `-d`, `--home` → Especifica el directorio home (por defecto /home/usuario).

- `-m`, `--create-home` → Crea el directorio home si no existe.

- `-M` → No crea el directorio home.

- `-s`, `--shell` → Especifica el shell del usuario (ej: /bin/bash).

- `-u`, `--uid` → Especifica el UID (User ID) manualmente.

- `-g`, `--gid` → Especifica el grupo principal (por ID o nombre).

- `-G`, `--groups` → Añade el usuario a grupos adicionales (separados por comas).

- `-e`, `--expiredate` → Fecha de expiración de la cuenta (YYYY-MM-DD).

- `-f`, `--inactive` → Días de inactividad antes de deshabilitar la cuenta.

- `-r`, `--system` → Crea una cuenta de sistema (sin home, UID bajo).

- `-p`, `--password` → Establece contraseña encriptada (inseguro, mejor usar passwd después).

- `-k`, `--skel` → Directorio esqueleto para copiar archivos al home (por defecto /etc/skel).

**Ejemplos**

```fish
useradd juan                                      # Crea usuario juan (puede no crear home)
useradd -m -s /bin/bash pedro                      # Crea con home y shell bash
useradd -m -c "María García" -G desarrolladores maria  # Con comentario y grupo adicional
useradd -u 1500 -g usuarios -G sudo,www-data ana   # UID específico y grupos
useradd -e 2026-12-31 temporal                      # Usuario con fecha de expiración
useradd -r servicio                                  # Cuenta de sistema (sin login)
```
---

## 46. `usermod` – Modificar un Usuario Existente

El comando `usermod` modifica las propiedades de una cuenta de usuario existente en el sistema.

**Uso básico**

```fish
usermod [opciones] nombre_usuario
```

**Opciones**

- `-c`, `--comment` → Cambia el comentario (nombre completo).

- `-d`, `--home` → Cambia el directorio home (no mueve archivos).

- `-m`, `--move-home` → Mueve el contenido del home a la nueva ubicación (usar con -d).

- `-l`, `--login` → Cambia el nombre de usuario.

- `-s`, `--shell` → Cambia el shell del usuario.

- `-u`, `--uid` → Cambia el UID.

- `-g`, `--gid` → Cambia el grupo principal.

- `-G`, `--groups` → Reemplaza la lista de grupos secundarios.

- `-a`, `--append` → Añade a grupos sin eliminar los existentes (usar con -G).

- `-L`, `--lock` → Bloquea la cuenta (pone ! en la contraseña).

- `-U`, `--unlock` → Desbloquea la cuenta.

- `-e`, `--expiredate` → Cambia fecha de expiración.

- `-f`, `--inactive` → Cambia días de inactividad.

**Ejemplos**

```fish
usermod -s /bin/zsh juan                          # Cambia shell a zsh
usermod -l pedro juan                              # Cambia nombre de juan a pedro
usermod -a -G docker,sudo maria                     # Añade a grupos docker y sudo
usermod -d /nuevo/home -m usuario                    # Cambia home y mueve archivos
usermod -L usuario                                    # Bloquea la cuenta
usermod -U usuario                                    # Desbloquea la cuenta
usermod -e 2026-01-01 temporal                        # Establece fecha de expiración
```
---

## 47. `userdel` – Eliminar un Usuario

El comando `userdel` elimina una cuenta de usuario del sistema.

**Uso básico**

```fish
userdel [opciones] nombre_usuario
```

**Opciones**

- `-r`, `--remove` → Elimina también el directorio home y el correo del usuario.

- `-f`, `--force` → Fuerza la eliminación incluso si el usuario está conectado.

- `-Z` → Elimina contextos SELinux del usuario.

**Ejemplos**

```fish
userdel juan                                      # Elimina el usuario juan
userdel -r pedro                                   # Elimina usuario y su home
userdel -f maria                                    # Fuerza eliminación aunque esté conectada
```
---

## 48. `groupadd` – Crear un Nuevo Grupo

El comando `groupadd` crea un nuevo grupo en el sistema.

**Uso básico**

```fish
groupadd [opciones] nombre_grupo
```

**Opciones**

- `-g`, `--gid` → Especifica el GID manualmente.

- `-r`, `--system` → Crea un grupo de sistema (GID bajo).

- `-f`, `--force` → Si el grupo existe, sale con éxito (no da error).

- `-o`, `--non-unique` → Permite GID no único (repetido).

- `-p`, `--password` → Establece contraseña (inseguro, no recomendado).

**Ejemplos**

```fish
groupadd desarrolladores                           # Crea grupo desarrolladores
groupadd -g 2000 proyectox                          # Crea con GID específico
groupadd -r sysgroup                                 # Crea grupo de sistema
groupadd -f backend                                   # No da error si ya existe
```
---

## 49. `groupmod` – Modificar un Grupo

El comando `groupmod` modifica las propiedades de un grupo existente.

**Uso básico**

```fish
groupmod [opciones] nombre_grupo
```

**Opciones**

- `-n`, `--new-name` → Cambia el nombre del grupo.

- `-g`, `--gid` → Cambia el GID.

- `-o`, `--non-unique` → Permite GID no único.

- `-p`, `--password` → Cambia la contraseña (no recomendado).

**Ejemplos**

```fish
groupmod -n programadores desarrolladores           # Cambia nombre a programadores
groupmod -g 2500 proyectox                           # Cambia GID a 2500
```
---

## 50. `groupdel` – Eliminar un Grupo

El comando `groupdel` elimina un grupo del sistema. No se puede eliminar un grupo que sea el grupo principal de algún usuario.

**Uso básico**

```fish
groupdel nombre_grupo
```

**Opciones**

- No tiene opciones significativas.

**Ejemplos**

```fish
groupdel desarrolladores                           # Elimina el grupo desarrolladores
groupdel proyectox                                  # Elimina el grupo proyectox
```
---

## 51. `passwd` – Cambiar Contraseña de Usuario

El comando `passwd` cambia la contraseña de un usuario. Los usuarios normales solo pueden cambiar su propia contraseña, root puede cambiar la de cualquier usuario.

**Uso básico**

```fish
passwd [opciones] [usuario]
```

**Opciones**

- `-S`, `--status` → Muestra el estado de la contraseña (bloqueada, fecha de cambio, etc.).

- `-l`, `--lock` → Bloquea la cuenta (deshabilita la contraseña).

- `-u`, `--unlock` → Desbloquea la cuenta.

- `-d`, `--delete` → Elimina la contraseña (cuenta sin contraseña).

- `-e`, `--expire` → Fuerza al usuario a cambiar la contraseña en el próximo login.

- `-x`, `--maxdays` → Días máximos que una contraseña es válida.

- `-n`, `--mindays` → Días mínimos entre cambios.

- `-w`, `--warndays` → Días de aviso antes de que expire.

- `-i`, `--inactive` → Días después de expirar para deshabilitar.

**Ejemplos**

```fish
passwd                                          # Cambia tu propia contraseña
passwd juan                                      # Root cambia contraseña de juan
passwd -S usuario                                 # Muestra estado de la contraseña
passwd -l usuario                                  # Bloquea la cuenta
passwd -u usuario                                   # Desbloquea la cuenta
passwd -e usuario                                    # Fuerza cambio en próximo login
passwd -x 90 -w 7 usuario                             # Expira en 90 días, avisa 7 antes
```
---

## 52. `whoami` – Mostrar Usuario Actual

El comando `whoami` muestra el nombre del usuario actualmente en uso. Es una forma rápida de saber con qué identidad estás trabajando.

**Uso básico**

```fish
whoami [opciones]
```

**Opciones**

- `--help` → Muestra ayuda.

- `--version` → Muestra información de versión.

**Ejemplos**

```fish
whoami                                          # Muestra tu nombre de usuario
sudo whoami                                      # Muestra "root"
```
---

## 53. `id` – Información de Usuario y Grupos

El comando `id` muestra información detallada sobre el usuario actual o un usuario específico: UID, GID y grupos a los que pertenece.

**Uso básico**

```fish
id [opciones] [usuario]
```

**Opciones**

- `-u`, `--user` → Muestra solo el UID.

- `-g`, `--group` → Muestra solo el GID del grupo principal.

- `-G`, `--groups` → Muestra todos los GIDs de los grupos a los que pertenece.

- `-n`, `--name` → Muestra nombres en lugar de números (usar con -u, -g, -G).

- `-r`, `--real` → Muestra el ID real en lugar del efectivo (usar con -u, -g, -G).

- `-Z`, `--context` → Muestra el contexto de seguridad SELinux.

**Ejemplos**

```fish
id                                              # Muestra toda la información
id juan                                          # Información del usuario juan
id -u                                             # Muestra solo tu UID
id -gn                                             # Muestra nombre del grupo principal
id -G                                              # Muestra todos los GIDs de grupos
id -nG                                             # Muestra nombres de todos los grupos
```
---

## 54. `groups` – Mostrar Grupos a los que Pertenece un Usuario

El comando `groups` muestra los grupos a los que pertenece un usuario específico o el usuario actual.

**Uso básico**

```fish
groups [opciones] [usuario]
```

**Opciones**

- No tiene opciones significativas en la mayoría de versiones.

**Ejemplos**

```fish
groups                                          # Muestra tus grupos
groups juan                                      # Muestra grupos del usuario juan
```
---

## 55. `w` – Usuarios Conectados y su Actividad

El comando `w` muestra información detallada sobre los usuarios actualmente conectados al sistema, incluyendo qué están ejecutando y la carga del sistema.

**Uso básico**

```fish
w [opciones] [usuario]
```

**Opciones**

- `-h`, `--no-header` → No muestra el encabezado.

- `-u`, `--no-current` → Ignora el nombre de usuario al mostrar procesos.

- `-s`, `--short` → Formato corto (sin tiempo de login, JCPU, PCPU).

- `-f`, `--from` → Muestra o no el campo "desde" (dónde se conectaron).

- `-o`, `--old-style` → Formato antiguo.

- `-i`, `--ip-addr` → Muestra direcciones IP en lugar de nombres.

**Ejemplos**

```fish
w                                               # Muestra todos los usuarios conectados
w juan                                           # Muestra solo información de juan
w -s                                              # Formato corto
w -h                                               # Sin encabezado
```
---

## 56. `who` – Usuarios Conectados al Sistema

El comando `who` muestra una lista simple de los usuarios que han iniciado sesión en el sistema.

**Uso básico**

```fish
who [opciones]
```

**Opciones**

- `-a`, `--all` → Muestra toda la información disponible.

- `-b`, `--boot` → Muestra la hora del último arranque del sistema.

- `-d`, `--dead` → Muestra procesos muertos.

- `-H`, `--heading` → Muestra encabezados de columna.

- `-l`, `--login` → Muestra procesos de login.

- `-p`, `--process` → Muestra procesos activos.

- `-q`, `--count` → Muestra solo nombres y cuenta de usuarios.

- `-r`, `--runlevel` → Muestra el runlevel actual.

- `-t`, `--time` → Muestra la última modificación del reloj del sistema.

- `-u`, `--users` → Muestra usuarios conectados (por defecto).

**Ejemplos**

```fish
who                                             # Muestra usuarios conectados
who -H                                           # Con encabezados
who -b                                            # Muestra hora del último arranque
who -q                                             # Solo nombres y contador
who -r                                              # Muestra runlevel actual
```
---

## 57. `last` – Historial de Logins

El comando `last` muestra un historial de los últimos inicios de sesión en el sistema, leyendo el archivo `/var/log/wtmp`.

**Uso básico**

```fish
last [opciones] [usuario] [tty]
```

**Opciones**

- `-n`, `-` → Número de líneas a mostrar (ej: last -10).

- `-x`, `--system` → Muestra también apagados y cambios de runlevel.

- `-a`, `--hostlast` → Muestra el host en la última columna.

- `-d`, `--dns` → Resuelve nombres de host.

- `-F`, `--fulltimes` → Muestra fechas completas.

- `-i`, `--ip` → Muestra IPs en lugar de nombres.

- `-R`, `--nohostname` → No muestra nombres de host.

- `-w`, `--fullnames` → Muestra nombres de usuario completos.

- `-t`, `--until` → Muestra logins hasta una fecha específica.

**Ejemplos**

```fish
last                                            # Muestra todo el historial
last -10                                         # Últimos 10 logins
last juan                                         # Historial del usuario juan
last -x                                            # Incluye apagados y reinicios
last -i                                             # Muestra IPs en lugar de nombres
last reboot                                         # Muestra solo reinicios
last -t 202601011200                                 # Logins hasta esa fecha
```
---

## 58. `finger` – Información Detallada de Usuarios

El comando `finger` muestra información detallada sobre los usuarios del sistema, incluyendo nombre completo, directorio home, shell, y si están conectados. En muchos sistemas modernos no viene instalado por defecto por razones de privacidad.

**Uso básico**

```fish
finger [opciones] [usuario]
```

**Opciones**

- `-l` → Formato largo (más detallado).

- `-s` → Formato corto (por defecto).

- `-m` → Evita hacer coincidencia con nombre real.

- `-p` → No muestra el contenido de .plan y .project.

**Ejemplos**

```fish
finger                                          # Muestra todos los usuarios conectados
finger juan                                      # Información detallada de juan
finger -l juan                                    # Formato largo
finger -s                                           # Formato corto
```
---

### Procesos, Memoria y Monitoreo

Linux es un sistema multiusuario y multitarea, lo que significa que múltiples procesos pueden ejecutarse simultáneamente. Los comandos de esta categoría permiten visualizar, controlar y monitorear los procesos del sistema, así como el uso de memoria y recursos. Son esenciales para diagnosticar problemas de rendimiento y administrar la carga del sistema.

---

## 59. `top` – Monitor en Tiempo Real de Procesos

El comando `top` muestra una vista dinámica y en tiempo real de los procesos del sistema, ordenados por uso de CPU o memoria. Es la herramienta estándar para monitorear el rendimiento del sistema.

**Uso básico**

```fish
top [opciones]
```

**Opciones**

- `-d`, `--delay` → Intervalo de actualización en segundos (ej: top -d 5).

- `-n`, `--iterations` → Número de actualizaciones antes de salir.

- `-p`, `--pid` → Monitorea solo PIDs específicos (ej: top -p 1234,5678).

- `-u`, `--user` → Muestra solo procesos de un usuario.

- `-b`, `--batch` → Modo batch (para scripts, sin interactividad).

- `-c` → Muestra la línea de comandos completa en lugar del nombre.

- `-H` → Muestra hilos individuales (threads).

- `-i` → Ignora procesos inactivos.

**Comandos interactivos dentro de top**

- `1` → Alterna vista de CPU individual/múltiple.

- `P` → Ordena por uso de CPU.

- `M` → Ordena por uso de memoria.

- `T` → Ordena por tiempo de CPU acumulado.

- `k` → Mata un proceso (pide PID y señal).

- `r` → Renice (cambia prioridad) un proceso.

- `u` → Filtra por usuario.

- `q` → Salir.

- `h` → Ayuda.

- `c` → Alterna nombre/comando completo.

- `V` → Vista en árbol (jerarquía de procesos).

**Ejemplos**

```fish
top                                             # Inicia top con actualización cada 3 segundos
top -d 5                                         # Actualiza cada 5 segundos
top -u juan                                       # Muestra solo procesos de juan
top -p 1234 -p 5678                                # Monitorea PIDs específicos
top -b -n 1 > procesos.txt                          # Una captura en modo batch a archivo
```
---

## 60. `htop` – Monitor Avanzado de Procesos

El comando `htop` es una versión mejorada e interactiva de `top`, con colores, navegación con teclas de flecha, y opciones más amigables. No viene instalado por defecto en todos los sistemas.

**Uso básico**

```fish
htop [opciones]
```

**Opciones**

- `-d`, `--delay` → Intervalo de actualización en décimas de segundo.

- `-C`, `--no-color` → Modo monocromático.

- `-u`, `--user` → Muestra solo procesos de un usuario.

- `-p`, `--pid` → Monitorea solo PIDs específicos.

- `-s`, `--sort` → Ordena por una columna específica.

- `-t`, `--tree` → Vista en árbol por defecto.

**Comandos interactivos dentro de htop**

- Flechas → Navegar entre procesos.

- `F1` → Ayuda.

- `F2` → Configuración.

- `F3` → Buscar.

- `F4` → Filtrar.

- `F5` → Vista en árbol.

- `F6` → Ordenar por columna.

- `F9` → Matar proceso.

- `F10` → Salir.

- `Espacio` → Marcar proceso.

- `u` → Mostrar solo procesos de un usuario.

- `k` → Mostrar hilos.

- `H` → Mostrar/ocultar hilos de usuario.

- `K` → Mostrar/ocultar hilos del kernel.

**Ejemplos**

```fish
htop                                            # Inicia htop
htop -u juan                                      # Solo procesos de juan
htop -d 20                                         # Actualiza cada 2 segundos (20 décimas)
```
---

## 61. `ps` – Ver Procesos Activos

El comando `ps` (process status) muestra información sobre los procesos en ejecución. Es una herramienta fundamental para inspeccionar el estado del sistema.

**Uso básico**

```fish
ps [opciones]
```

**Opciones comunes**

- `ps aux` → Muestra todos los procesos con formato detallado (BSD).

- `ps -ef` → Muestra todos los procesos en formato estándar (Unix).

- `-e` → Todos los procesos.

- `-f` → Formato completo.

- `-u` [usuario] → Procesos de un usuario específico.

- `-p` [PID] → Procesos con PID específico.

- `-C` [comando] → Procesos con nombre de comando específico.

- `--sort` → Ordena la salida (ej: --sort=-%cpu).

- `-L` → Muestra hilos (threads).

- `-H` → Muestra jerarquía de procesos.

- `-o` → Formato personalizado de columnas.

**Columnas comunes en ps**

- `PID` → ID del proceso.

- `PPID` → ID del proceso padre.

- `%CPU` → Porcentaje de CPU usado.

- `%MEM` → Porcentaje de memoria usado.

- `VSZ` → Tamaño virtual en KB.

- `RSS` → Memoria residente en KB.

- `TTY` → Terminal asociada.

- `STAT` → Estado del proceso.

- `START` → Hora de inicio.

- `TIME` → Tiempo total de CPU usado.

- `COMMAND` → Comando ejecutado.

**Ejemplos**

```fish
ps aux                                          # Todos los procesos (formato BSD)
ps -ef                                           # Todos los procesos (formato Unix)
ps -u juan                                        # Procesos del usuario juan
ps -C firefox                                      # Procesos con nombre firefox
ps -p 1234                                          # Información del PID 1234
ps aux --sort=-%cpu | head -10                       # Top 10 procesos por CPU
ps aux --sort=-%mem | head -10                        # Top 10 procesos por memoria
ps -eo pid,ppid,cmd,%cpu,%mem --sort=-%cpu            # Columnas personalizadas
ps -efH                                               # Vista en árbol de procesos
```
---

## 62. `pstree` – Mostrar Procesos en Forma de Árbol

El comando `pstree` muestra los procesos en ejecución en forma de árbol jerárquico, facilitando la visualización de las relaciones padre-hijo entre procesos.

**Uso básico**

```fish
pstree [opciones] [pid|usuario]
```

**Opciones**

- `-p` → Muestra también los PIDs.

- `-u` → Muestra cambios de usuario.

- `-a` → Muestra argumentos de línea de comandos.

- `-h` → Resalta el proceso actual.

- `-l` → Líneas largas (no truncar).

- `-n` → Ordena por PID.

- `-s` → Muestra ancestros del proceso especificado.

- `-t` → Muestra hilos como procesos hijos.

- `-U` → Usa caracteres Unicode para el árbol.

- `-G` → Usa caracteres VT100 para el árbol.

**Ejemplos**

```fish
pstree                                          # Árbol completo de procesos
pstree -p                                        # Con PIDs
pstree -u                                         # Con cambios de usuario
pstree -a                                          # Con argumentos de línea
pstree 1234                                        # Árbol a partir del PID 1234
pstree juan                                         # Árbol de procesos del usuario juan
pstree -s 1234                                       # Ancestros del PID 1234
```
---

## 63. `kill` – Terminar Procesos por PID

El comando `kill` envía señales a procesos, generalmente para terminarlos. Por defecto envía la señal TERM (15), que solicita al proceso que termine de forma ordenada.

**Uso básico**

```fish
kill [señal] PID
```

**Señales comunes**

- `TERM` (15) → Terminación ordenada (por defecto).

- `KILL` (9) → Forzar terminación (el proceso no puede ignorarla).

- `HUP` (1) → Reiniciar/recargar configuración.

- `STOP` (19) → Pausar el proceso.

- `CONT` (18) → Continuar un proceso pausado.

- `INT` (2) → Interrupción (como Ctrl+C).

- `QUIT` (3) → Terminar y generar core dump.

- `USR1` (10) → Señal definida por el usuario 1.

- `USR2` (12) → Señal definida por el usuario 2.

**Opciones**

- `-l`, `--list` → Lista todos los nombres de señales.

- `-L` → Lista señales en formato tabla.

- `-s`, `--signal` → Especifica la señal por nombre.

**Ejemplos**

```fish
kill 1234                                        # Termina proceso 1234 (señal TERM)
kill -9 1234                                      # Fuerza terminación (KILL)
kill -HUP 1234                                     # Reinicia/recarga proceso
kill -STOP 1234                                     # Pausa el proceso
kill -CONT 1234                                      # Continúa proceso pausado
kill -l                                              # Lista todas las señales
kill -s KILL 1234                                     # Usa nombre de señal
```
---

## 64. `pkill` – Terminar Procesos por Nombre

El comando `pkill` envía señales a procesos basándose en su nombre u otros atributos, sin necesidad de conocer el PID.

**Uso básico**

```fish
pkill [opciones] [patrón]
```

**Opciones**

- `-f` → Busca en la línea de comandos completa.

- `-u` [usuario] → Mata solo procesos de un usuario.

- `-g` [grupo] → Mata solo procesos de un grupo.

- `-P` [ppid] → Mata solo hijos de un proceso padre.

- `-t` [terminal] → Mata procesos en una terminal.

- `-x` → Coincidencia exacta (nombre completo).

- `-i` → Ignora mayúsculas/minúsculas.

- `-n` → Mata el proceso más reciente.

- `-o` → Mata el proceso más antiguo.

- `-signal` → Especifica la señal (ej: -9, -TERM).

**Ejemplos**

```fish
pkill firefox                                    # Mata procesos llamados firefox
pkill -9 python                                   # Fuerza terminación de python
pkill -f "script.py"                               # Mata por línea de comandos completa
pkill -u juan -9                                    # Mata todos los procesos de juan
pkill -t pts/2                                       # Mata procesos en terminal pts/2
pkill -HUP nginx                                      # Recarga nginx
pkill -n chrome                                        # Mata el chrome más reciente
```
---

## 65. `killall` – Terminar Todos los Procesos con un Nombre

El comando `killall` mata todos los procesos que tengan un nombre específico. A diferencia de `pkill`, `killall` requiere el nombre exacto del proceso (sin patrón).

**Uso básico**

```fish
killall [opciones] nombre_proceso
```

**Opciones**

- `-e`, `--exact` → Requiere coincidencia exacta (por defecto).

- `-I`, `--ignore-case` → Ignora mayúsculas/minúsculas.

- `-g`, `--process-group` → Mata el grupo de procesos.

- `-i`, `--interactive` → Pregunta antes de matar.

- `-q`, `--quiet` → No muestra mensajes de error.

- `-v`, `--verbose` → Muestra información detallada.

- `-w`, `--wait` → Espera a que los procesos terminen.

- `-u` [usuario] → Mata solo procesos de un usuario.

- `-signal` → Especifica la señal (ej: -9, -TERM).

**Ejemplos**

```fish
killall firefox                                   # Mata todos los firefox
killall -9 chrome                                  # Fuerza terminación de chrome
killall -i apache2                                  # Pregunta antes de matar
killall -v -TERM nginx                               # Detallado con señal TERM
killall -u juan -9                                    # Mata todos los procesos de juan
killall -w firefox                                     # Espera a que terminen
```
---

## 66. `nice` – Ejecutar Procesos con Prioridad Modificada

El comando `nice` ejecuta un programa con una prioridad de planificación (niceness) modificada. El valor "nice" va de -20 (máxima prioridad) a 19 (mínima prioridad). Por defecto, los procesos se ejecutan con nice 0.

**Uso básico**

```fish
nice [opciones] [comando]
```

**Opciones**

- `-n`,

---

Continúo desde el comando **66. `nice`** exactamente donde lo dejamos:

---

## 66. `nice` – Ejecutar Procesos con Prioridad Modificada

El comando `nice` ejecuta un programa con una prioridad de planificación (niceness) modificada. El valor "nice" va de -20 (máxima prioridad) a 19 (mínima prioridad). Por defecto, los procesos se ejecutan con nice 0.

**Uso básico**

```fish
nice [opciones] [comando]
```

**Opciones**

- `-n`, `--adjustment` → Especifica el valor de nice (por defecto 10).

- `-`[valor] → Formato antiguo: nice -5 comando (sin -n).

**Ejemplos**

```fish
nice -n 10 ./script.sh                           # Ejecuta script con prioridad baja (nice 10)
nice -n -5 ./proceso_urgente                      # Ejecuta con prioridad alta (nice -5, requiere root)
nice -19 tareas_pesadas                           # Prioridad muy baja (nice 19)
nice ./comando                                     # Ejecuta con nice 10 (valor por defecto)
sudo nice -n -20 ./critico                          # Máxima prioridad (nice -20, requiere root)
```
---

## 67. `renice` – Cambiar Prioridad de Procesos en Ejecución

El comando `renice` modifica la prioridad (niceness) de procesos que ya están en ejecución. Los valores van de -20 (máxima prioridad) a 19 (mínima prioridad).

**Uso básico**

```fish
renice [opciones] valor -p PID
```

**Opciones**

- `-p`, `--pid` → Cambia prioridad de PIDs (por defecto).

- `-g`, `--pgrp` → Cambia prioridad de grupos de procesos.

- `-u`, `--user` → Cambia prioridad de todos los procesos de un usuario.

- `-n`, `--priority` → Especifica el valor de nice (opcional en algunos sistemas).

**Ejemplos**

```fish
renice 10 -p 1234                                # Cambia PID 1234 a nice 10
renice -5 -p 1234                                 # Cambia a prioridad más alta (nice -5, requiere root)
renice 15 -g 5678                                  # Cambia grupo de procesos
renice 19 -u juan                                   # Todos los procesos de juan a nice 19
renice 5 -p 1234 5678 9012                           # Múltiples PIDs
```
---

## 68. `nohup` – Ejecutar un Comando Ignorando la Salida de Cierre

El comando `nohup` (no hang up) ejecuta un comando de manera que ignore las señales de "colgar" (HUP), permitiendo que el proceso continúe ejecutándose incluso después de cerrar la sesión de terminal.

**Uso básico**

```fish
nohup [comando] [argumentos]
```

**Opciones**

- `--help` → Muestra ayuda.

- `--version` → Muestra información de versión.

**Características**

- La salida se redirige automáticamente a `nohup.out` en el directorio actual.

- Si no se puede escribir en `nohup.out`, usa `$HOME/nohup.out`.

- El proceso hereda el nice 0 por defecto.

**Ejemplos**

```fish
nohup ./script.sh &                               # Ejecuta script en segundo plano ignorando HUP
nohup tar -czf backup.tar.gz /home/ &              # Backup grande que no se interrumpa
nohup python servidor.py > salida.log 2>&1 &       # Redirige salida personalizada
nohup wget http://archivo_grande.iso &              # Descarga que continúa tras cerrar sesión
```
---

## 69. `bg` – Poner un Proceso en Segundo Plano

El comando `bg` reanuda un trabajo suspendido y lo pone a ejecutarse en segundo plano. Se usa junto con el control de trabajos de la shell.

**Uso básico**

```fish
bg [%id_trabajo]
```

**Ejemplos**

```fish
bg                                              # Pone el trabajo actual suspendido en segundo plano
bg %1                                            # Pone el trabajo 1 en segundo plano
bg %2                                             # Pone el trabajo 2 en segundo plano
```
---

## 70. `fg` – Traer un Proceso a Primer Plano

El comando `fg` trae un trabajo que se está ejecutando en segundo plano al primer plano, permitiendo interactuar con él directamente.

**Uso básico**

```fish
fg [%id_trabajo]
```

**Ejemplos**

```fish
fg                                              # Trae el trabajo actual al primer plano
fg %1                                            # Trae el trabajo 1 al primer plano
fg %2                                             # Trae el trabajo 2 al primer plano
```
---

## 71. `jobs` – Listar Trabajos en Segundo Plano

El comando `jobs` lista los trabajos que están ejecutándose en segundo plano o suspendidos en la sesión actual de la shell.

**Uso básico**

```fish
jobs [opciones]
```

**Opciones**

- `-l` → Muestra también los PIDs de los trabajos.

- `-p` → Muestra solo los PIDs.

- `-s` → Muestra solo trabajos detenidos (suspendidos).

- `-r` → Muestra solo trabajos en ejecución.

- `-n` → Muestra solo trabajos que han cambiado de estado.

**Ejemplos**

```fish
jobs                                            # Lista todos los trabajos
jobs -l                                          # Con PIDs
jobs -r                                           # Solo trabajos en ejecución
jobs -s                                            # Solo trabajos suspendidos
```
---

## 72. `free` – Información de Memoria

El comando `free` muestra la cantidad de memoria RAM libre y usada, así como la memoria de intercambio (swap) en el sistema.

**Uso básico**

```fish
free [opciones]
```

**Opciones**

- `-h`, `--human` → Muestra tamaños en formato legible (KiB, MiB, GiB).

- `-b`, `--bytes` → Muestra en bytes.

- `-k`, `--kibi` → Muestra en KiB (por defecto).

- `-m`, `--mebi` → Muestra en MiB.

- `-g`, `--gibi` → Muestra en GiB.

- `-t`, `--total` → Muestra una línea con el total.

- `-s`, `--seconds` → Actualiza cada N segundos (modo monitor).

- `-c`, `--count` → Número de actualizaciones en modo monitor.

- `-w`, `--wide` → Muestra formato ancho con columnas separadas.

**Ejemplos**

```fish
free                                            # Muestra memoria en KiB
free -h                                          # Formato legible (MiB/GiB)
free -m                                           # En MiB
free -h -t                                         # Con total y legible
free -s 5 -c 3                                      # Actualiza cada 5 segundos, 3 veces
watch -n 2 free -h                                   # Monitor continuo con watch
```
---

## 73. `vmstat` – Estadísticas de Memoria y CPU

El comando `vmstat` (virtual memory statistics) reporta información sobre procesos, memoria, paginación, bloques de E/S, interrupciones y actividad de CPU.

**Uso básico**

```fish
vmstat [opciones] [intervalo] [contador]
```

**Opciones**

- `-a`, `--active` → Muestra memoria activa e inactiva.

- `-f`, `--forks` → Muestra número de forks desde el arranque.

- `-m`, `--slabs` → Muestra información de slabs (caché del kernel).

- `-n`, `--one-header` → Muestra encabezado solo una vez (no repetir).

- `-s`, `--stats` → Muestra tabla de estadísticas.

- `-d`, `--disk` → Estadísticas de disco.

- `-D`, `--disk-sum` → Resumen de estadísticas de disco.

- `-p`, `--partition` → Estadísticas de partición específica.

- `-S`, `--unit` → Unidad de medida (k, K, m, M).

- `-t`, `--timestamp` → Añade marca de tiempo.

**Columnas de vmstat**

- `procs`: r (ejecutando), b (bloqueados).

- `memory`: swpd (swap usado), free (libre), buff (buffer), cache (caché).

- `swap`: si (swap in), so (swap out).

- `io`: bi (bloques recibidos), bo (bloques enviados).

- `system`: in (interrupciones), cs (cambios de contexto).

- `cpu`: us (usuario), sy (sistema), id (idle), wa (wait), st (steal).

**Ejemplos**

```fish
vmstat                                          # Estadísticas desde el arranque
vmstat 2                                         # Actualiza cada 2 segundos
vmstat 5 10                                       # Cada 5 segundos, 10 veces
vmstat -a                                          # Con memoria activa/inactiva
vmstat -s                                           # Tabla de estadísticas
vmstat -d                                            # Estadísticas de disco
vmstat -t 2                                          # Con timestamp
```
---

## 74. `iostat` – Estadísticas de I/O de Discos

El comando `iostat` (input/output statistics) monitoriza la actividad de entrada/salida de los dispositivos de almacenamiento, mostrando información sobre el rendimiento de discos.

**Uso básico**

```fish
iostat [opciones] [intervalo] [contador]
```

**Opciones**

- `-c`, `--cpu` → Muestra solo estadísticas de CPU.

- `-d`, `--disk` → Muestra solo estadísticas de disco.

- `-h`, `--human` → Tamaños legibles.

- `-k`, `--kilobytes` → Muestra en kilobytes.

- `-m`, `--megabytes` → Muestra en megabytes.

- `-t`, `--timestamp` → Añade marca de tiempo.

- `-x`, `--extended` → Estadísticas extendidas (más detalladas).

- `-p`, `--partitions` → Muestra estadísticas por partición.

- `-y`, `--omit-first` → Omite el primer informe (sin datos desde arranque).

- `-z`, `--omit-zero` → Omite dispositivos sin actividad.

**Ejemplos**

```fish
iostat                                          # Estadísticas básicas
iostat 2                                         # Actualiza cada 2 segundos
iostat -x 5                                       # Estadísticas extendidas cada 5 segundos
iostat -d 2                                        # Solo discos
iostat -p sda                                       # Particiones de sda
iostat -x -k 2 10                                     # Extendido en KB, 10 veces
```
---

## 75. `lsof` – Archivos Abiertos por Procesos

El comando `lsof` (list open files) lista todos los archivos abiertos por los procesos en ejecución. En Unix, "todo es un archivo", por lo que incluye archivos regulares, directorios, sockets, tuberías, etc.

**Uso básico**

```fish
lsof [opciones]
```

**Opciones**

- `-p` [PID] → Archivos abiertos por un proceso específico.

- `-u` [usuario] → Archivos abiertos por un usuario.

- `-c` [comando] → Archivos abiertos por procesos con ese comando.

- `-d` [FD] → Archivos con descriptor específico.

- `-i` [protocolo] → Conexiones de red (TCP, UDP, puertos).

- `-t` → Solo muestra PIDs (modo terse, para scripts).

- `+D` [directorio] → Archivos abiertos en un directorio recursivamente.

- `-a` → AND lógico entre condiciones (por defecto es OR).

- `-n` → No resuelve nombres de host.

- `-P` → No resuelve nombres de puerto.

**Ejemplos**

```fish
lsof                                            # Todos los archivos abiertos
lsof -p 1234                                      # Archivos abiertos por PID 1234
lsof -u juan                                       # Archivos abiertos por juan
lsof -i :80                                         # Procesos usando el puerto 80
lsof -i TCP:22                                       # Conexiones TCP en puerto 22
lsof -c firefox                                       # Archivos abiertos por firefox
lsof +D /home                                         # Archivos abiertos en /home
lsof -u juan -a -i                                    # Conexiones de red de juan (AND)
lsof -t -i :8080                                      # Solo PIDs usando puerto 8080
```
---

## 76. `strace` – Rastrear Llamadas al Sistema

El comando `strace` rastrea las llamadas al sistema y señales recibidas por un proceso. Es una herramienta de depuración fundamental para entender qué hace un programa a nivel de sistema.

**Uso básico**

```fish
strace [opciones] comando
strace -p PID
```

**Opciones**

- `-p` [PID] → Se adjunta a un proceso en ejecución.

- `-e` [expresión] → Filtra llamadas específicas (ej: -e open,read).

- `-o` [archivo] → Guarda salida en archivo.

- `-c` → Cuenta tiempo, llamadas y errores por syscall.

- `-t` → Añade timestamp a cada línea.

- `-tt` → Timestamp con microsegundos.

- `-T` → Muestra tiempo empleado en cada syscall.

- `-f` → Sigue procesos hijos (fork, vfork, clone).

- `-ff` → Sigue hijos y separa salida por PID con -o.

- `-v` → Modo verboso (no abrevia estructuras).

- `-s` [tamaño] → Máximo longitud de strings a mostrar.

- `-y` → Muestra rutas asociadas a descriptores de archivo.

**Ejemplos**

```fish
strace ls                                        # Rastrea el comando ls
strace -p 1234                                    # Se adjunta al PID 1234
strace -e open,read cat archivo.txt                # Solo syscalls open y read
strace -o salida.txt comando                        # Guarda en archivo
strace -c firefox                                    # Cuenta estadísticas de syscalls
strace -f -o salida comando                           # Sigue hijos, salida separada
strace -t -e write ls -la                              # Timestamp en syscalls write
```
---

## 77. `uptime` – Tiempo de Actividad del Sistema

El comando `uptime` muestra cuánto tiempo lleva el sistema funcionando desde el último arranque, el número de usuarios conectados y las cargas medias del sistema.

**Uso básico**

```fish
uptime [opciones]
```

**Opciones**

- `-p`, `--pretty` → Muestra tiempo de actividad en formato legible.

- `-h`, `--help` → Muestra ayuda.

- `-s`, `--since` → Muestra la hora exacta desde que el sistema está activo.

- `-V`, `--version` → Muestra información de versión.

**Ejemplos**

```fish
uptime                                          # Hora actual, uptime, usuarios, carga
uptime -p                                        # "up 2 hours, 15 minutes"
uptime -s                                         # "2026-03-14 09:23:45"
```
---

## 78. `watch` – Ejecutar un Comando Repetidamente

El comando `watch` ejecuta un comando periódicamente (por defecto cada 2 segundos) y muestra su salida en pantalla, permitiendo monitorizar cambios en tiempo real.

**Uso básico**

```fish
watch [opciones] comando
```

**Opciones**

- `-n`, `--interval` → Intervalo en segundos entre ejecuciones.

- `-d`, `--differences` → Resalta las diferencias entre ejecuciones.

- `-t`, `--no-title` → No muestra el título (encabezado).

- `-b`, `--beep` → Emite un pitido si el comando sale con error.

- `-e`, `--errexit` → Se detiene si el comando sale con error.

- `-g`, `--chgexit` → Se detiene cuando la salida cambia.

- `-c`, `--color` → Interpreta secuencias de color en la salida.

- `-x` → Pasa el comando a la shell con exec (más seguro).

**Ejemplos**

```fish
watch -n 1 date                                  # Muestra fecha cada segundo
watch -d free -h                                  # Monitoriza memoria resaltando cambios
watch -n 5 'ps aux | grep python'                  # Procesos Python cada 5 segundos
watch -t ls -l                                      # Lista archivos sin título
watch -g 'wc -l archivo.txt'                         # Espera hasta que cambie el número de líneas
watch -c 'echo -e "\033[31mRojo\033[0m"'             # Muestra colores
```
---

### Almacenamiento, Discos y Hardware

Linux proporciona un conjunto completo de herramientas para administrar el almacenamiento, desde la visualización del espacio disponible hasta el particionado de discos y la obtención de información detallada del hardware. Estos comandos son esenciales para mantener la integridad de los datos y optimizar el uso de los recursos de almacenamiento.

---

## 79. `df` – Espacio Disponible en Discos

El comando `df` (disk free) muestra el espacio libre y usado en los sistemas de archivos montados. Es la herramienta principal para verificar la disponibilidad de espacio en disco.

**Uso básico**

```fish
df [opciones] [archivo|directorio]
```

**Opciones**

- `-h`, `--human-readable` → Muestra tamaños en formato legible (KB, MB, GB).

- `-H` → Similar a -h pero usa potencias de 1000 (SI) en lugar de 1024.

- `-T`, `--print-type` → Muestra el tipo de sistema de archivos.

- `-t`, `--type` → Limita a sistemas de archivos de un tipo específico.

- `-x`, `--exclude-type` → Excluye sistemas de archivos de un tipo.

- `-a`, `--all` → Incluye sistemas de archivos con 0 bloques.

- `-i`, `--inodes` → Muestra información de inodos en lugar de bloques.

- `-l`, `--local` → Limita a sistemas de archivos locales.

- `-P`, `--portability` → Formato POSIX (una línea por sistema).

- `--total` → Añade una línea con el total.

- `-B`, `--block-size` → Define el tamaño de bloque.

**Ejemplos**

```fish
df -h                                           # Todos los discos en formato legible
df -hT                                           # Con tipo de sistema de archivos
df -i                                             # Información de inodos
df -h /home                                        # Solo el disco que contiene /home
df -t ext4                                         # Solo sistemas ext4
df -x tmpfs                                         # Excluye sistemas tmpfs
df --total -h                                        # Añade línea total
```
---

## 80. `du` – Tamaño de Archivos y Directorios

El comando `du` (disk usage) estima el espacio en disco utilizado por archivos y directorios. Es útil para encontrar qué está ocupando más espacio.

**Uso básico**

```fish
du [opciones] [archivo|directorio]
```

**Opciones**

- `-h`, `--human-readable` → Tamaños en formato legible.

- `-s`, `--summarize` → Muestra solo el total de cada argumento.

- `-a`, `--all` → Muestra también archivos, no solo directorios.

- `-c`, `--total` → Muestra un total al final.

- `-d`, `--max-depth` → Profundidad máxima en directorios.

- `--exclude` → Excluye archivos que coincidan con patrón.

- `--max-size` → No muestra archivos mayores que N.

- `--min-size` → No muestra archivos menores que N.

- `-L`, `--dereference` → Sigue enlaces simbólicos.

- `-l`, `--count-links` → Cuenta enlaces duros múltiples veces.

- `-k` → Muestra en kilobytes.

- `-m` → Muestra en megabytes.

- `-B`, `--block-size` → Define el tamaño de bloque.

- `-t`, `--threshold` → Muestra solo si supera cierto tamaño.

- `-x`, `--one-file-system` → No sale del sistema de archivos actual.

**Ejemplos**

```fish
du -sh                                          # Total del directorio actual
du -sh *                                         # Tamaño de cada elemento visible
du -h --max-depth=1                               # Un nivel de profundidad
du -sh /home/* | sort -rh                          # Directorios home ordenados por tamaño
du -a -h | grep '\.txt$'                            # Tamaño de archivos .txt
du -c -h                                            # Con total al final
du -x /                                              # Solo el sistema de archivos raíz
du -t 100M                                           # Solo archivos/dirs mayores a 100MB
```
---

## 81. `mount` – Montar Sistemas de Archivos

El comando `mount` monta sistemas de archivos (dispositivos) en un directorio específico del árbol de directorios. También se usa sin argumentos para ver los sistemas montados actualmente.

**Uso básico**

```fish
mount [opciones] [dispositivo] [punto_montaje]
```

**Opciones**

- `-a`, `--all` → Monta todos los sistemas de archivos en /etc/fstab.

- `-t`, `--types` → Especifica el tipo de sistema de archivos (ext4, ntfs, vfat, etc.).

- `-o`, `--options` → Opciones de montaje (rw, ro, noexec, etc.).

- `-r`, `--read-only` → Monta en modo solo lectura (equivalente a -o ro).

- `-w`, `--rw` → Monta en modo lectura-escritura (por defecto).

- `-v`, `--verbose` → Modo detallado.

- `-B`, `--bind` → Vuelve a montar un directorio en otro lugar (bind mount).

- `-L`, `--label` → Monta por etiqueta del sistema de archivos.

- `-U`, `--uuid` → Monta por UUID.

- `--move` → Mueve un punto de montaje a otro.

**Opciones comunes de -o**

- `rw` → Lectura-escritura.

- `ro` → Solo lectura.

- `noexec` → No permite ejecutar binarios.

- `nosuid` → Ignora bits suid/sgid.

- `nodev` → No interpreta dispositivos especiales.

- `noatime` → No actualiza tiempos de acceso (mejora rendimiento).

- `remount` → Vuelve a montar con nuevas opciones.

- `loop` → Monta archivo como dispositivo loop.

- `uid`, `gid` → Propietario para sistemas FAT/NTFS.

- `umask` → Máscara de permisos para FAT/NTFS.

**Ejemplos**

```fish
mount                                           # Muestra todos los sistemas montados
mount /dev/sdb1 /mnt/datos                       # Monta partición en /mnt/datos
mount -t ntfs /dev/sdc1 /mnt/windows              # Monta NTFS con tipo específico
mount -o ro /dev/sr0 /mnt/cdrom                    # Monta CD-ROM solo lectura
mount -o remount,rw /                               # Vuelve a montar raíz como lectura-escritura
mount -o loop imagen.iso /mnt/iso                   # Monta archivo ISO
mount -B /home /mnt/home_backup                      # Bind mount de /home
mount -L DATOS /mnt/datos                             # Monta por etiqueta
mount -U 1234-5678 /mnt/usb                            # Monta por UUID
```
---

## 82. `umount` – Desmontar Sistemas de Archivos

El comando `umount` desmonta sistemas de archivos que estaban montados previamente.

**Uso básico**

```fish
umount [opciones] [dispositivo|punto_montaje]
```

**Opciones**

- `-a`, `--all` → Desmonta todos los sistemas de archivos en /etc/mtab.

- `-f`, `--force` → Fuerza desmontaje (si el sistema está ocupado).

- `-l`, `--lazy` → Desmontaje diferido (cuando deje de estar ocupado).

- `-R`, `--recursive` → Desmonta todo el árbol de montaje.

- `-r`, `--read-only` → Si falla el desmontaje, intenta montar como solo lectura.

- `-t`, `--types` → Limita a sistemas de archivos de un tipo.

- `-v`, `--verbose` → Modo detallado.

- `-n`, `--no-mtab` → No actualiza /etc/mtab.

- `-O`, `--test-opts` → Desmonta solo si tiene ciertas opciones.

**Ejemplos**

```fish
umount /mnt/datos                                # Desmonta por punto de montaje
umount /dev/sdb1                                  # Desmonta por dispositivo
umount -f /mnt/ocupado                             # Fuerza desmontaje si está ocupado
umount -l /mnt/lento                                # Desmontaje diferido (lazy)
umount -a                                            # Desmonta todos (excepto sistemas críticos)
```
---

## 83. `fdisk` – Particionar Discos

El comando `fdisk` es una herramienta interactiva para crear y manipular tablas de particiones en discos. Trabaja con MBR (msdos) y GPT.

**Uso básico**

```fish
fdisk [opciones] [dispositivo]
```

**Opciones**

- `-l`, `--list` → Lista las particiones de todos los discos o de uno específico.

- `-u`, `--units` → Usa sectores como unidad (en lugar de cilindros).

- `-s` [partición] → Muestra el tamaño de una partición.

- `-t`, `--type` → Especifica el tipo de tabla de particiones.

- `-v`, `--version` → Muestra versión.

**Comandos interactivos de fdisk**

- `m` → Muestra ayuda.

- `p` → Muestra tabla de particiones actual.

- `n` → Crea nueva partición.

- `d` → Elimina partición.

- `t` → Cambia tipo de partición.

- `w` → Escribe cambios y sale.

- `q` → Sale sin guardar.

- `l` → Lista tipos de partición conocidos.

- `a` → Alterna flag de booteable.

- `g` → Crea nueva tabla GPT.

- `o` → Crea nueva tabla DOS (MBR).

**Ejemplos**

```fish
fdisk -l                                        # Lista todos los discos y particiones
fdisk -l /dev/sda                                 # Lista particiones de /dev/sda
fdisk /dev/sdb                                     # Interactivo para /dev/sdb
fdisk -s /dev/sda1                                  # Tamaño de la partición sda1
```
---

## 84. `lsblk` – Mostrar Dispositivos de Bloques

El comando `lsblk` (list block devices) muestra información sobre todos los dispositivos de bloque disponibles (discos, particiones, LVM, etc.) en un formato de árbol.

**Uso básico**

```fish
lsblk [opciones]
```

**Opciones**

- `-a`, `--all` → Muestra también dispositivos vacíos.

- `-f`, `--fs` → Muestra información del sistema de archivos.

- `-l`, `--list` → Formato de lista (no árbol).

- `-t`, `--topology` → Muestra información de topología.

- `-m`, `--perms` → Muestra propietario, grupo y permisos.

- `-o`, `--output` → Especifica columnas a mostrar.

- `-p`, `--paths` → Muestra rutas completas de dispositivos.

- `-r`, `--raw` → Salida en formato raw.

- `-d`, `--nodeps` → No muestra dispositivos hijos (solo discos).

- `-n`, `--noheadings` → No muestra encabezados.

- `-J`, `--json` → Salida en formato JSON.

**Ejemplos**

```fish
lsblk                                           # Árbol de dispositivos
lsblk -f                                         # Con sistema de archivos
lsblk -l                                          # Formato de lista
lsblk -o NAME,SIZE,TYPE,MOUNTPOINT                  # Columnas personalizadas
lsblk -m                                             # Con permisos y propietario
lsblk -d                                              # Solo discos (sin particiones)
lsblk -J                                              # Salida JSON
```
---

## 85. `blkid` – Mostrar UUID de Particiones

El comando `blkid` (block ID) muestra los atributos de dispositivos de bloque, como el UUID, el tipo de sistema de archivos y la etiqueta.

**Uso básico**

```fish
blkid [opciones] [dispositivo]
```

**Opciones**

- `-o`, `--output` → Formato de salida (full, value, list, device, udev).

- `-s`, `--match-tag` → Muestra solo una etiqueta específica (ej: UUID).

- `-t`, `--token` → Busca dispositivos que coincidan con token (ej: UUID=...).

- `-p`, `--probe` → Escanea el dispositivo (no usa caché).

- `-c`, `--cache-file` → Usa archivo de caché específico.

- `-L`, `--label` → Busca dispositivo por etiqueta.

- `-U`, `--uuid` → Busca dispositivo por UUID.

**Ejemplos**

```fish
blkid                                           # Muestra todos los dispositivos
blkid /dev/sda1                                   # Solo /dev/sda1
blkid -o value -s UUID /dev/sda1                   # Solo el valor del UUID
blkid -t UUID="1234-5678"                           # Busca dispositivo por UUID
blkid -L DATOS                                       # Busca por etiqueta
blkid -p /dev/sdb1                                    # Escaneo directo (sin caché)
```
---

## 86. `fsck` – Revisar y Reparar Sistemas de Archivos

El comando `fsck` (file system check) verifica y repara sistemas de archivos. Es la herramienta para mantener la integridad de los datos.

**Uso básico**

```fish
fsck [opciones] [dispositivo]
```

**Opciones**

- `-A`, `--all` → Verifica todos los sistemas en /etc/fstab.

- `-C`, `--progress` → Muestra barra de progreso.

- `-N`, `--no-execute` → Muestra lo que haría pero no ejecuta.

- `-R`, `--root-skip` → Omite el sistema de archivos raíz (con -A).

- `-T`, `--ignore-time` → Ignora información de timestamp.

- `-t`, `--type` → Especifica tipo de sistema de archivos.

- `-y` → Responde "sí" automáticamente a todas las preguntas.

- `-n` → Responde "no" automáticamente (modo solo lectura).

- `-p` → Repara automáticamente problemas menores.

- `-V`, `--verbose` → Modo detallado.

**Ejemplos**

```fish
fsck /dev/sda1                                    #S Verifica /dev/sda1
fsck -y /dev/sdb1                                  # Repara automáticamente
fsck -f /dev/sda1                                   # Fuerza verificación aunque parezca limpio
fsck -A                                              # Verifica todos en fstab
fsck -C -V /dev/sda1                                  # Con progreso y detallado
fsck -t ext4 /dev/sda1                                 # Especifica tipo ext4
```
---

## 87. `mkfs` – Formatear Sistemas de Archivos

El comando `mkfs` (make file system) crea un sistema de archivos en un dispositivo, es decir, lo formatea. Normalmente se usa con un prefijo del tipo de sistema de archivos.

**Uso básico**

```fish
mkfs [opciones] [-t tipo] dispositivo
```

**Variantes comunes**

- `mkfs.ext2`, `mkfs.ext3`, `mkfs.ext4` → Sistemas de archivos Linux.

- `mkfs.xfs` → Sistema de archivos XFS.

- `mkfs.btrfs` → Sistema de archivos Btrfs.

- `mkfs.vfat`, `mkfs.fat` → FAT32 (compatible con Windows).

- `mkfs.ntfs` → NTFS (Windows).

- `mkfs.exfat` → exFAT (archivos grandes).

**Opciones comunes**

- `-t`, `--type` → Especifica tipo de sistema de archivos.

- `-L`, `--label` → Añade una etiqueta al sistema de archivos.

- `-q`, `--quiet` → Modo silencioso.

- `-V`, `--verbose` → Modo detallado.

- `-c`, `--check` → Comprueba bloques defectuosos antes de formatear.

- `-F`, `--force` → Fuerza formateo (incluso si parece montado).

**Ejemplos**

```fish
mkfs.ext4 /dev/sdb1                               # Formatea como ext4
mkfs -t ext4 /dev/sdb1                             # Mismo efecto
mkfs.ext4 -L DATOS /dev/sdb1                        # Con etiqueta
mkfs.ntfs -f /dev/sdc1                               # Formatea como NTFS
mkfs.vfat -F 32 /dev/sdd1                             # FAT32
mkfs.xfs -f /dev/sde1                                  # XFS forzado
```
---

---

## 88. `sync` – Forzar Escritura de Datos en Disco

El comando `sync` vacía los búferes del sistema de archivos, forzando la escritura de todos los datos pendientes en caché a los discos. Es útil antes de desconectar dispositivos o apagar el sistema para asegurar que no hay pérdida de datos.

**Uso básico**

```fish
sync [opciones]
```

**Opciones**

- `-d`, `--data` → Sincroniza solo datos de archivos, no metadatos.

- `-f`, `--file-system` → Sincroniza el sistema de archivos que contiene el archivo.

- `-a`, `--all` → Sincroniza todos los sistemas de archivos.

- `--help` → Muestra ayuda.

- `--version` → Muestra información de versión.

**Ejemplos**

```fish
sync                                            # Sincroniza todos los búferes
sync -d                                         # Solo datos de archivos
sync -f /home/usuario/archivo.txt               # Sincroniza sistema de archivos del archivo
```
---

## 89. `eject` – Expulsar Dispositivos Extraíbles

El comando `eject` expulsa medios extraíbles como CDs, DVDs, unidades USB o disquetes. También puede cerrar la bandeja si el dispositivo lo soporta.

**Uso básico**

```fish
eject [opciones] [dispositivo|punto_montaje]
```

**Opciones**

- `-t`, `--trayclose` → Cierra la bandeja (si es posible).

- `-T`, `--traytoggle` → Alterna entre abrir/cerrar bandeja.

- `-r`, `--cdrom` → Expulsa CD-ROM.

- `-s`, `--scsi` → Expulsa dispositivo SCSI.

- `-f`, `--floppy` → Expulsa disquete.

- `-d`, `--default` → Muestra el dispositivo por defecto.

- `-a`, `--auto` → Activa/desactiva expulsión automática.

- `-v`, `--verbose` → Modo detallado.

- `-n`, `--noop` → No hace nada, solo muestra lo que haría.

- `-M`, `--no-partitions-unmount` → No desmonta particiones, solo el dispositivo.

**Ejemplos**

```fish
eject                                           # Expulsa el dispositivo por defecto
eject /dev/cdrom                                # Expulsa el CD-ROM
eject /mnt/usb                                  # Expulsa por punto de montaje
eject -t                                        # Cierra la bandeja
eject -T                                        # Abre/cierra la bandeja
eject -v /dev/sdb                               # Detallado
```
---

## 90. `parted` – Administrar Particiones de Discos

El comando `parted` es una herramienta avanzada para crear, eliminar, redimensionar y gestionar particiones en discos. Soporta tanto MBR como GPT.

**Uso básico**

```fish
parted [opciones] [dispositivo] [comando]
```

**Opciones**

- `-l`, `--list` → Lista particiones de todos los dispositivos.

- `-s`, `--script` → Modo script (no interactivo, no pide confirmación).

- `-a`, `--align` → Alineación de particiones (none, cylinder, minimal, optimal).

- `-m`, `--machine` → Salida en formato legible por máquina.

- `-v`, `--version` → Muestra versión.

- `-h`, `--help` → Muestra ayuda.

**Comandos de parted (modo interactivo o directo)**

- `mklabel [tipo]` → Crea tabla de particiones (msdos, gpt, etc.).

- `mkpart [tipo] [inicio] [fin]` → Crea partición.

- `rm [número]` → Elimina partición.

- `resizepart [número] [fin]` → Redimensiona partición.

- `print` → Muestra tabla de particiones.

- `unit [unidad]` → Establece unidad (s, kB, MB, GB, etc.).

- `quit` → Sale.

**Ejemplos**

```fish
parted -l                                         # Lista particiones de todos los discos
parted /dev/sdb print                             # Muestra particiones de /dev/sdb
parted /dev/sdb mklabel gpt                       # Crea tabla GPT
parted /dev/sdb mkpart primary ext4 1MB 10GB      # Crea partición primaria
parted /dev/sdb rm 1                              # Elimina partición 1
parted /dev/sdb resizepart 1 20GB                 # Redimensiona partición 1
parted -s /dev/sdb mkpart primary 10GB 20GB       # Modo script (sin preguntar)
```
---

## 91. `pv` – Monitorear Progreso de Pipes

El comando `pv` (pipe viewer) monitoriza el progreso de datos a través de una tubería (pipe). Muestra información como velocidad de transferencia, tiempo transcurrido y barra de progreso.

**Uso básico**

```fish
comando_origen | pv [opciones] | comando_destino
```

**Opciones**

- `-p`, `--progress` → Muestra barra de progreso.

- `-t`, `--timer` → Muestra tiempo transcurrido.

- `-e`, `--eta` → Muestra tiempo estimado restante.

- `-r`, `--rate` → Muestra velocidad de transferencia.

- `-a`, `--average-rate` → Muestra velocidad media.

- `-b`, `--bytes` → Muestra bytes transferidos.

- `-n`, `--numeric` → Salida numérica (para scripts).

- `-q`, `--quiet` → No muestra salida.

- `-W`, `--wait` → Espera hasta que llegue el primer byte para empezar.

- `-D`, `--delay-start` → Retraso antes de empezar.

- `-s`, `--size` → Tamaño total esperado (para barra de progreso).

- `-B`, `--buffer-size` → Tamaño del búfer.

- `-C`, `--no-splice` → No usa splice(2) (para depuración).

**Ejemplos**

```fish
pv archivo_grande.iso | dd of=/dev/sdb                            # Copia con progreso
tar -czf - /home | pv | ssh usuario@server "cat > backup.tar.gz"  # Backup remoto con progreso
pv -s 4G archivo.iso > /dev/null                                  # Simula transferencia con tamaño conocido
cat /dev/zero | pv | dd of=/dev/null                              # Prueba de velocidad
pv -tpreb archivo.txt | grep "error"                              # Estadísticas completas
dd if=/dev/sda | pv | dd of=/dev/sdb                              # Clonación de disco con progreso
```
---

## 92. `dd` – Copiar y Convertir Datos de Bajo Nivel

El comando `dd` (data duplicator) copia y convierte datos a nivel de bloques. Es extremadamente poderoso para clonar discos, crear imágenes, o realizar operaciones de bajo nivel.

**Uso básico**

```fish
dd if=origen of=destino [opciones]
```

**Opciones**

- `if=` → Archivo de entrada (input file).

- `of=` → Archivo de salida (output file).

- `bs=` → Tamaño de bloque (block size).

- `count=` → Número de bloques a copiar.

- `skip=` → Salta N bloques en la entrada.

- `seek=` → Salta N bloques en la salida.

- `conv=` → Conversiones a aplicar.

- `status=` → Nivel de detalle (none, progress, noxfer).

- `iflag=` → Flags de entrada.

- `oflag=` → Flags de salida.

**Conversiones comunes (conv=)**

- `notrunc` → No truncar archivo de salida.

- `noerror` → Continuar después de errores de lectura.

- `sync` → Rellenar con ceros bloques con error.

- `fsync` → Escritura física antes de terminar.

- `swab` → Intercambiar pares de bytes.

- `lcase` → Convertir a minúsculas.

- `ucase` → Convertir a mayúsculas.

- `sparse` → Intentar crear archivos sparse.

**Flags comunes (iflag/oflag)**

- `direct` → Usar E/S directa (sin caché).

- `dsync` → Escritura sincronizada.

- `sync` → E/S sincronizada.

- `fullblock` → Asegurar bloques completos.

- `append` → Añadir al final (solo oflag).

- `count_bytes` → Interpretar count como bytes.

**Ejemplos**

```fish
dd if=/dev/sda of=backup.img bs=4M               # Clona disco a imagen
dd if=backup.img of=/dev/sdb bs=4M                # Restaura imagen a disco
dd if=/dev/zero of=archivo bs=1M count=100         # Crea archivo de 100MB con ceros
dd if=/dev/sda of=respuesta.img bs=4M status=progress  # Con progreso
dd if=/dev/sda of=/dev/sdb bs=4M conv=noerror,sync    # Clona ignorando errores
dd if=/dev/urandom of=aleatorio.bin bs=1M count=10     # Crea archivo con datos aleatorios
dd if=/dev/cdrom of=imagen.iso bs=2048                  # Crea ISO de CD
dd if=archivo.txt of=archivo.txt.bak conv=ucase         # Convierte a mayúsculas
dd if=/dev/sda bs=512 count=1 | hexdump -C              # Lee primer sector (MBR)
```
---

## 93. `lsmod` – Listar Módulos del Kernel Cargados

El comando `lsmod` muestra qué módulos del kernel están actualmente cargados en el sistema, junto con su tamaño y dependencias.

**Uso básico**

```fish
lsmod
```

**Opciones**

- No tiene opciones significativas.

**Formato de salida**

- `Module` → Nombre del módulo.

- `Size` → Tamaño en bytes.

- `Used by` → Número de instancias y qué módulos lo usan.

**Ejemplos**

```fish
lsmod                                           # Lista todos los módulos cargados
lsmod | grep usb                                 # Filtra módulos USB
lsmod | sort -k2 -n                               # Ordena por tamaño
```
---

## 94. `modprobe` – Cargar o Quitar Módulos del Kernel

El comando `modprobe` añade o elimina módulos del kernel de forma inteligente, resolviendo dependencias automáticamente.

**Uso básico**

```fish
modprobe [opciones] [nombre_módulo]
```

**Opciones**

- `-a`, `--all` → Carga todos los módulos especificados.

- `-r`, `--remove` → Elimina el módulo (en lugar de cargarlo).

- `-v`, `--verbose` → Modo detallado.

- `-q`, `--quiet` → Modo silencioso.

- `-n`, `--dry-run` → Muestra lo que haría pero no ejecuta.

- `-c`, `--show-config` → Muestra la configuración.

- `-l`, `--list` → Lista módulos disponibles (obsoleto).

- `-d`, `--dirname` → Especifica directorio de módulos.

- `-f`, `--force` → Fuerza carga incluso si hay problemas.

- `-s`, `--syslog` → Usa syslog en lugar de stderr.

- `-C`, `--config` → Especifica archivo de configuración.

**Ejemplos**

```fish
modprobe usb-storage                            # Carga el módulo usb-storage
modprobe -r usb-storage                           # Elimina el módulo
modprobe vfat                                       # Carga soporte para FAT
modprobe -v nvidia                                   # Detallado
modprobe -n ntfs                                       # Simula (no ejecuta)
modprobe -r -v usb-storage                              # Elimina detallado
```
---

## 95. `lspci` – Información de Dispositivos PCI

El comando `lspci` lista todos los dispositivos conectados al bus PCI del sistema, como tarjetas gráficas, controladores de red, etc.

**Uso básico**

```fish
lspci [opciones]
```

**Opciones**

- `-v`, `--verbose` → Modo detallado.

- `-vv` → Muy detallado.

- `-vvv` → Extremadamente detallado.

- `-n`, `--numeric` → Muestra IDs numéricos (sin resolver nombres).

- `-nn` → Muestra IDs numéricos y nombres.

- `-k`, `--kernel` → Muestra controladores del kernel en uso.

- `-t`, `--tree` → Muestra en forma de árbol.

- `-s` [[[[domain]:]bus]:][slot][.[func]] → Especifica dispositivo.

- `-d` [vendor]:[device] → Filtra por vendor/device ID.

- `-m`, `--machine` → Salida legible por máquina.

- `-Q`, `--query` → Consulta capacidades.

- `-x` → Hexdump de configuración.

- `-xxx` → Hexdump completo (requiere root).

**Ejemplos**

```fish
lspci                                           # Lista todos los dispositivos PCI
lspci -v                                         # Detallado
lspci -k                                          # Muestra controladores
lspci -t                                           # Vista de árbol
lspci -s 00:02.0                                    # Solo dispositivo específico
lspci -d 10de:                                      # Todos los dispositivos NVIDIA
lspci -nn                                           # Con IDs numéricos
lspci | grep VGA                                     # Tarjetas gráficas
```
---

## 96. `lsusb` – Información de Dispositivos USB

El comando `lsusb` lista todos los dispositivos conectados al bus USB del sistema.

**Uso básico**

```fish
lsusb [opciones]
```

**Opciones**

- `-v`, `--verbose` → Modo detallado.

- `-t`, `--tree` → Muestra en forma de árbol.

- `-s` [[bus]:][devnum] → Especifica dispositivo por bus/número.

- `-d` [vendor]:[product] → Filtra por vendor/product ID.

- `-D` [dispositivo] → Muestra información del archivo de dispositivo.

- `-p`, `--path` → Muestra rutas de sysfs.

- `-q`, `--quiet` → Modo silencioso (solo errores).

**Ejemplos**

```fish
lsusb                                           # Lista todos los dispositivos USB
lsusb -v                                         # Detallado
lsusb -t                                          # Vista de árbol
lsusb -s 002:003                                   # Dispositivo bus 2 dispositivo 3
lsusb -d 0781:                                      # Todos los dispositivos SanDisk
lsusb -D /dev/bus/usb/002/003                        # Info desde archivo de dispositivo
```
---

## 97. `lscpu` – Información de CPU

El comando `lscpu` muestra información detallada sobre la arquitectura de la CPU del sistema.

**Uso básico**

```fish
lscpu [opciones]
```

**Opciones**

- `-a`, `--all` → Muestra CPU online y offline.

- `-b`, `--online` → Muestra solo CPU online.

- `-c`, `--offline` → Muestra solo CPU offline.

- `-e`, `--extended` → Formato extendido (tabla).

- `-p`, `--parse` → Salida parseable (para scripts).

- `-J`, `--json` → Salida en formato JSON.

- `-y`, `--physical` → Muestra IDs físicos en lugar de lógicos.

- `-x`, `--hex` → Muestra máscaras en hexadecimal.

**Ejemplos**

```fish
lscpu                                           # Información completa de CPU
lscpu -e                                          # Formato tabla extendida
lscpu -J                                           # Salida JSON
lscpu -p                                            # Para scripts
lscpu | grep "Model name"                             # Nombre del procesador
lscpu | grep "CPU(s)"                                  # Número de núcleos
```
---

## 98. `dmidecode` – Información del Hardware del Sistema

El comando `dmidecode` extrae información del hardware del sistema desde la tabla DMI (SMBIOS). Proporciona datos detallados sobre BIOS, sistema, placa base, memoria, etc.

**Uso básico**

```fish
dmidecode [opciones]
```

**Opciones**

- `-t`, `--type` → Muestra solo un tipo específico.

- `-s`, `--string` → Muestra solo una cadena DMI específica.

- `-q`, `--quiet` → Modo silencioso.

- `-d`, `--dev-mem` → Lee desde archivo en lugar de /dev/mem.

- `-u`, `--dump` → Muestra datos en bruto (hex).

- `--no-sysfs` → No usa sysfs.

- `-V`, `--version` → Muestra versión.

**Tipos comunes (para -t)**

- `bios` → Información de BIOS.

- `system` → Información del sistema (fabricante, modelo).

- `baseboard` → Información de la placa base.

- `processor` → Información del procesador.

- `memory` → Información de memoria.

- `cache` → Información de caché.

- `connector` → Conectores.

- `slot` → Slots de expansión.

**Ejemplos**

```fish
dmidecode                                       # Toda la información DMI
dmidecode -t system                              # Fabricante y modelo
dmidecode -t bios                                 # Información de BIOS
dmidecode -t memory                                # Información de RAM
dmidecode -s system-serial-number                   # Número de serie
dmidecode -t processor | grep -i speed               # Velocidad del procesador
dmidecode -q -t memory                                # Silencioso, solo memoria
```
---

### Redes y Transferencia de Datos

Linux dispone de un amplio conjunto de herramientas para administrar redes, diagnosticar conectividad y transferir datos entre sistemas. Estos comandos permiten desde verificar la conectividad básica hasta realizar transferencias seguras de archivos y consultas DNS avanzadas.

---

## 99. `ping` – Verificar Conectividad con Otro Host

El comando `ping` envía paquetes ICMP ECHO_REQUEST a un host para probar la conectividad de red y medir la latencia.

**Uso básico**

```fish
ping [opciones] destino
```

**Opciones**

- `-c`, `--count` → Número de paquetes a enviar.

- `-i`, `--interval` → Intervalo entre paquetes (segundos).

- `-s`, `--size` → Tamaño del paquete en bytes.

- `-t`, `--ttl` → Establece TTL (time to live).

- `-W`, `--timeout` → Tiempo de espera para respuesta.

- `-w`, `--deadline` → Tiempo máximo total de ejecución.

- `-f`, `--flood` → Envía paquetes lo más rápido posible (flood ping).

- `-q`, `--quiet` → Salida silenciosa (solo resumen).

- `-v`, `--verbose` → Salida detallada.

- `-a`, `--audible` → Pitido cuando hay respuesta.

- `-4` → Usa IPv4.

- `-6` → Usa IPv6.

**Ejemplos**

```fish
ping google.com                                  # Ping continuo (Ctrl+C para parar)
ping -c 4 8.8.8.8                                 # 4 pings a Google DNS
ping -i 2 -c 10 servidor.local                     # Cada 2 segundos, 10 veces
ping -s 1472 -c 5 192.168.1.1                      # Paquetes de 1472 bytes
ping -W 1 -c 3 10.0.0.1                             # Timeout de 1 segundo
ping -f -c 1000 localhost                           # Flood ping (solo localhost)
```
---

## 100. `ifconfig` – Mostrar y Configurar Interfaces de Red (legacy)

El comando `ifconfig` (interface configuration) muestra y configura interfaces de red. Aunque es legacy y ha sido reemplazado por `ip`, aún se usa ampliamente.

**Uso básico**

```fish
ifconfig [interfaz] [opciones]
```

**Opciones**

- `-a` → Muestra todas las interfaces (incluyendo inactivas).

- `up` → Activa la interfaz.

- `down` → Desactiva la interfaz.

- `inet` [dirección] → Asigna dirección IP.

- `netmask` [máscara] → Asigna máscara de red.

- `broadcast` [dirección] → Asigna dirección de broadcast.

- `hw ether` [MAC] → Cambia dirección MAC.

- `mtu` [tamaño] → Cambia MTU.

- `-s` → Muestra lista corta (similar a netstat -i).

- `-v` → Modo detallado.

**Ejemplos**

```fish
ifconfig                                       # Muestra todas las interfaces activas
ifconfig -a                                      # Muestra todas (incluso inactivas)
ifconfig eth0                                     # Muestra solo eth0
ifconfig eth0 up                                   # Activa eth0
ifconfig eth0 down                                  # Desactiva eth0
ifconfig eth0 192.168.1.100 netmask 255.255.255.0   # Asigna IP y máscara
ifconfig eth0 hw ether 00:11:22:33:44:55            # Cambia MAC
```
---

## 101. `ip` – Configuración y Estado de Red Moderno

El comando `ip` es la herramienta moderna y unificada para mostrar y configurar interfaces de red, rutas, túneles, etc. Reemplaza a ifconfig, route y otros.

**Uso básico**

```fish
ip [opciones] objeto comando
```

**Objetos principales**

- `link` → Interfaz de red (capa 2).

- `addr` → Direcciones IP (capa 3).

- `route` → Tabla de enrutamiento.

- `neigh` → Tabla ARP/NDISC.

- `rule` → Reglas de enrutamiento.

- `maddr` → Direcciones multicast.

- `mroute` → Rutas multicast.

- `tunnel` → Túneles IP.

- `xfrm` → Políticas IPsec.

**Opciones comunes**

- `-s`, `-stats` → Muestra estadísticas.

- `-d`, `-details` → Muestra más detalles.

- `-h`, `-human` → Tamaños legibles.

- `-r`, `-resolve` → Resuelve nombres DNS.

- `-c`, `-color` → Salida coloreada.

- `-4` → Solo IPv4.

- `-6` → Solo IPv6.

- `-br` → Salida breve (brief).

**Ejemplos**

```fish
ip addr show                                    # Muestra todas las IPs (como ifconfig)
ip -br addr show                                 # Formato breve
ip link set eth0 up                               # Activa interfaz
ip link set eth0 down                              # Desactiva interfaz
ip addr add 192.168.1.100/24 dev eth0               # Añade IP
ip addr del 192.168.1.100/24 dev eth0                # Elimina IP
ip route show                                         # Muestra tabla de rutas
ip route add default via 192.168.1.1                   # Añade ruta por defecto
ip neigh show                                          # Muestra tabla ARP
ip -s link show eth0                                    # Estadísticas de interfaz
```
---

## 102. `route` – Mostrar Rutas de Red

El comando `route` muestra y manipula la tabla de enrutamiento IP. Ha sido reemplazado por `ip route`, pero aún se usa en sistemas legacy.

**Uso básico**

```fish
route [opciones] [comando]
```

**Opciones**

- `-n`, `--numeric` → No resuelve nombres (muestra IPs numéricas).

- `-e`, `--extend` → Muestra información extendida.

- `-A`, `--family` → Familia de direcciones (inet, inet6).

- `-F`, `--fib` → Muestra la tabla FIB (Forwarding Information Base).

- `-C`, `--cache` → Muestra la caché de enrutamiento.

**Comandos**

- `add` → Añade ruta.

- `del` → Elimina ruta.

- `-net` → Destino es una red.

- `-host` → Destino es un host.

- `netmask` → Máscara de red.

- `gw` → Gateway.

- `dev` → Interfaz de salida.

**Ejemplos**

```fish
route                                          # Muestra tabla de rutas
route -n                                        # Muestra IPs numéricas
route add -net 192.168.2.0 netmask 255.255.255.0 gw 192.168.1.1  # Añade ruta
route add default gw 192.168.1.1                  # Añade ruta por defecto
route del -net 192.168.2.0                         # Elimina ruta
route add -host 10.0.0.5 dev eth0                   # Ruta para host específico
```
---

## 103. `netstat` – Información de Conexiones y Puertos

El comando `netstat` (network statistics) muestra conexiones de red, tablas de enrutamiento, estadísticas de interfaz y más. Ha sido reemplazado por `ss` en sistemas modernos.

**Uso básico**

```fish
netstat [opciones]
```

**Opciones**

- `-a`, `--all` → Muestra todas las conexiones y puertos en escucha.

- `-t`, `--tcp` → Muestra conexiones TCP.

- `-u`, `--udp` → Muestra conexiones UDP.

- `-l`, `--listening` → Muestra solo puertos en escucha.

- `-p`, `--program` → Muestra programa/PID asociado.

- `-n`, `--numeric` → Muestra direcciones y puertos numéricos.

- `-r`, `--route` → Muestra tabla de enrutamiento.

- `-i`, `--interfaces` → Muestra estadísticas de interfaces.

- `-s`, `--statistics` → Estadísticas por protocolo.

- `-c`, `--continuous` → Actualización continua.

- `-e`, `--extend` → Información extendida.

- `-o`, `--timers` → Muestra timers.

- `-v`, `--verbose` → Modo detallado.

**Ejemplos**

```fish
netstat -a                                       # Todas las conexiones y puertos
netstat -tulpn                                    # Puertos en escucha TCP/UDP con programas
netstat -rn                                        # Tabla de rutas numérica
netstat -i                                           # Estadísticas de interfaces
netstat -s                                            # Estadísticas por protocolo
netstat -t -c 2                                        # Conexiones TCP cada 2 segundos
netstat -an | grep :80                                  # Conexiones en puerto 80
```
---

## 104. `ss` – Información de Sockets

El comando `ss` (socket statistics) es el reemplazo moderno y más rápido de `netstat`. Muestra información detallada sobre sockets de red.

**Uso básico**

```fish
ss [opciones]
```

**Opciones**

- `-t`, `--tcp` → Muestra sockets TCP.

- `-u`, `--udp` → Muestra sockets UDP.

- `-l`, `--listening` → Muestra sockets en escucha.

- `-a`, `--all` → Muestra todos los sockets.

- `-p`, `--processes` → Muestra procesos usando los sockets.

- `-n`, `--numeric` → No resuelve nombres.

- `-r`, `--resolve` → Resuelve nombres.

- `-s`, `--summary` → Muestra resumen estadístico.

- `-e`, `--extended` → Información extendida.

- `-o`, `--options` → Muestra información de timers.

- `-m`, `--memory` → Muestra uso de memoria de sockets.

- `-f`, `--family` → Familia de direcciones (inet, inet6, unix).

- `-A`, `--query` → Tipos de sockets a mostrar.

- `-K`, `--kill` → Mata sockets (requiere más opciones).

- `-H`, `--no-header` → Sin encabezados.

**Ejemplos**

```fish
ss -tulpn                                       # Puertos en escucha TCP/UDP con programas
ss -t -a                                         # Todas las conexiones TCP
ss -u -a                                          # Todas las conexiones UDP
ss -s                                              # Resumen estadístico
ss -lnt                                             # Puertos TCP en escucha numérico
ss -t state established '( dport = :80 )'           # Conexiones establecidas al puerto 80
ss -l '( sport = :22 )'                              # Escuchando en puerto 22
ss -xp                                               # Sockets Unix con procesos
```
---

## 105. `traceroute` – Rastrear Ruta a un Host

El comando `traceroute` rastrea la ruta que siguen los paquetes hasta un host de red, mostrando cada salto (router) intermedio.

**Uso básico**

```fish
traceroute [opciones] destino
```

**Opciones**

- `-n`, `--numeric` → No resuelve nombres (solo IPs).

- `-I`, `--icmp` → Usa ICMP ECHO en lugar de UDP.

- `-T`, `--tcp` → Usa TCP SYN (puerto 80 por defecto).

- `-U`, `--udp` → Usa UDP (por defecto).

- `-p`, `--port` → Puerto de destino.

- `-w`, `--wait` → Tiempo de espera por respuesta.

- `-q`, `--queries` → Número de consultas por salto.

- `-m`, `--max-hops` → Número máximo de saltos.

- `-f`, `--first-hop` → Primer salto TTL.

- `-z`, `--pause` → Pausa entre sondas.

- `-4` → Usa IPv4.

- `-6` → Usa IPv6.

**Ejemplos**

```fish
traceroute google.com                            # Ruta a google.com
traceroute -n 8.8.8.8                              # Solo IPs, sin resolver
traceroute -I 192.168.1.1                           # Usa ICMP
traceroute -T -p 80 google.com                       # TCP SYN al puerto 80
traceroute -m 30 -q 2 servidor.local                  # Máx 30 saltos, 2 consultas
```
---

## 106. `mtr` – Combinación de ping y traceroute

El comando `mtr` (my traceroute) combina la funcionalidad de `traceroute` y `ping` en una herramienta interactiva que actualiza continuamente la información.

**Uso básico**

```fish
mtr [opciones] destino
```

**Opciones**

- `-r`, `--report` → Modo reporte (ejecuta y muestra resultado final).

- `-c`, `--report-cycles` → Número de ciclos para el reporte.

- `-n`, `--no-dns` → No resuelve nombres (solo IPs).

- `-b`, `--show-ips` → Muestra IPs junto con nombres.

- `-i`, `--interval` → Intervalo entre paquetes.

- `-p`, `--port` → Puerto de destino.

- `-4` → Usa IPv4.

- `-6` → Usa IPv6.

- `-t`, `--tcp` → Usa TCP.

- `-u`, `--udp` → Usa UDP.

- `-I`, `--icmp` → Usa ICMP.

- `-a`, `--address` → Dirección de origen.

- `-s`, `--packetsize` → Tamaño del paquete.

- `-w`, `--timeout` → Tiempo de espera.

**Comandos interactivos de mtr**

- `?` → Ayuda.

- `p` → Pausa/continua.

- `q` → Salir.

- `r` → Resetear.

- `0-9` → Ajusta intervalo.

**Ejemplos**

```fish
mtr google.com                                    # Modo interactivo
mtr -r -c 10 8.8.8.8                               # Reporte con 10 ciclos
mtr -n -r -c 5 servidor.local                       # Reporte sin DNS
mtr -T -p 443 google.com                             # TCP al puerto 443
mtr -4 -i 2 google.com                                # IPv4, intervalo 2 segundos
```
---



## 107. `nslookup` – Resolver Nombres de Dominio

El comando `nslookup` consulta servidores DNS para obtener información sobre nombres de dominio y direcciones IP. Es una herramienta clásica aunque algo antigua.

**Uso básico**

```fish
nslookup [opciones] [nombre] [servidor]
```

**Opciones**

- `-type=` → Tipo de registro (A, MX, NS, CNAME, etc.).

- `-port=` → Puerto del servidor DNS.

- `-timeout=` → Tiempo de espera.

- `-retry=` → Número de reintentos.

- `-debug` → Modo debug.

- `-nodebug` → No debug (por defecto).

- `-vc` → Usa TCP en lugar de UDP.

**Modo interactivo**

- `server [nombre]` → Cambia servidor DNS.

- `set type=[tipo]` → Cambia tipo de registro.

- `set debug` → Activa debug.

- `exit` → Salir.

**Ejemplos**

```fish
nslookup google.com                               # Resuelve google.com a IP
nslookup 8.8.8.8                                   # Resuelve IP a nombre (PTR)
nslookup -type=mx gmail.com                         # Consulta registros MX
nslookup -type=ns google.com                         # Consulta servidores DNS
nslookup -port=53 google.com 8.8.8.8                  # Usa servidor específico
nslookup                                             # Modo interactivo
```
---

## 108. `dig` – Información Avanzada de DNS

El comando `dig` (domain information groper) es una herramienta flexible y detallada para realizar consultas DNS. Es más potente que nslookup y es el estándar actual para diagnóstico DNS.

**Uso básico**

```fish
dig [@servidor] [nombre] [tipo] [opciones]
```

**Tipos de registro comunes**

- `A` → Dirección IPv4.

- `AAAA` → Dirección IPv6.

- `MX` → Mail exchange.

- `NS` → Name servers.

- `CNAME` → Alias canónico.

- `TXT` → Texto.

- `SOA` → Start of authority.

- `PTR` → Puntero (resolución inversa).

- `ANY` → Cualquier registro.

**Opciones**

- `+short` → Salida breve (solo respuesta).

- `+noall` → No muestra nada por defecto.

- `+answer` → Muestra solo la sección respuesta.

- `+authority` → Muestra sección autoridad.

- `+additional` → Muestra sección adicional.

- `+stats` → Muestra estadísticas.

- `+trace` → Traza la resolución desde la raíz.

- `+recurse` → Consulta recursiva (por defecto).

- `+norecurse` → Consulta no recursiva.

- `+tcp` → Usa TCP en lugar de UDP.

- `+dnssec` → Muestra información DNSSEC.

- `+multi` → Salida en múltiples líneas.

- `-x [IP]` → Resolución inversa.

**Ejemplos**

```fish
dig google.com                                    # Consulta estándar
dig google.com A                                   # Especifica tipo A
dig google.com MX                                   # Registros MX
dig -x 8.8.8.8                                       # Resolución inversa
dig @8.8.8.8 google.com                               # Usa servidor específico
dig google.com +short                                  # Solo la IP
dig google.com +noall +answer                           # Solo respuesta
dig google.com +trace                                     # Traza completa
dig gmail.com MX +short                                    # Solo servidores MX
dig +nocmd google.com ANY +noall +answer                    # Solo registros ANY
```
---

## 109. `host` – Resolver Nombres de Dominio Simples

El comando `host` es una utilidad simple para realizar búsquedas DNS. Es más directo que `dig` y `nslookup`, ideal para consultas rápidas.

**Uso básico**

```fish
host [opciones] nombre [servidor]
```

**Opciones**

- `-a`, `--all` → Muestra toda la información (equivalente a ANY).

- `-t`, `--type` → Especifica tipo de registro.

- `-v`, `--verbose` → Modo detallado.

- `-W`, `--timeout` → Tiempo de espera.

- `-R`, `--retry` → Número de reintentos.

- `-4` → Usa solo IPv4.

- `-6` → Usa solo IPv6.

- `-C` → Muestra registros SOA.

- `-T` → Usa TCP en lugar de UDP.

- `-l`, `--list` → Lista zona (transferencia de zona).

**Ejemplos**

```fish
host google.com                                    # IP de google.com
host 8.8.8.8                                       # Resolución inversa
host -t mx gmail.com                               # Registros MX
host -a google.com                                 # Todos los registros
host -v google.com                                 # Detallado
host -t ns google.com 8.8.8.8                      # Consulta a servidor específico
```
---

## 110. `hostname` – Mostrar o Cambiar el Nombre del Host

El comando `hostname` muestra o establece el nombre del sistema (hostname) en la red.

**Uso básico**

```fish
hostname [opciones] [nombre]
```

**Opciones**

- `-s`, `--short` → Muestra el nombre corto (primer componente).

- `-f`, `--fqdn` → Muestra el nombre de dominio completo (FQDN).

- `-d`, `--domain` → Muestra solo el dominio.

- `-i`, `--ip-address` → Muestra direcciones IP del host.

- `-I`, `--all-ip-addresses` → Muestra todas las direcciones IP.

- `-A`, `--all-fqdns` → Muestra todos los FQDNs.

- `-y`, `--yp` → Muestra nombre NIS/YP.

- `-b`, `--boot` → Establece hostname por defecto.

- `-F`, `--file` → Lee hostname desde archivo.

**Ejemplos**

```fish
hostname                                           # Muestra nombre del host
hostname -s                                        # Nombre corto
hostname -f                                        # FQDN
hostname -i                                        # IP asociada
hostname -I                                        # Todas las IPs
sudo hostname nuevo-nombre                         # Cambia hostname (temporal)
sudo hostname -F /etc/hostname                     # Cambia desde archivo
```
---

## 111. `curl` – Descargar o Interactuar con Recursos Web

El comando `curl` (client URL) transfiere datos desde o hacia un servidor, soportando múltiples protocolos (HTTP, HTTPS, FTP, SFTP, etc.). Es extremadamente versátil y ampliamente utilizado.

**Uso básico**

```fish
curl [opciones] [URL]
```

**Opciones principales**

- `-o`, `--output` → Guarda salida en archivo.

- `-O`, `--remote-name` → Guarda con nombre remoto.

- `-L`, `--location` → Sigue redirecciones.

- `-I`, `--head` → Muestra solo cabeceras.

- `-i`, `--include` → Incluye cabeceras en salida.

- `-s`, `--silent` → Modo silencioso (sin progreso).

- `-S`, `--show-error` → Muestra errores (con -s).

- `-v`, `--verbose` → Modo detallado.

- `-k`, `--insecure` → Permite conexiones SSL sin verificar.

- `-u`, `--user` → Usuario:contraseña para autenticación.

- `-X`, `--request` → Método HTTP (GET, POST, PUT, DELETE).

- `-H`, `--header` → Añade cabecera HTTP.

- `-d`, `--data` → Envía datos POST.

- `-F`, `--form` → Envía datos multipart/form-data.

- `-b`, `--cookie` → Envía cookies.

- `-c`, `--cookie-jar` → Guarda cookies.

- `-A`, `--user-agent` → User-Agent personalizado.

- `-C`, `--continue-at` → Continúa descarga interrumpida.

- `--limit-rate` → Limita velocidad.

- `--progress-bar` → Barra de progreso.

- `-T`, `--upload-file` → Sube archivo.

**Ejemplos**

```fish
curl https://ejemplo.com                              # Muestra contenido
curl -o archivo.html https://ejemplo.com              # Guarda en archivo
curl -O https://ejemplo.com/archivo.zip               # Guarda con nombre remoto
curl -I https://google.com                            # Solo cabeceras
curl -L https://bit.ly/xxxx                           # Sigue redirecciones
curl -u usuario:pass ftp://servidor/archivo.txt       # FTP autenticado
curl -X POST -d "nombre=juan" https://ejemplo.com     # POST con datos
curl -H "Authorization: Bearer TOKEN" https://api.com # Con cabecera
curl -k https://sitio-con-certificado-invalido.com    # Ignora SSL
curl -C - -O https://ejemplo.com/gran_archivo.iso     # Reanuda descarga
curl --limit-rate 100K -O https://ejemplo.com/archivo # Limita velocidad
```
---

## 112. `wget` – Descargar Archivos desde Web

El comando `wget` es una herramienta no interactiva para descargar archivos de internet. Soporta HTTP, HTTPS, FTP y es ideal para descargas recursivas y automatizadas.

**Uso básico**

```fish
wget [opciones] [URL]
```

**Opciones**

- `-O`, `--output-document` → Guarda con nombre específico.

- `-P`, `--directory-prefix` → Directorio de destino.

- `-c`, `--continue` → Continúa descarga parcial.

- `-b`, `--background` → Descarga en segundo plano.

- `-q`, `--quiet` → Modo silencioso.

- `-v`, `--verbose` → Modo detallado.

- `--limit-rate` → Limita velocidad.

- `-t`, `--tries` → Número de reintentos.

- `-T`, `--timeout` → Tiempo de espera.

- `-w`, `--wait` → Espera entre descargas.

- `-r`, `--recursive` → Descarga recursiva.

- `-l`, `--level` → Profundidad recursiva.

- `-np`, `--no-parent` → No sube al directorio padre.

- `-A`, `--accept` → Acepta solo ciertas extensiones.

- `-R`, `--reject` → Rechaza ciertas extensiones.

- `-nd`, `--no-directories` → No crea directorios.

- `-x`, `--force-directories` → Fuerza creación de directorios.

- `-nH`, `--no-host-directories` → No crea directorio host.

- `--cut-dirs` → Elimina N componentes de directorio.

- `-U`, `--user-agent` → User-Agent personalizado.

- `--header` → Añade cabecera.

- `--post-data` → Envía datos POST.

- `--mirror` → Modo espejo (equivalente a -r -l inf -N -np).

- `-N`, `--timestamping` → Solo descarga si es más reciente.

- `-m`, `--mirror` → Activa opciones para espejo.

**Ejemplos**

```fish
wget https://ejemplo.com/archivo.zip                 # Descarga simple
wget -c https://ejemplo.com/gran_archivo.iso         # Continúa descarga
wget -O script.py https://ejemplo.com/script.py      # Guarda con otro nombre
wget -r -l 2 https://ejemplo.com/docs/               # Descarga recursiva 2 niveles
wget -r -A .pdf,.doc https://ejemplo.com/            # Solo PDFs y DOCs
wget -m https://ejemplo.com                          # Modo espejo (sitio completo)
wget -b https://ejemplo.com/archivo.iso              # Segundo plano
wget --limit-rate=200k https://ejemplo.com/archivo   # Limita a 200KB/s
wget -U "Mozilla/5.0" https://ejemplo.com            # User-Agent personalizado
wget -t 5 -T 30 https://ejemplo.com/archivo          # 5 reintentos, timeout 30s
```
---

## 113. `ssh` – Conexión Remota Segura

El comando `ssh` (Secure Shell) permite conectarse de forma segura a un sistema remoto, ejecutar comandos o transferir archivos de manera encriptada.

**Uso básico**

```fish
ssh [opciones] [usuario@]host [comando]
```

**Opciones**

- `-p`, `--port` → Puerto del servidor SSH.

- `-l`, `--login` → Usuario de login.

- `-i`, `--identity_file` → Archivo de clave privada.

- `-v`, `--verbose` → Modo detallado (para depuración).

- `-vvv` → Muy detallado.

- `-q`, `--quiet` → Modo silencioso.

- `-F`, `--config` → Archivo de configuración.

- `-C`, `--compression` → Activa compresión.

- `-X`, `--forward-x11` → Reenvío X11.

- `-Y`, `--forward-x11-trusted` → X11 confiable.

- `-L`, `--local-forward` → Reenvío de puerto local.

- `-R`, `--remote-forward` → Reenvío de puerto remoto.

- `-D`, `--dynamic-forward` → Reenvío dinámico (SOCKS).

- `-N`, `--no-shell` → No ejecuta comando remoto.

- `-f`, `--background` → Segundo plano después de autenticación.

- `-t`, `--tty` → Fuerza asignación de pseudo-terminal.

- `-T`, `--no-tty` → Desactiva pseudo-terminal.

- `-o`, `--option` → Opciones de configuración.

- `-J`, `--proxy-jump` → Salta a través de host bastión.

**Ejemplos**

```fish
ssh usuario@servidor.com                              # Conexión simple
ssh -p 2222 usuario@servidor.com                      # Puerto personalizado
ssh -i ~/.ssh/id_rsa usuario@servidor.com             # Usa clave específica
ssh usuario@servidor.com 'comando'                    # Ejecuta comando remoto
ssh -X usuario@servidor.com                           # Reenvío X11
ssh -L 8080:localhost:80 usuario@servidor.com         # Reenvío de puerto local
ssh -D 1080 usuario@servidor.com                      # Proxy SOCKS
ssh -J bastion@servidor1 servidor2                    # Salta por bastión
ssh -v usuario@servidor.com                           # Modo debug
```
---

## 114. `scp` – Copiar Archivos vía SSH

El comando `scp` (secure copy) copia archivos entre hosts de forma segura usando SSH.

**Uso básico**

```fish
scp [opciones] origen destino
```

**Formatos**

- `archivo_local` → Archivo local.

- `usuario@host:ruta` → Archivo remoto.

- `-r`, `--recursive` → Copia directorios recursivamente.

- `-p`, `--preserve` → Preserva atributos (permisos, tiempos).

- `-P`, `--port` → Puerto del servidor SSH.

- `-i`, `--identity_file` → Archivo de clave privada.

- `-v`, `--verbose` → Modo detallado.

- `-q`, `--quiet` → Modo silencioso.

- `-C`, `--compression` → Activa compresión.

- `-l`, `--limit` → Limita ancho de banda (Kbit/s).

- `-o`, `--option` → Opciones SSH.

- `-3` → Copia entre dos hosts remotos via local.

- `-4` → Usa solo IPv4.

- `-6` → Usa solo IPv6.

**Ejemplos**

```fish
scp archivo.txt usuario@servidor.com:/home/usuario/       # Copia local a remoto
scp usuario@servidor.com:/home/usuario/archivo.txt .      # Copia remoto a local
scp -r carpeta/ usuario@servidor.com:/home/usuario/       # Copia directorio
scp -P 2222 archivo.txt usuario@servidor.com:             # Puerto personalizado
scp -i clave.pem archivo.txt usuario@servidor.com:        # Con clave específica
scp usuario1@servidor1:/archivo.txt usuario2@servidor2:/  # Entre remotos
scp -l 1000 archivo_grande.iso usuario@servidor.com:      # Limita a 1000 Kbit/s
```
---

## 115. `rsync` – Sincronización Eficiente de Archivos

El comando `rsync` (remote sync) sincroniza archivos y directorios de forma eficiente, copiando solo las diferencias. Es ideal para backups y transferencias.

**Uso básico**

```fish
rsync [opciones] origen destino
```

**Opciones**

- `-a`, `--archive` → Modo archivo (preserva todo, recursivo).

- `-v`, `--verbose` → Modo detallado.

- `-z`, `--compress` → Comprime durante la transferencia.

- `-r`, `--recursive` → Recursivo.

- `-u`, `--update` → Solo copia si origen es más reciente.

- `-n`, `--dry-run` → Simula (no ejecuta).

- `-P` → Muestra progreso y permite reanudar (--partial --progress).

- `--progress` → Muestra progreso.

- `--partial` → Mantiene archivos parciales.

- `--delete` → Elimina en destino archivos que no están en origen.

- `--exclude` → Excluye patrones.

- `--include` → Incluye patrones.

- `-e`, `--rsh` → Especifica shell remota (ssh por defecto).

- `-b`, `--backup` → Crea backups.

- `--backup-dir` → Directorio para backups.

- `-l`, `--links` → Copia enlaces simbólicos.

- `-L`, `--copy-links` → Sigue enlaces y copia destino.

- `-H`, `--hard-links` → Preserva enlaces duros.

- `-p`, `--perms` → Preserva permisos.

- `-o`, `--owner` → Preserva propietario (root).

- `-g`, `--group` → Preserva grupo.

- `-t`, `--times` → Preserva tiempos.

- `-D`, `--devices` → Preserva archivos especiales.

- `--delete-excluded` → Elimina excluidos en destino.

- `--max-size` → No transfiere archivos mayores.

- `--min-size` → No transfiere archivos menores.

- `-W`, `--whole-file` → Copia archivos completos (no delta).

- `--bwlimit` → Limita ancho de banda.

**Ejemplos**

```fish
rsync -av origen/ destino/                                    # Sincroniza local
rsync -avz archivo.txt usuario@servidor.com:/home/            # Envía comprimido
rsync -av usuario@servidor.com:/home/ ./backup/               # Descarga remoto
rsync -av --delete origen/ destino/                           # Elimina en destino lo que falta en origen
rsync -avn --exclude="*.tmp" origen/ destino/                 # Simula excluyendo .tmp
rsync -avP usuario@servidor.com:archivo.iso .                 # Con progreso y reanudable
rsync -av -e "ssh -p 2222" origen/ usuario@servidor.com:      # Puerto personalizado
rsync -av --bwlimit=1000 origen/ destino/                     # Limita a 1000 KB/s
rsync -av --link-dest=../backup_anterior origen/ backup_hoy   # Backup incremental
```
---

## 116. `ftp` – Transferencia de Archivos (legacy)

El comando `ftp` (file transfer protocol) es un cliente para el protocolo FTP tradicional. Es inseguro (transmite en claro) y ha sido reemplazado por sftp.

**Uso básico**

```fish
ftp [opciones] [host]
```

**Opciones**

- `-v`, `--verbose` → Modo detallado.

- `-n`, `--no-login` → No intenta login automático.

- `-i`, `--no-prompt` → Desactiva confirmación en mget/mput.

- `-d`, `--debug` → Modo debug.

- `-g`, `--no-glob` → Desactiva expansión de nombres.

- `-p`, `--passive` → Modo pasivo.

- `-s`, `--source` → Ejecuta comandos desde archivo.

**Comandos FTP interactivos**

- `open [host]` → Conecta a servidor.

- `user [nombre]` → Especifica usuario.

- `ls` → Lista archivos.

- `cd [dir]` → Cambia directorio.

- `get [archivo]` → Descarga archivo.

- `put [archivo]` → Sube archivo.

- `mget [patrón]` → Descarga múltiples archivos.

- `mput [patrón]` → Sube múltiples archivos.

- `binary` → Modo binario.

- `ascii` → Modo texto.

- `passive` → Activa modo pasivo.

- `quit` o `bye` → Salir.

**Ejemplos**

```fish
ftp servidor.com                                  # Conecta a servidor
ftp -p servidor.com                               # Modo pasivo
ftp -n servidor.com                               # Sin login automático
```
**Dentro de FTP:**
```
user usuario
password
get archivo.txt
put local.txt
quit
```
---

## 117. `sftp` – Transferencia Segura de Archivos

El comando `sftp` (SSH File Transfer Protocol) es un cliente de transferencia de archivos interactivo que usa SSH, proporcionando seguridad en las transferencias.

**Uso básico**

```fish
sftp [opciones] [usuario@]host
```

**Opciones**

- `-P`, `--port` → Puerto del servidor SSH.

- `-i`, `--identity` → Archivo de clave privada.

- `-v`, `--verbose` → Modo detallado.

- `-q`, `--quiet` → Modo silencioso.

- `-b`, `--batch` → Archivo por lotes (comandos).

- `-C`, `--compression` → Activa compresión.

- `-o`, `--option` → Opciones SSH.

- `-R`, `--request` → Solicita opciones.

- `-B`, `--buffer` → Tamaño de búfer.

- `-r`, `--recursive` → Operaciones recursivas.

**Comandos sftp interactivos**

- `ls` → Lista archivos remotos.

- `lls` → Lista archivos locales.

- `cd [dir]` → Cambia directorio remoto.

- `lcd [dir]` → Cambia directorio local.

- `get [archivo]` → Descarga archivo.

- `put [archivo]` → Sube archivo.

- `mget [patrón]` → Descarga múltiples archivos.

- `mput [patrón]` → Sube múltiples archivos.

- `rm [archivo]` → Elimina archivo remoto.

- `mkdir [dir]` → Crea directorio remoto.

- `rmdir [dir]` → Elimina directorio remoto.

- `chmod [permisos] [archivo]` → Cambia permisos.

- `chown [propietario] [archivo]` → Cambia propietario.

- `chgrp [grupo] [archivo]` → Cambia grupo.

- `pwd` → Directorio remoto actual.

- `lpwd` → Directorio local actual.

- `!comando` → Ejecuta comando local.

- `bye`, `quit`, `exit` → Salir.

**Ejemplos**

```fish
sftp usuario@servidor.com                           # Conecta
sftp -P 2222 usuario@servidor.com                   # Puerto personalizado
sftp -i ~/.ssh/clave.pem usuario@servidor.com       # Con clave específica
sftp -b comandos.txt usuario@servidor.com           # Modo batch
```

**Dentro de sftp:**
```
get archivo_remoto.txt
put archivo_local.txt
mget *.log
ls -la
quit
```
---

## 118. `telnet` – Conexión Remota Simple

El comando `telnet` es un protocolo de conexión remota inseguro (texto en claro). Se usa principalmente para probar puertos y servicios, no para acceso remoto real.

**Uso básico**

```fish
telnet [opciones] [host] [puerto]
```

**Opciones**

- `-l`, `--user` → Usuario de login.

- `-a`, `--autologin` → Login automático.

- `-K`, `--no-autologin` → Desactiva login automático.

- `-d`, `--debug` → Modo debug.

- `-e`, `--escape` → Carácter de escape.

- `-n`, `--trace` → Traza conexiones.

**Comandos telnet (modo interactivo)**

- `Ctrl+]` → Carácter de escape para comandos.

- `quit` → Salir.

- `close` → Cierra conexión.

- `open [host] [puerto]` → Abre nueva conexión.

- `status` → Estado de la conexión.

- `send [argumentos]` → Envía comandos especiales.

- `set [variable] [valor]` → Configura variables.

**Ejemplos**

```fish
telnet servidor.com                               # Conexión a servidor (puerto 23)
telnet servidor.com 80                             # Prueba puerto HTTP
telnet smtp.gmail.com 25                            # Prueba SMTP
telnet localhost 22                                  # Prueba SSH local
# Ctrl+] para salir al prompt de telnet
# quit para salir
```
---

### Compresión y Empaquetado

Linux ofrece numerosas herramientas para comprimir y empaquetar archivos, reduciendo el espacio ocupado y facilitando el transporte y almacenamiento de datos. Estos comandos permiten trabajar con los formatos de compresión más comunes.

---

## 119. `tar` – Empaquetar y Comprimir Archivos

El comando `tar` (tape archive) empaqueta múltiples archivos en un solo archivo (tarball). Puede combinarse con compresión (gzip, bzip2, xz) para reducir el tamaño.

**Uso básico**

```fish
tar [opciones] [archivo.tar] [archivos...]
```

**Opciones principales**

- `-c`, `--create` → Crea un nuevo archivo.

- `-x`, `--extract` → Extrae archivos.

- `-t`, `--list` → Lista contenido.

- `-f`, `--file` → Especifica nombre del archivo.

- `-v`, `--verbose` → Modo detallado.

- `-z`, `--gzip` → Comprime/descomprime con gzip (.tar.gz, .tgz).

- `-j`, `--bzip2` → Comprime/descomprime con bzip2 (.tar.bz2).

- `-J`, `--xz` → Comprime/descomprime con xz (.tar.xz).

- `-a`, `--auto-compress` → Detecta compresión por extensión.

- `-r`, `--append` → Añade archivos al final.

- `-u`, `--update` → Añade solo archivos más nuevos.

- `-d`, `--diff` → Compara archivo con sistema.

- `-p`, `--preserve-permissions` → Preserva permisos.

- `--same-owner` → Preserva propietario (root).

- `--exclude` → Excluye patrones.

- `-C`, `--directory` → Cambia a directorio.

- `-P`, `--absolute-names` → Usa rutas absolutas.

- `--wildcards` → Usa comodines.

**Ejemplos**

```fish
tar -cvf archivo.tar carpeta/                         # Empaqueta sin comprimir
tar -czvf archivo.tar.gz carpeta/                     # Empaqueta y comprime con gzip
tar -cjvf archivo.tar.bz2 carpeta/                    # Empaqueta y comprime con bzip2
tar -cJvf archivo.tar.xz carpeta/                     # Empaqueta y comprime con xz
tar -xvf archivo.tar                                  # Extrae
tar -xzvf archivo.tar.gz                              # Extrae gzip
tar -xjvf archivo.tar.bz2                             # Extrae bzip2
tar -xJvf archivo.tar.xz                              # Extrae xz
tar -tvf archivo.tar                                  # Lista contenido
tar -rvf archivo.tar nuevo.txt                        # Añade archivo
tar -czvf archivo.tgz --exclude="*.tmp" carpeta/      # Excluye .tmp
tar -czvf backup.tar.gz -C /home/usuario .            # Empaqueta desde directorio
tar -xzvf archivo.tar.gz -C /directorio/destino       # Extrae en directorio
```
---

## 120. `gzip` – Comprimir Archivos .gz

El comando `gzip` comprime archivos usando el algoritmo Lempel-Ziv (LZ77), reduciendo su tamaño. Por defecto, reemplaza el archivo original por uno con extensión .gz.

**Uso básico**

```fish
gzip [opciones] [archivo]
```

**Opciones**

- `-d`, `--decompress` → Descomprime.

- `-c`, `--stdout` → Escribe en salida estándar (no modifica archivo).

- `-k`, `--keep` → Mantiene el archivo original.

- `-l`, `--list` → Lista información del archivo comprimido.

- `-r`, `--recursive` → Comprime recursivamente directorios.

- `-v`, `--verbose` → Modo detallado.

- `-t`, `--test` → Prueba integridad.

- `-1` a `-9` → Nivel de compresión (1 rápido, 9 mejor compresión).

- `-f`, `--force` → Fuerza compresión.

- `-n`, `--no-name` → No guarda nombre original.

- `-N`, `--name` → Guarda nombre original.

**Ejemplos**

```fish
gzip archivo.txt                                   # Comprime a archivo.txt.gz
gzip -9 archivo.txt                                # Máxima compresión
gzip -d archivo.txt.gz                             # Descomprime
gzip -k archivo.txt                                # Comprime manteniendo original
gzip -c archivo.txt > archivo.txt.gz               # Comprime a stdout
gzip -l archivo.txt.gz                             # Información del comprimido
gzip -r carpeta/                                   # Comprime todos los archivos en carpeta
```
---

## 121. `gunzip` – Descomprimir .gz

El comando `gunzip` descomprime archivos comprimidos con gzip. Es equivalente a `gzip -d`.

**Uso básico**

```fish
gunzip [opciones] [archivo.gz]
```

**Opciones**

- `-c`, `--stdout` → Escribe en salida estándar.

- `-f`, `--force` → Fuerza descompresión.

- `-k`, `--keep` → Mantiene el archivo comprimido.

- `-l`, `--list` → Lista información.

- `-r`, `--recursive` → Recursivo.

- `-v`, `--verbose` → Modo detallado.

- `-t`, `--test` → Prueba integridad.

**Ejemplos**

```fish
gunzip archivo.txt.gz                             # Descomprime
gunzip -c archivo.txt.gz > archivo.txt              # Descomprime a stdout
gunzip -k archivo.txt.gz                             # Descomprime manteniendo .gz
gunzip -r carpeta/                                    # Descomprime todos .gz en carpeta
gunzip -l archivo.txt.gz                               # Muestra información
```
---

## 122. `bzip2` – Comprimir Archivos .bz2

El comando `bzip2` comprime archivos usando el algoritmo Burrows-Wheeler, generalmente ofreciendo mejor compresión que gzip a costa de mayor tiempo.

**Uso básico**

```fish
bzip2 [opciones] [archivo]
```

**Opciones**

- `-d`, `--decompress` → Descomprime.

- `-c`, `--stdout` → Escribe en salida estándar.

- `-k`, `--keep` → Mantiene el archivo original.

- `-v`, `--verbose` → Modo detallado.

- `-t`, `--test` → Prueba integridad.

- `-1` a `-9` → Nivel de compresión (1 rápido, 9 mejor compresión).

- `-f`, `--force` → Fuerza compresión.

- `-z`, `--compress` → Comprime (por defecto).

- `-s`, `--small` → Reduce uso de memoria.

**Ejemplos**

```fish
bzip2 archivo.txt                                # Comprime a archivo.txt.bz2
bzip2 -9 archivo.txt                              # Máxima compresión
bzip2 -d archivo.txt.bz2                           # Descomprime
bzip2 -k archivo.txt                                # Comprime manteniendo original
bzip2 -c archivo.txt > archivo.txt.bz2               # Comprime a stdout
bzip2 -v archivo.txt                                  # Detallado
```

---

## 123. `bunzip2` – Descomprimir .bz2

El comando `bunzip2` descomprime archivos comprimidos con bzip2. Es equivalente a `bzip2 -d`.

**Uso básico**

```fish
bunzip2 [opciones] [archivo.bz2]
```

**Opciones**

- `-c`, `--stdout` → Escribe en salida estándar.

- `-f`, `--force` → Fuerza descompresión.

- `-k`, `--keep` → Mantiene el archivo comprimido.

- `-v`, `--verbose` → Modo detallado.

- `-t`, `--test` → Prueba integridad.

- `-L`, `--license` → Muestra licencia.

**Ejemplos**

```fish
bunzip2 archivo.txt.bz2                           # Descomprime
bunzip2 -c archivo.txt.bz2 > archivo.txt           # Descomprime a stdout
bunzip2 -k archivo.txt.bz2                          # Descomprime manteniendo .bz2
bunzip2 -v archivo.txt.bz2                           # Detallado
bunzip2 -t archivo.txt.bz2                            # Prueba integridad
```
---

## 124. `zip` – Comprimir en .zip

El comando `zip` empaqueta y comprime archivos en el formato ZIP, ampliamente compatible con otros sistemas operativos como Windows.

**Uso básico**

```fish
zip [opciones] archivo.zip [archivos...]
```

**Opciones**

- `-r`, `--recurse-paths` → Recursivo (incluye subdirectorios).

- `-m`, `--move` → Mueve archivos (los elimina después de comprimir).

- `-u`, `--update` → Actualiza archivos existentes.

- `-d`, `--delete` → Elimina archivos del zip.

- `-l`, `--list` → Lista contenido.

- `-v`, `--verbose` → Modo detallado.

- `-q`, `--quiet` → Modo silencioso.

- `-e`, `--encrypt` → Cifra con contraseña.

- `-P`, `--password` → Especifica contraseña (inseguro).

- `-x`, `--exclude` → Excluye patrones.

- `-i`, `--include` → Incluye solo patrones.

- `-0` a `-9` → Nivel de compresión (0 sin compresión, 9 máxima).

- `-T`, `--test` → Prueba integridad.

- `-y`, `--symlinks` → Almacena enlaces simbólicos.

- `-z`, `--comment` → Añade comentario.

- `-j`, `--junk-paths` → No almacena rutas (solo nombres).

**Ejemplos**

```fish
zip archivo.zip archivo.txt                        # Comprime un archivo
zip -r respaldo.zip carpeta/                         # Comprime directorio recursivamente
zip -e secreto.zip documento.txt                      # Cifra con contraseña
zip -r -9 maxima.zip carpeta/                          # Máxima compresión
zip -u archivo.zip nuevo.txt                            # Actualiza añadiendo
zip -d archivo.zip viejo.txt                             # Elimina archivo del zip
zip -r excluye.zip carpeta/ -x "*.tmp"                   # Excluye .tmp
zip -j solo_nombres.zip carpeta/*                        # Sin rutas, solo nombres
zip -T archivo.zip                                        # Prueba integridad
```
---

## 125. `unzip` – Descomprimir .zip

El comando `unzip` extrae archivos de un archivo ZIP.

**Uso básico**

```fish
unzip [opciones] archivo.zip [archivos...] [-d directorio]
```

**Opciones**

- `-d`, `--directory` → Directorio de destino.

- `-l`, `--list` → Lista contenido sin extraer.

- `-v`, `--verbose` → Modo detallado.

- `-q`, `--quiet` → Modo silencioso.

- `-n`, `--never-overwrite` → No sobrescribe archivos existentes.

- `-o`, `--overwrite` → Sobrescribe sin preguntar.

- `-u`, `--update` → Actualiza archivos más nuevos.

- `-t`, `--test` → Prueba integridad.

- `-P`, `--password` → Especifica contraseña.

- `-x`, `--exclude` → Excluye archivos.

- `-j`, `--junk-paths` → No crea directorios (extrae todos al mismo nivel).

- `-Z` → Modo zipinfo (información detallada).

**Ejemplos**

```fish
unzip archivo.zip                                  # Extrae en directorio actual
unzip archivo.zip -d /directorio/destino            # Extrae en directorio específico
unzip -l archivo.zip                                 # Lista contenido
unzip -t archivo.zip                                  # Prueba integridad
unzip -o archivo.zip                                   # Sobrescribe sin preguntar
unzip -n archivo.zip                                    # No sobrescribe existentes
unzip archivo.zip "*.txt" -d textos/                    # Extrae solo .txt
unzip -j archivo.zip                                     # Extrae sin directorios
unzip -P contraseña secreto.zip                           # Con contraseña
```
---

## 126. `7z` – Comprimir o Descomprimir .7z

El comando `7z` es parte de p7zip, una implementación del formato 7-Zip, que ofrece alta compresión. Soporta múltiples formatos (7z, ZIP, GZIP, BZIP2, TAR, etc.).

**Uso básico**

```fish
7z [comando] [opciones] archivo [archivos...]
```

**Comandos principales**

- `a` → Añadir a archivo (crear).

- `x` → Extraer con rutas completas.

- `e` → Extraer sin rutas (todos al mismo nivel).

- `l` → Listar contenido.

- `t` → Probar integridad.

- `u` → Actualizar.

- `d` → Eliminar del archivo.

- `rn` → Renombrar.

**Opciones**

- `-r` → Recursivo.

- `-o` → Directorio de salida.

- `-p` → Establece contraseña.

- `-m` → Método de compresión.

- `-mx` → Nivel de compresión (0-9).

- `-t` → Tipo de archivo (7z, zip, gzip, etc.).

- `-y` → Sí a todo.

- `-spf` → Usa rutas completas.

- `-ssw` → Comprime archivos abiertos.

**Ejemplos**

```fish
7z a archivo.7z carpeta/                           # Crea 7z con carpeta
7z a -tzip archivo.zip carpeta/                     # Crea ZIP
7z x archivo.7z                                      # Extrae con rutas
7z e archivo.7z                                       # Extrae sin rutas
7z l archivo.7z                                        # Lista contenido
7z t archivo.7z                                         # Prueba integridad
7z a -mx=9 archivo.7z carpeta/                           # Máxima compresión
7z a -psecreto archivo.7z documento.txt                  # Con contraseña
7z x -o/directorio/destino archivo.7z                     # Extrae a directorio
7z d archivo.7z archivo.txt                                # Elimina archivo del 7z
```
---

## 127. `rar` – Comprimir .rar

El comando `rar` comprime archivos en formato RAR, un formato propietario muy utilizado. Puede no estar instalado por defecto en todos los sistemas.

**Uso básico**

```fish
rar [comando] [opciones] archivo.rar [archivos...]
```

**Comandos principales**

- `a` → Añadir a archivo (crear).

- `x` → Extraer con rutas.

- `e` → Extraer sin rutas.

- `l` → Listar contenido.

- `t` → Probar integridad.

- `r` → Reparar archivo.

- `d` → Eliminar del archivo.

- `c` → Añadir comentario.

- `cw` → Escribir comentario a archivo.

**Opciones**

- `-r` → Recursivo.

- `-m0` a `-m5` → Nivel de compresión (0 sin compresión, 5 máxima).

- `-p` → Establece contraseña.

- `-v` → Crea volúmenes (tamaño especificado).

- `-ep1` → Excluye base de nombres.

- `-y` → Sí a todo.

- `-o+` → Sobrescribe archivos existentes.

- `-o-` → No sobrescribe.

- `-rr` → Añade datos de recuperación.

**Ejemplos**

```fish
rar a archivo.rar carpeta/                          # Crea RAR con carpeta
rar a -r archivo.rar *.txt                           # Comprime todos los .txt
rar x archivo.rar                                     # Extrae con rutas
rar e archivo.rar                                      # Extrae sin rutas
rar l archivo.rar                                       # Lista contenido
rar t archivo.rar                                        # Prueba integridad
rar a -m5 -psecreto archivo.rar documento.txt            # Máxima compresión con contraseña
rar a -v100M gran_archivo.rar archivo.iso                 # Crea volúmenes de 100MB
rar d archivo.rar archivo.txt                              # Elimina archivo
```
---

## 128. `unrar` – Descomprimir .rar

El comando `unrar` extrae archivos de un archivo RAR. Es la versión gratuita para descomprimir (no para crear).

**Uso básico**

```fish
unrar [comando] [opciones] archivo.rar [archivos...] [ruta_destino]
```

**Comandos principales**

- `x` → Extraer con rutas completas.

- `e` → Extraer sin rutas (todos al mismo nivel).

- `l` → Listar contenido.

- `t` → Probar integridad.

- `v` → Listar contenido detallado (verboso).

- `p` → Enviar a stdout.

**Opciones**

- `-o+` → Sobrescribe archivos existentes.

- `-o-` → No sobrescribe.

- `-p` → Especifica contraseña.

- `-y` → Sí a todo.

- `-r` → Recursivo.

- `-idp` → No muestra porcentaje.

**Ejemplos**

```fish
unrar x archivo.rar                                 # Extrae con rutas
unrar e archivo.rar                                  # Extrae sin rutas
unrar l archivo.rar                                   # Lista contenido
unrar t archivo.rar                                    # Prueba integridad
unrar x archivo.rar /directorio/destino/                # Extrae a directorio específico
unrar x -pcontraseña secreto.rar                        # Con contraseña
unrar x archivo.rar *.txt -o+                            # Extrae solo .txt sobrescribiendo
```
---

## 129. `xz` – Comprimir .xz

El comando `xz` comprime archivos usando el algoritmo LZMA2, ofreciendo altas tasas de compresión, generalmente superiores a gzip y bzip2.

**Uso básico**

```fish
xz [opciones] [archivo]
```

**Opciones**

- `-d`, `--decompress` → Descomprime.

- `-c`, `--stdout` → Escribe en salida estándar.

- `-k`, `--keep` → Mantiene el archivo original.

- `-v`, `--verbose` → Modo detallado.

- `-l`, `--list` → Lista información del archivo comprimido.

- `-t`, `--test` → Prueba integridad.

- `-0` a `-9` → Nivel de compresión (0 rápido, 9 mejor compresión).

- `-e`, `--extreme` → Modo extremo (más compresión, más lento).

- `-f`, `--force` → Fuerza compresión.

- `-T`, `--threads` → Número de hilos.

- `-z`, `--compress` → Comprime (por defecto).

- `-q`, `--quiet` → Modo silencioso.

**Ejemplos**

```fish
xz archivo.txt                                     # Comprime a archivo.txt.xz
xz -9 archivo.txt                                   # Máxima compresión
xz -d archivo.txt.xz                                 # Descomprime
xz -k archivo.txt                                     # Comprime manteniendo original
xz -c archivo.txt > archivo.txt.xz                     # Comprime a stdout
xz -l archivo.txt.xz                                    # Información del comprimido
xz -T 4 archivo.txt                                      # Usa 4 hilos
xz -e -9 archivo.txt                                      # Modo extremo con máxima compresión
```
---

## 130. `cpio` – Empaquetar Archivos

El comando `cpio` (copy in/out) es un formato de archivo antiguo que copia archivos hacia y desde archivos de almacenamiento. Se usa frecuentemente en scripts y empaquetado de software.

**Uso básico**

```fish
cpio [opciones] < [archivo]
```

**Modos principales**

- `-o`, `--create` → Crea archivo (modo output).

- `-i`, `--extract` → Extrae archivo (modo input).

- `-p`, `--pass-through` → Modo pass-through (copia directorios).

- `-t`, `--list` → Lista contenido.

**Opciones**

- `-v`, `--verbose` → Modo detallado.

- `-d`, `--make-directories` → Crea directorios necesarios.

- `-u`, `--unconditional` → Sobrescribe sin preguntar.

- `-m`, `--preserve-modification-time` → Preserva tiempos.

- `-l`, `--link` → Enlaza en lugar de copiar cuando sea posible.

- `-L`, `--dereference` → Sigue enlaces simbólicos.

- `-0`, `--null` → Archivos separados por null (con find -print0).

- `-F`, `--file` → Usa archivo específico.

- `-R`, `--owner` → Especifica propietario.

- `--no-absolute-filenames` → Relativiza rutas absolutas.

**Ejemplos**

```fish
find . -name "*.txt" | cpio -o > archivos.cpio      # Crea cpio con .txt
cpio -i < archivos.cpio                               # Extrae todos
cpio -iv < archivos.cpio                               # Extrae detallado
cpio -it < archivos.cpio                                # Lista contenido
find . -type f | cpio -pdm /directorio/destino          # Copia preservando estructura
find . -depth -print0 | cpio --null -pvd /destino       # Con null (nombres con espacios)
cpio -i "*.txt" < archivos.cpio                          # Extrae solo .txt
```
---

## 131. `zdiff` – Comparar Archivos Comprimidos

El comando `zdiff` compara archivos comprimidos con gzip (.gz) sin necesidad de descomprimirlos primero. Es equivalente a `gzip -dc archivo1.gz | diff - archivo2`.

**Uso básico**

```fish
zdiff [opciones] archivo1.gz [archivo2.gz]
```

**Opciones**

- Acepta las mismas opciones que `diff`.

- Si se omite archivo2, compara archivo1.gz con archivo1 sin .gz.

**Ejemplos**

```fish
zdiff archivo1.txt.gz archivo2.txt.gz               # Compara dos comprimidos
zdiff archivo.txt.gz archivo.txt                      # Comprime con versión sin comprimir
zdiff -i archivo1.txt.gz archivo2.txt.gz               # Ignora mayúsculas
zdiff -b archivo.txt.gz                                 # Compara con archivo.txt (ignora espacios)
```
---

## 132. `zgrep` – Buscar Patrones Dentro de Archivos Comprimidos

El comando `zgrep` busca patrones dentro de archivos comprimidos con gzip (.gz) sin descomprimirlos primero.

**Uso básico**

```fish
zgrep [opciones] patrón [archivo.gz...]
```

**Opciones**

- Acepta las mismas opciones que `grep`.

- `-h` → No muestra nombres de archivo.

- `-l` → Muestra solo nombres de archivos que coinciden.

- `-L` → Muestra solo nombres de archivos que no coinciden.

- `-n` → Muestra números de línea.

- `-i` → Ignora mayúsculas/minúsculas.

- `-v` → Invierte coincidencia.

- `-c` → Cuenta coincidencias.

- `-w` → Palabra completa.

- `-x` → Línea completa.

**Ejemplos**

```fish
zgrep "error" log.txt.gz                            # Busca "error" en log comprimido
zgrep -i "warning" *.gz                               # Ignora mayúsculas en todos .gz
zgrep -n "TODO" codigo.c.gz                            # Con números de línea
zgrep -c "ERROR" app.log.gz                             # Cuenta ocurrencias
zgrep -l "import" *.py.gz                                # Archivos .py.gz con "import"
zgrep -v "debug" sistema.log.gz                           # Líneas sin "debug"
```
---

### Sesión, Energía y Misceláneos

Esta categoría agrupa comandos relacionados con el control de sesiones de usuario, la gestión de energía del sistema y otras utilidades diversas que no encajan en las categorías anteriores.

---

## 133. `shutdown` – Apagar el Sistema

El comando `shutdown` apaga o reinicia el sistema de forma programada y segura, notificando a los usuarios conectados.

**Uso básico**

```fish
shutdown [opciones] [tiempo] [mensaje]
```

**Opciones**

- `-h`, `--halt` → Detiene el sistema (halt).

- `-P`, `--poweroff` → Apaga el sistema (poweroff).

- `-r`, `--reboot` → Reinicia el sistema.

- `-c`, `--cancel` → Cancela un apagado programado.

- `-k`, `--no-wall` → No envía mensaje a usuarios.

- `--no-wall` → No envía mensaje de advertencia.

- `-f`, `--force` → Fuerza apagado (salta fsck).

- `-F`, `--force-fsck` → Fuerza fsck en reinicio.

**Tiempo**

- `now` → Inmediatamente.

- `+m` → En m minutos.

- `hh:mm` → A hora específica (24h).

**Ejemplos**

```fish
shutdown now                                       # Apaga inmediatamente
shutdown -r now                                     # Reinicia inmediatamente
shutdown -h +10 "Mantenimiento en 10 minutos"        # Apaga en 10 minutos con mensaje
shutdown -r 23:30                                     # Reinicia a las 23:30
shutdown -c                                            # Cancela apagado programado
shutdown -P now                                         # Poweroff inmediato
```
---

## 134. `reboot` – Reiniciar el Sistema

El comando `reboot` reinicia el sistema inmediatamente. Es equivalente a `shutdown -r now`.

**Uso básico**

```fish
reboot [opciones]
```

**Opciones**

- `-f`, `--force` → Fuerza reinicio (no llama a shutdown).

- `-p`, `--poweroff` → Apaga en lugar de reiniciar.

- `--halt` → Detiene el sistema.

- `-w`, `--wtmp-only` → Solo escribe en wtmp, no reinicia.

- `-d`, `--no-wtmp` → No escribe en wtmp.

- `-n`, `--no-sync` → No sincroniza discos.

**Ejemplos**

```fish
reboot                                           # Reinicia el sistema
sudo reboot -f                                     # Fuerza reinicio
reboot -p                                            # Apaga (no reinicia)
```
---

## 135. `poweroff` – Apagar el Sistema Inmediatamente

El comando `poweroff` apaga el sistema inmediatamente, cortando la alimentación. Es equivalente a `shutdown -P now`.

**Uso básico**

```fish
poweroff [opciones]
```

**Opciones**

- `-f`, `--force` → Fuerza apagado (no llama a shutdown).

- `-w`, `--wtmp-only` → Solo escribe en wtmp.

- `-d`, `--no-wtmp` → No escribe en wtmp.

- `-n`, `--no-sync` → No sincroniza discos.

- `--halt` → Detiene en lugar de apagar.

**Ejemplos**

```fish
poweroff                                         # Apaga el sistema
sudo poweroff -f                                   # Fuerza apagado
```
---

## 136. `halt` – Detener el Sistema

El comando `halt` detiene el sistema, pero puede no apagar la alimentación (depende del sistema). Es equivalente a `shutdown -h now`.

**Uso básico**

```fish
halt [opciones]
```

**Opciones**

- `-f`, `--force` → Fuerza detención (no llama a shutdown).

- `-p`, `--poweroff` → Apaga después de detener.

- `-w`, `--wtmp-only` → Solo escribe en wtmp.

- `-d`, `--no-wtmp` → No escribe en wtmp.

- `-n`, `--no-sync` → No sincroniza discos.

**Ejemplos**

```fish
halt                                             # Detiene el sistema
halt -p                                            # Detiene y apaga
```
---

## 137. `exit` – Salir del Shell Actual

El comando `exit` termina la sesión actual de shell. Si es el shell principal, cierra la terminal o cierra la sesión.

**Uso básico**

```fish
exit [código]
```

**Opciones**

- `código` → Código de salida (0 éxito, otro error).

**Ejemplos**

```fish
exit                                             # Sale del shell
exit 0                                             # Sale con código 0
exit 1                                              # Sale con error
```
---

## 138. `logout` – Cerrar Sesión de Usuario

El comando `logout` cierra la sesión de un usuario en una shell de login. Similar a `exit` pero solo funciona en shells de login.

**Uso básico**

```fish
logout
```

**Ejemplos**

```fish
logout                                           # Cierra sesión
```
---

## 139. `clear` – Limpiar Pantalla

El comando `clear` limpia la pantalla de la terminal, moviendo el prompt a la esquina superior izquierda.

**Uso básico**

```fish
clear
```

**Opciones**

- `-x` → No limpia scrollback (en algunas versiones).

**Ejemplos**

```fish
clear                                            # Limpia la pantalla
```
---

## 140. `reset` – Reiniciar Terminal

El comando `reset` reinicializa la terminal. Es útil cuando la pantalla se corrompe o muestra caracteres extraños.

**Uso básico**

```fish
reset
```

**Opciones**

- `-q`, `--quiet` → Modo silencioso.

- `-I`, `--no-init` → No inicializa.

- `-k`, `--keep` → Mantiene algunas configuraciones.

**Ejemplos**

```fish
reset                                            # Reinicia la terminal
```

---

