



# Comandos de Administración de Archivos en Linux

La administración de archivos es una tarea común al trabajar con la línea de comandos en Linux. Aquí te presentamos algunos comandos esenciales para gestionar archivos y directorios:

## 1. `ls` – Listar Contenidos de Directorio

El comando `ls` es uno de los más frecuentes en Linux, utilizado para mostrar el contenido de un directorio, incluyendo archivos y subdirectorios.

**Sintaxis:**

```bash
ls [opciones] [directorio]
```

**Opciones útiles:**

- `-l` – Muestra detalles extendidos como permisos, propietario, tamaño y fecha de modificación.
- `-a` – Incluye archivos y directorios ocultos que empiezan con un punto.
- `-R` – Lista de forma recursiva todo el contenido de subdirectorios.
- `-S` – Ordena los resultados por tamaño, comenzando con el más grande.
- `-t` – Ordena por fecha de modificación, mostrando el más reciente primero.

**Ejemplo:**

```bash
ls -l /home/user/documentos
```

Esto mostrará el contenido del directorio `documentos` en un formato detallado.

**Resultado de ejemplo:**

```
total 824
-rwxrwx--- 1 user user    8389 Jul 12 08:53 report.pdf
-rw-r--r-- 1 user user   10231 Jun 30 16:32 presentation.pptx
drwxr-xr-x 2 user user    4096 May 11 09:21 images
-rw-rw-r-- 1 user user     453 Apr 18 13:32 todo.txt
```

## 2. `cd` – Cambiar de Directorio

El comando `cd` te permite navegar entre directorios. Al ejecutarlo sin argumentos, te llevará al directorio de inicio. Puedes especificar una ruta para moverte a una ubicación concreta.

**Sintaxis:**

```bash
cd [directorio]
```

**Ejemplos:**

- `cd /usr/local` – Cambia al directorio `/usr/local`.
- `cd ..` – Regresa al directorio padre.
- `cd ~/pictures` – Cambia al directorio `pictures` en tu directorio de inicio.

## 3. `mkdir` – Crear un Nuevo Directorio

Utiliza `mkdir` para crear un nuevo directorio. Simplemente indica el nombre del directorio que deseas crear.

**Sintaxis:**

```bash
mkdir [opción] <directorio>
```

**Opciones útiles:**

- `-p` – Crea directorios principales de manera recursiva si es necesario.
- `-v` – Muestra detalles de los directorios creados.

**Ejemplo:**

```bash
mkdir -v ~/project/code
```

Esto creará el subdirectorio `code` dentro de `project` en tu directorio de inicio y mostrará un mensaje confirmando la creación.

## 4. `rmdir` – Eliminar Directorio

El comando `rmdir` elimina directorios vacíos. Para eliminar directorios con contenido, utiliza el comando `rm`.

**Sintaxis:**

```bash
rmdir [opciones] <directorio>
```

**Opciones útiles:**

- `-v` – Muestra detalles sobre los directorios eliminados.
- `-p` – Elimina directorios de manera recursiva si están vacíos.

**Ejemplo:**

```bash
rmdir -v ~/project/code
```

Esto eliminará el subdirectorio `code` y mostrará un mensaje detallado.

## 5. `touch` – Crear un Nuevo Archivo Vacío

El comando `touch` crea un archivo vacío o actualiza la marca de tiempo de un archivo existente.

**Sintaxis:**

```bash
touch [opciones] /nombredearchivo
```

**Opciones útiles:**

- `-c` – No crea el archivo si ya existe, evitando sobrescribir archivos existentes.
- `-m` – Actualiza la marca de tiempo de un archivo existente en lugar de crear uno nuevo.

**Ejemplo:**

```bash
touch /home/user/nuevoarchivo.txt
```

Esto crea un archivo vacío llamado `nuevoarchivo.txt` en `/home/user`, o actualiza su marca de tiempo si ya existe.

## 6. `cp` – Copiar Archivos y Directorios

El comando `cp` copia archivos o directorios de una ubicación a otra.

**Sintaxis:**

```bash
cp [opciones] /origen/ /destino/
```

**Opciones útiles:**

- `-r` – Copia directorios de manera recursiva.
- `-i` – Solicita confirmación antes de sobrescribir archivos existentes.
- `-v` – Muestra detalles sobre los archivos copiados.

**Ejemplo:**

```bash
cp -r /home/user/documents /backups/
```

Esto copia el directorio `documents` y su contenido al directorio `/backups/`.

## 7. `mv` – Mover o Renombrar Archivos y Directorios

El comando `mv` se usa para mover o renombrar archivos y directorios. Los archivos se eliminan de la ubicación original después de ser movidos.

**Sintaxis:**

```bash
mv [opciones] /origen/ /destino/
```

**Opciones útiles:**

- `-i` – Solicita confirmación antes de sobrescribir archivos en la ubicación de destino.
- `-v` – Muestra detalles sobre los archivos movidos.

**Ejemplos:**

- Mover un directorio: `mv ~/folder1 /tmp/folder1`
- Renombrar un archivo: `mv folder1 folder2`

## 8. `rm` – Eliminar Archivos y Directorios

El comando `rm` elimina archivos y directorios. Usa `rm` con precaución, ya que los archivos eliminados no se pueden recuperar.

**Sintaxis:**

```bash
rm [opciones] /nombre/
```

**Opciones útiles:**

- `-r` – Elimina directorios de manera recursiva.
- `-f` – Forza la eliminación sin solicitar confirmación.
- `-i` – Solicita confirmación antes de eliminar cada archivo o directorio.

**Ejemplo:**

```bash
rm -rf temp
```

Esto elimina de forma recursiva el directorio `temp` y todo su contenido, sin pedir confirmación.

## 9. `find` – Buscar Archivos en una Jerarquía de Directorios

El comando `find` busca archivos dentro de directorios según criterios específicos.

**Sintaxis:**

```bash
find [ruta] [criterio]
```

**Criterios útiles:**

- `-type f` – Busca solo archivos.
- `-mtime +30` – Busca archivos modificados hace más de 30 días.
- `-user jane` – Busca archivos pertenecientes al usuario `jane`.

**Ejemplo:**

```bash
find . -type f -mtime +30
```

Esto encuentra todos los archivos regulares mayores de 30 días en el directorio actual.

## 10. `du` – Estimar el Uso del Espacio de un Archivo

El comando `du` estima el uso del espacio en disco para un directorio.

**Sintaxis:**

```bash
du [opciones] [ruta]
```

**Opciones útiles:**

- `-h` – Muestra tamaños en un formato legible (por ejemplo, K para kilobytes).
- `-s` – Muestra solo el tamaño total del directorio.
- `-a` – Muestra tamaños individuales de archivos y subdirectorios.

**Ejemplo:**

```bash
du -sh pictures
```

Esto muestra el tamaño total del directorio `pictures` en un formato legible.

## Comandos de Linux para Búsqueda y Filtros

A continuación, te mostramos comandos para buscar, filtrar y manipular texto directamente desde la línea de comandos de Linux.

## 11. `grep` – Buscar Texto Usando Patrones

El comando `grep` busca patrones de texto dentro de archivos o salida, imprimiendo las líneas que coinciden con el patrón.

**Sintaxis:**

```bash
grep [opciones] patrón [archivos]
```

**Opciones útiles:**

- `-i` – Ignora mayúsculas y minúsculas.
- `-R` – Busca de forma recursiva en subdirectorios.
- `-c` – Muestra solo el conteo de líneas coincidentes.
- `-v` – Muestra las líneas que no coinciden con el patrón.

**Ejemplo:**

```bash
grep -i "error" /var/log/syslog
```

Esto busca la palabra "error" en `syslog`, ignorando la diferencia entre mayúsculas y minúsculas.

## 12. `awk` – Escaneo de Patrones y Procesamiento de Lenguaje

`awk` permite procesar texto basado en patrones y acciones. Opera línea por línea, dividiendo cada línea en campos.

**Sintaxis:**

```bash
awk 'pattern { acción }' archivo
```

**Ejemplo:**

```bash
awk '/error/ {print $1}' /var/log/syslog
```

Esto imprime el primer campo de cada línea que contiene "error".



## 13. `sed` – Editor de Flujos

`sed` es una herramienta de edición de texto que permite realizar transformaciones en un flujo de texto o archivos.

**Sintaxis:**

```bash
sed 'expresión' archivo
```

**Ejemplo:**

```bash
sed 's/error/ERROR/g' /var/log/syslog
```

Esto reemplaza todas las apariciones de "error" por "ERROR" en el archivo `syslog`.


## 14. `sort` – Ordenar Líneas de Archivos de Texto

Cuando trabajas con grandes volúmenes de texto o datos, ordenar la información puede facilitar la gestión y análisis. El comando `sort` organiza las líneas de un archivo de texto en orden alfabético o numérico.

**Sintaxis básica:**

```bash
sort [opciones] [archivo]
```

**Opciones útiles:**

- `-n` – Ordena numéricamente en lugar de alfabéticamente.
- `-r` – Invierte el orden de clasificación.
- `-k` – Ordena según un campo o columna específica.

**Ejemplo:**

```bash
sort -n notas.txt
```

Esto ordenará el contenido de `notas.txt` numéricamente. El comando `sort` es esencial para organizar datos y hacer que la información sea más comprensible.

## 15. `uniq` – Filtrar Líneas Repetidas

El comando `uniq` elimina las líneas duplicadas adyacentes en la entrada. Suele usarse junto con `sort` para eliminar duplicados después de ordenar.

**Sintaxis básica:**

```bash
uniq [opciones] [entrada]
```

**Opciones útiles:**

- `-c` – Muestra el recuento de ocurrencias de cada línea.
- `-d` – Muestra solo las líneas duplicadas, no las únicas.

**Ejemplo:**

```bash
sort datos.txt | uniq
```

Esto eliminará las líneas duplicadas en `datos.txt` después de ordenarlas. `uniq` te permite controlar qué líneas se filtran o muestran.

## 16. `diff` – Comparar Archivos Línea por Línea

El comando `diff` compara dos archivos línea por línea e imprime las diferencias entre ellos. Es útil para ver cambios entre versiones de archivos.

**Sintaxis:**

```bash
diff [opciones] archivo1 archivo2
```

**Opciones útiles:**

- `-b` – Ignora cambios en espacios en blanco.
- `-B` – Muestra diferencias de línea, resaltando los cambios.
- `-u` – Muestra diferencias con tres líneas de contexto.

**Ejemplo:**

```bash
diff original.txt actualizado.txt
```

Esto mostrará las diferencias entre `original.txt` y `actualizado.txt`. `diff` es esencial para comparar versiones de documentos o código fuente.

## 17. `wc` – Contar Líneas, Palabras y Bytes

El comando `wc` (word count) proporciona el conteo de líneas, palabras y bytes en un archivo.

**Sintaxis:**

```bash
wc [opciones] [archivo]
```

**Opciones útiles:**

- `-l` – Muestra solo el conteo de líneas.
- `-w` – Muestra solo el conteo de palabras.
- `-c` – Muestra solo el conteo de bytes.

**Ejemplo:**

```bash
wc reporte.txt
```

Este comando imprimirá el número de líneas, palabras y bytes en `reporte.txt`.

## Comandos de Redirección en Linux

Los comandos de redirección permiten controlar las fuentes de entrada y los resultados en Linux, facilitando la manipulación de datos y resultados de comandos.

## 18. `>` – Redirigir el Resultado Estándar

El operador `>` redirige el flujo de resultado estándar de un comando a un archivo, sobrescribiendo cualquier contenido existente.

**Ejemplo:**

```bash
ls -l /home > homelist.txt
```

Esto ejecuta `ls -l` para listar el contenido del directorio `/home` y guarda el resultado en `homelist.txt`, sobrescribiendo su contenido anterior.

## 19. `>>` – Anexar Resultado Estándar

El operador `>>` añade el resultado estándar de un comando a un archivo sin sobrescribir el contenido existente.

**Ejemplo:**

```bash
tail /var/log/syslog >> logfile.txt
```

Esto añade las últimas 10 líneas del archivo de registro `syslog` al final de `logfile.txt`, conservando el contenido previo.

## 20. `<` – Redirigir la Entrada Estándar

El operador `<` dirige el contenido de un archivo como entrada estándar a un comando en lugar de tomar la entrada desde el teclado.

**Ejemplo:**

```bash
wc -l < miarchivo.txt
```

Esto proporciona el contenido de `miarchivo.txt` al comando `wc`, que contará las líneas del archivo.

## 21. `|` – Canalizar el Resultado a Otro Comando

El operador de tubería `|` envía el resultado de un comando como entrada a otro comando, permitiendo encadenar comandos.

**Ejemplo:**

```bash
ls -l | less
```

Esto canaliza el resultado de `ls -l` al comando `less`, que permite visualizar el contenido de forma desplazable.

## 22. `tee` – Leer y Escribir en Varios Destinos

El comando `tee` lee de la entrada estándar y escribe tanto en la salida estándar como en un archivo.

**Ejemplo:**

```bash
cat archivo.txt | tee copia.txt
```

Esto muestra el contenido de `archivo.txt` en la terminal y lo guarda simultáneamente en `copia.txt`.

## Comandos de Archivado

Los comandos de archivado permiten agrupar varios archivos y directorios en archivos comprimidos, facilitando su almacenamiento y transporte.

## 23. `tar` – Crear y Extraer Archivos Tar

El comando `tar` agrupa varios archivos y directorios en un solo archivo .tar, que puede ser comprimido con otros formatos como gzip.

**Sintaxis:**

```bash
tar [opciones] archivo
```

**Opciones útiles:**

- `-c` – Crea un nuevo archivo .tar.
- `-x` – Extrae archivos de un archivo .tar.
- `-f` – Especifica el nombre del archivo.
- `-v` – Muestra detalles del proceso.
- `-z` – Comprime o descomprime con gzip.

**Ejemplo:**

```bash
tar -cvzf images.tar.gz /home/user/images
```

Esto crea un archivo comprimido `images.tar.gz` que contiene la carpeta `/home/user/images`.

## 24. `gzip` – Comprimir o Expandir Archivos

El comando `gzip` comprime archivos usando el algoritmo LZ77, generando archivos con extensión .gz.

**Sintaxis:**

```bash
gzip [opciones] archivo
```

**Opciones útiles:**

- `-c` – Escribe el resultado en stdout en lugar de un archivo.
- `-d` – Descomprime un archivo.
- `-r` – Comprime directorios de manera recursiva.

**Ejemplo:**

```bash
gzip -cr documents/
```

Esto comprime recursivamente la carpeta `documents` y muestra el resultado en stdout.


## 25. `gunzip` – Descomprimir Archivos

El comando `gunzip` se utiliza para descomprimir archivos con la extensión `.gz`.

**Sintaxis:**

```bash
gunzip archivo.gz
```

**Ejemplo:**

```bash
gunzip documentos.tar.gz
```

Este comando descomprimirá `documentos.tar.gz`, devolviendo el archivo original sin comprimir.

## 26. `zip` – Empacar y Comprimir Archivos

El comando `zip` crea archivos `.zip` que contienen archivos comprimidos. Es útil para empaquetar varios archivos en un solo archivo comprimido.

**Sintaxis:**

```bash
zip [opciones] archivo.zip nombres-de-archivos
```

**Opciones útiles:**

- `-r` – Comprimir un directorio de forma recursiva.
- `-e` – Encriptar el archivo con una contraseña.

**Ejemplo:**

```bash
zip -re imagenes.zip fotos
```

Esto comprimirá y encriptará la carpeta `fotos` en un archivo `imagenes.zip`.

## 27. `unzip` – Extraer Archivos de Archivos ZIP

El comando `unzip` descomprime archivos `.zip`, extrayendo su contenido al directorio actual.

**Sintaxis:**

```bash
unzip archivo.zip
```

**Ejemplo:**

```bash
unzip imagenes.zip
```

Este comando extraerá todos los archivos contenidos en `imagenes.zip` al directorio actual.

## Comandos para Transferencia de Archivos

Estos comandos permiten mover archivos entre sistemas en una red, facilitando la transferencia segura y eficiente.

## 28. `scp` – Copiar Archivos de Forma Segura Entre Hosts

El comando `scp` (secure copy) copia archivos entre hosts a través de SSH, asegurando que los datos se transfieran de forma cifrada.

**Sintaxis:**

```bash
scp origen usuario@host:destino
```

**Ejemplo:**

```bash
scp imagen.jpg usuario@servidor:/uploads/
```

Esto copiará `imagen.jpg` al directorio `/uploads/` en el servidor remoto, usando `usuario`.

## 29. `rsync` – Sincronizar Archivos Entre Hosts

El comando `rsync` sincroniza archivos entre dos ubicaciones, optimizando la transferencia de datos con codificación delta para eficiencia.

**Sintaxis:**

```bash
rsync [opciones] /origen /destino
```

**Ejemplo:**

```bash
rsync -ahv ~/documentos usuario@servidor:/backups/
```

Este comando sincroniza recursivamente la carpeta `documentos` con `servidor:/backups/`, mostrando detalles del proceso.

**Opciones útiles:**

- `-a` – Modo archivo, conserva permisos, tiempos, etc.
- `-h` – Salida legible por humanos.
- `-v` – Muestra detalles del proceso.

## 30. `sftp` – Programa de Transferencia de Archivos Segura

El programa `sftp` proporciona una interfaz interactiva para transferir archivos sobre SSH, similar a FTP pero cifrado.

**Sintaxis básica:**

```bash
sftp usuario@host
```

**Comandos comunes:**

- `get archivo-remoto archivo-local` – Descarga un archivo del servidor remoto.
- `put archivo-local archivo-remoto` – Carga un archivo al servidor remoto.

**Ejemplo:**

```bash
sftp usuario@servidor
get archivo-remoto.txt archivo-local.txt
```

Esto descargará `archivo-remoto.txt` desde el servidor remoto a `archivo-local.txt` en el sistema local.

## 31. `wget` – Recuperar Archivos de la Web

El comando `wget` descarga archivos desde servidores web usando protocolos HTTP, HTTPS y FTP.

**Sintaxis:**

```bash
wget [opciones] URL
```

**Ejemplo:**

```bash
wget https://ejemplo.com/archivo.iso
```

Este comando descarga el archivo `archivo.iso` desde `https://ejemplo.com`.

**Opciones útiles:**

- `-c` – Reanudar una descarga interrumpida.
- `-r` – Descargar de forma recursiva.
- `-O` – Especificar el nombre del archivo de salida.

## 32. `curl` – Transferir Datos Desde o Hacia un Servidor

El comando `curl` transfiere datos a través de diversas redes y protocolos, incluyendo REST, HTTP y FTP.

**Sintaxis:**

```bash
curl [opciones] URL
```

**Ejemplo:**

```bash
curl -L https://ejemplo.com
```

Este comando obtiene datos de `https://ejemplo.com` y los muestra en la terminal.

**Opciones útiles:**

- `-o` – Guarda la salida en un archivo.
- `-I` – Muestra solo los encabezados de respuesta.
- `-L` – Sigue redirecciones.

## Comandos de Permisos de Archivos

Estos comandos permiten ajustar los permisos y la propiedad de archivos y directorios, controlando el acceso y la seguridad.

## 33. `chmod` – Cambiar Modos de Archivo o Permisos de Acceso

El comando `chmod` modifica los permisos de acceso de archivos y directorios, determinando quién puede leer, escribir o ejecutar el archivo.

**Sintaxis básica:**

```bash
chmod [modo] archivo
```

**Modo numérico:**

- `7` – Leer, escribir y ejecutar (rwx).
- `6` – Leer y escribir (rw-).
- `4` – Solo lectura (r--).
- `0` – Sin permisos (---).

**Ejemplo:**

```bash
chmod 755 archivo.txt
```

Esto establece los permisos de `archivo.txt` a `rwxr-xr-x`.

**Modo simbólico:**

```bash
chmod g+w archivo.txt
```

Esto añade permisos de escritura al grupo del archivo.

## 34. `chown` – Cambiar Propietario y Grupo de Archivos

El comando `chown` cambia la propiedad de un archivo o directorio, incluyendo el usuario y el grupo al que pertenece.

**Sintaxis:**

```bash
chown usuario:grupo archivo
```

**Ejemplo:**

```bash
chown juan:desarrolladores archivo.txt
```

Este comando establece al usuario `juan` como el propietario y al grupo `desarrolladores` como el grupo del archivo `archivo.txt`.


## 35. `umask` – Establecer Permisos Predeterminados para Archivos

El comando `umask` controla los permisos predeterminados para archivos y directorios recién creados. Utiliza una máscara octal que se resta de 666 para archivos y de 777 para directorios, determinando los permisos iniciales.

**Sintaxis:**

```bash
umask máscara
```

**Ejemplo:**

```bash
umask 007
```

Con esta configuración, los archivos nuevos tendrán permisos 750 (rwxr-x---) y los directorios nuevos 700 (rwx------). Esto ayuda a establecer permisos predeterminados sin tener que ajustarlos manualmente después de la creación.

## Comandos de Administración de Procesos

Estos comandos son útiles para monitorear y controlar los procesos en tu sistema Linux.

## 36. `ps` – Informe de Procesos Actuales

El comando `ps` proporciona una instantánea de los procesos en ejecución, mostrando detalles como PID, TTY, estado y uso de recursos.

**Sintaxis:**

```bash
ps [opciones]
```

**Ejemplo:**

```bash
ps aux
```

Esto muestra todos los procesos en ejecución para todos los usuarios, incluyendo información detallada sobre uso de CPU y memoria.

**Opciones útiles:**

- `aux` – Muestra procesos para todos los usuarios.
- `--forest` – Muestra la jerarquía de procesos principal/secundario en un formato de árbol.

## 37. `top` – Mostrar Procesos en Tiempo Real

El comando `top` muestra información dinámica en tiempo real sobre los procesos, incluyendo el uso de CPU y memoria, tiempo de actividad y más.

**Sintaxis:**

```bash
top [opciones]
```

**Ejemplo:**

```bash
top -u mysql
```

Este comando muestra los procesos en ejecución del usuario `mysql`, ayudando a identificar procesos que consumen muchos recursos.

## 38. `htop` – Visor de Procesos Interactivo

El comando `htop` es una versión mejorada de `top`, ofreciendo una interfaz interactiva con gráficos para visualizar el uso de CPU, memoria y swap. Permite ordenar, filtrar y gestionar procesos de manera más intuitiva.

**Uso:**

```bash
htop
```

`htop` proporciona una vista colorida y fácil de usar para la gestión de procesos, soportando desplazamiento y navegación con el mouse.

## 39. `kill` – Enviar Señales a un Proceso

El comando `kill` envía señales a los procesos para terminarlos o controlarlos. Las señales pueden ser utilizadas para detener un proceso de manera ordenada.

**Sintaxis:**

```bash
kill [señal] PID
```

**Ejemplo:**

```bash
kill -15 12345
```

Esto envía la señal SIGTERM (15) al proceso con PID 12345 para terminarlo de manera ordenada.

## 40. `pkill` – Enviar Señales a Procesos Basados en el Nombre

El comando `pkill` permite terminar procesos basados en su nombre, simplificando la gestión sin necesidad de conocer el PID.

**Sintaxis:**

```bash
pkill [opciones] nombre-del-proceso
```

**Ejemplo:**

```bash
pkill -9 firefox
```

Esto envía la señal SIGKILL (9) a todos los procesos llamados `firefox`, forzando su terminación.

## 41. `nohup` – Ejecutar Comandos Inmunes a Desconexiones

El comando `nohup` ejecuta un comando de forma que continúe en ejecución incluso si cierras sesión o te desconectas.

**Sintaxis:**

```bash
nohup comando &
```

**Ejemplo:**

```bash
nohup python script.py &
```

Esto ejecuta `script.py` en segundo plano, manteniéndolo en ejecución independientemente de la sesión del usuario.

---

# Comandos de Monitoreo de Rendimiento

Estos comandos proporcionan información sobre el rendimiento del sistema, incluyendo el uso de recursos y la actividad de procesos.

## 42. `vmstat` – Informar Estadísticas de Memoria Virtual

El comando `vmstat` proporciona informes sobre memoria, swap, I/O y CPU, ayudando a analizar el rendimiento del sistema.

**Sintaxis:**

```bash
vmstat [opciones] [intervalo]
```

**Ejemplo:**

```bash
vmstat 5
```

Este comando muestra estadísticas de memoria y CPU cada 5 segundos.

**Opciones útiles:**

- `-a` – Muestra memoria activa e inactiva.
- `-s` – Muestra estadísticas de memoria y contadores de eventos.
- `-S` – Resultado en KB en lugar de bloques.

## 43. `iostat` – Informar Estadísticas de CPU e I/O

El comando `iostat` muestra estadísticas de CPU e I/O de disco, incluyendo rendimiento de lectura/escritura y uso de la CPU.

**Sintaxis:**

```bash
iostat [opciones] [intervalo]
```

**Ejemplo:**

```bash
iostat -d -p sda 5
```

Este comando muestra estadísticas detalladas de I/O para el dispositivo `sda` cada 5 segundos.

**Opciones útiles:**

- `-c` – Muestra estadísticas de utilización de la CPU.
- `-d` – Muestra estadísticas detalladas por dispositivo.
- `-x` – Muestra estadísticas extendidas como tiempos de servicio y recuentos de espera.

## 44. `free` – Mostrar la Cantidad de Memoria Libre y Utilizada

El comando `free` muestra la memoria física y swap libre y utilizada en el sistema.

**Sintaxis:**

```bash
free [opciones]
```

**Ejemplo:**

```bash
free -h
```

Este comando imprime estadísticas de memoria en un formato legible para humanos (GB, MB).

**Opciones útiles:**

- `-b` – Muestra el resultado en bytes.
- `-k` – Muestra el resultado en KB.
- `-m` – Muestra el resultado en MB.
- `-h` – Muestra el resultado en un formato legible para humanos.


## 45. `df` – Informar del Uso del Espacio en Disco

El comando `df` muestra la utilización del espacio en disco para los sistemas de archivos montados, incluyendo el espacio total, usado y disponible.

**Sintaxis:**

```bash
df [opciones]
```

**Ejemplo:**

```bash
df -h
```

Este comando muestra el uso del espacio en disco en un formato legible para humanos (GB, MB). Si se ejecuta sin opciones, `df` muestra el espacio en bloques de 1K.

**Opciones útiles:**

- `-h` – Muestra los tamaños en un formato legible para humanos (GB, MB, etc.).

## 46. `sar` – Recopilar e Informar Actividad del Sistema

El comando `sar` recopila y reporta datos sobre la actividad del sistema, incluyendo el uso de CPU, memoria, I/O, y más. Es útil para análisis de rendimiento a lo largo del tiempo.

**Sintaxis:**

```bash
sar [opciones] [intervalo] [número-de-muestras]
```

**Ejemplo:**

```bash
sar -u 5 60
```

Este comando muestra el uso de la CPU cada 5 segundos durante un total de 60 muestras.

**Opciones útiles:**

- `-u` – Muestra la utilización de la CPU.
- `5` – Intervalo en segundos entre cada muestra.
- `60` – Número total de muestras.

---

# Comandos de Administración de Usuarios y Grupos

Estos comandos te permiten gestionar cuentas de usuario y grupos en sistemas Linux.

## 47. `useradd` – Crear un Nuevo Usuario

El comando `useradd` crea una nueva cuenta de usuario y un directorio de inicio asociado, configurando UID, grupo y shell.

**Sintaxis:**

```bash
useradd [opciones] nombre-de-usuario
```

**Ejemplo:**

```bash
useradd -m juan
```

**Opciones útiles:**

- `-m` – Crea un directorio de inicio para el nuevo usuario.
- `-g` – Especifica el grupo primario del usuario.
- `-s` – Establece el shell de inicio de sesión.

## 48. `usermod` – Modificar una Cuenta de Usuario

El comando `usermod` cambia las configuraciones de una cuenta de usuario existente, como el grupo, shell, y más.

**Sintaxis:**

```bash
usermod [opciones] nombre-de-usuario
```

**Ejemplo:**

```bash
usermod -aG developers juan
```

Esto añade al usuario `juan` al grupo `developers`.

**Opciones útiles:**

- `-aG` – Añade al usuario a un grupo adicional sin eliminarlo de otros grupos.

## 49. `userdel` – Eliminar una Cuenta de Usuario

El comando `userdel` elimina una cuenta de usuario y, opcionalmente, su directorio de inicio y buzón de correo.

**Sintaxis:**

```bash
userdel [opciones] nombre-de-usuario
```

**Ejemplo:**

```bash
userdel -rf juan
```

**Opciones útiles:**

- `-r` – Elimina el directorio de inicio del usuario.
- `-f` – Fuerza la eliminación incluso si el usuario está conectado.

## 50. `groupadd` – Añadir un Grupo

El comando `groupadd` crea un nuevo grupo de usuarios, que puede ser usado para gestionar permisos y acceso.

**Sintaxis:**

```bash
groupadd [opciones] nombre-de-grupo
```

**Ejemplo:**

```bash
groupadd -r sysadmin
```

**Opciones útiles:**

- `-r` – Crea un grupo del sistema.
- `-g` – Especifica el GID del nuevo grupo.

## 51. `passwd` – Actualizar Contraseñas de Usuario

El comando `passwd` establece o cambia la contraseña de un usuario.

**Sintaxis:**

```bash
passwd [nombre-de-usuario]
```

**Ejemplo:**

```bash
passwd juan
```

Esto solicita una nueva contraseña para el usuario `juan`.

---

# Comandos de Red

Estos comandos te ayudan a monitorear y solucionar problemas relacionados con la red.

## 52. `ping` – Enviar Paquetes ICMP ECHO_REQUEST

El comando `ping` verifica la conectividad a un host remoto enviando paquetes de solicitud de eco ICMP.

**Sintaxis:**

```bash
ping [opciones] destino
```

**Ejemplo:**

```bash
ping google.com
```

**Opciones útiles:**

- `-c [count]` – Limita el número de paquetes enviados.
- `-i [interval]` – Establece el intervalo entre pings en segundos.

## 53. `ifconfig` – Configurar Interfaces de Red

El comando `ifconfig` muestra y configura la información de las interfaces de red, como direcciones IP, máscaras de red, y más.

**Sintaxis:**

```bash
ifconfig [interfaz] [opciones]
```

**Ejemplo:**

```bash
ifconfig
```

Esto muestra todas las interfaces de red disponibles y sus configuraciones.

**Opciones útiles:**

- `up` – Activa la interfaz de red.
- `down` – Desactiva la interfaz de red.

## 54. `netstat` – Estadísticas de Red

El comando `netstat` muestra estadísticas de red, incluyendo conexiones activas, tablas de enrutamiento y más.

**Sintaxis:**

```bash
netstat [opciones]
```

**Ejemplo:**

```bash
netstat -pt tcp
```

Este comando muestra todas las conexiones TCP activas y los procesos asociados.

## 55. `ss` – Estadísticas de Socket

El comando `ss` proporciona información detallada sobre sockets de red, similar a `netstat`, pero con mejor rendimiento.

**Sintaxis:**

```bash
ss [opciones]
```

**Ejemplo:**

```bash
ss -t -a
```

Esto muestra todos los sockets TCP abiertos.

**Opciones útiles:**

- `-t` – Muestra sockets TCP.
- `-a` – Muestra todos los sockets.


## 56. `traceroute` – Rastrear Ruta a un Host

El comando `traceroute` muestra la ruta que siguen los paquetes para llegar a un host de red, indicando cada salto y el tiempo de tránsito.

**Sintaxis:**

```bash
traceroute [opciones] destino
```

**Ejemplo:**

```bash
traceroute google.com
```

Esto traza la ruta hacia `google.com` y muestra cada salto en el camino junto con los tiempos de respuesta.

**Opciones útiles:**

- `-m [max_ttl]` – Establece el número máximo de saltos.

## 57. `dig` – DNS Lookup

El comando `dig` realiza búsquedas DNS y devuelve información detallada sobre los registros DNS para un dominio.

**Sintaxis:**

```bash
dig [opciones] dominio
```

**Ejemplo:**

```bash
dig google.com
```

Esto consulta los servidores DNS para obtener registros relacionados con `google.com`.

**Opciones útiles:**

- `+short` – Muestra la respuesta en un formato resumido.
- `+noall +answer` – Muestra solo la sección de respuesta.

## 58. `nslookup` – Consulta a Servidores de Nombres de Internet de Forma Interactiva

El comando `nslookup` realiza consultas DNS de forma interactiva, permitiendo buscar nombres de host, direcciones IP inversas, y otros registros DNS.

**Sintaxis:**

```bash
nslookup [opciones] [dominio]
```

**Ejemplo interactivo:**

```bash
nslookup
> server 8.8.8.8
> set type=A
> stackoverflow.com
```

Esto consulta el registro A para `stackoverflow.com` usando el servidor DNS 8.8.8.8.

**Opciones útiles:**

- `set type=MX` – Consulta registros MX para servidores de correo.
- `server [DNS]` – Cambia el servidor DNS usado para la consulta.

---

# Comandos de Gestión de Red

## 59. `iptables` – Filtrado de Paquetes IPv4 y NAT

El comando `iptables` permite configurar reglas de firewall en Linux para filtrar y procesar paquetes de red. Puedes establecer políticas y reglas para el manejo de conexiones y tráfico.

**Sintaxis:**

```bash
iptables [opciones]
```

**Ejemplo:**

```bash
iptables -A INPUT -s 192.168.1.10 -j DROP
```

Esto bloquea todo el tráfico entrante desde la IP `192.168.1.10`.

**Opciones útiles:**

- `-A [CHAIN]` – Añade una regla a la cadena especificada (INPUT, FORWARD, OUTPUT).
- `-D [CHAIN]` – Elimina una regla de la cadena especificada.

## 60. `ip` – Gestión de Dispositivos y Enrutamiento de Red

El comando `ip` gestiona dispositivos de red, direcciones IP y enrutamiento. Es una herramienta moderna para manejar configuraciones de red en Linux.

**Sintaxis:**

```bash
ip [opciones] [subcomando]
```

**Ejemplo:**

```bash
ip link show
```

Esto muestra todas las interfaces de red y sus detalles.

**Opciones útiles:**

- `ip addr show` – Muestra direcciones IP y detalles de las interfaces.
- `ip route show` – Muestra la tabla de enrutamiento.

---

# Comandos de Administración de Paquetes

Estos comandos permiten instalar, actualizar y eliminar software en distribuciones de Linux.

## 61. `apt` – Administrador de Paquetes de Debian/Ubuntu

El comando `apt` gestiona paquetes en sistemas Debian/Ubuntu. Permite realizar operaciones como instalación, actualización y eliminación de paquetes.

**Sintaxis:**

```bash
apt [opciones] [comando]
```

**Ejemplo:**

```bash
apt update
```

Esto actualiza la lista de paquetes disponibles.

```bash
apt install nginx
```

Esto instala el paquete `nginx`.

**Opciones útiles:**

- `apt upgrade` – Actualiza los paquetes instalados a sus versiones más recientes.

## 62. `pacman` – Gestor de Paquetes de Arch Linux

El comando `pacman` gestiona paquetes en Arch Linux desde el repositorio de Arch User Repository (AUR). Permite instalar, actualizar y eliminar paquetes.

**Sintaxis:**

```bash
pacman [opciones] [comando]
```

**Ejemplo:**

```bash
pacman -S nmap
```

Esto instala el paquete `nmap`.

```bash
pacman -Syu
```

Esto sincroniza con los repositorios y actualiza todos los paquetes.

**Opciones útiles:**

- `-R` – Elimina un paquete.
- `-Q` – Muestra información sobre paquetes instalados.

## 63. `dnf` – Gestor de Paquetes de Fedora

El comando `dnf` gestiona paquetes en Fedora y otras distribuciones basadas en RPM. Reemplaza a `yum` con una interfaz más moderna.

**Sintaxis:**

```bash
dnf [opciones] [comando]
```

**Ejemplo:**

```bash
dnf install util-linux
```

Esto instala el paquete `util-linux`.

```bash
dnf upgrade
```

Esto actualiza todos los paquetes instalados a las versiones más recientes.

**Opciones útiles:**

- `dnf remove` – Elimina un paquete.

## 64. `yum` – Gestor de Paquetes de Red Hat

El comando `yum` gestiona paquetes en distribuciones basadas en Red Hat, como RHEL y CentOS. Utiliza repositorios RPM para instalar y actualizar paquetes.

**Sintaxis:**

```bash
yum [opciones] [comando]
```

**Ejemplo:**

```bash
yum update
```

Esto actualiza todos los paquetes instalados.

```bash
yum install httpd
```

Esto instala el paquete `httpd` (Apache).

**Opciones útiles:**

- `yum remove` – Elimina un paquete.
- `yum search` – Busca paquetes disponibles.


## 65. `zypper` – Gestor de Paquetes de openSUSE

`zypper` es el gestor de paquetes utilizado en openSUSE y SUSE Linux. Permite la instalación, actualización y eliminación de paquetes, así como la gestión de repositorios.

**Ejemplos:**

- **Actualizar metadatos de repositorios:**

  ```bash
  zypper refresh
  ```

- **Instalar un paquete:**

  ```bash
  zypper install python
  ```

- **Actualizar todos los paquetes instalados:**

  ```bash
  zypper update
  ```

- **Eliminar un paquete:**

  ```bash
  zypper remove [paquete]
  ```

---

## 66. `flatpak` – Gestor de Paquetes de Aplicaciones Flatpak

`flatpak` permite gestionar aplicaciones empaquetadas en un entorno aislado conocido como sandbox. Esto facilita la distribución y ejecución de aplicaciones en diferentes distribuciones de Linux.

**Ejemplos:**

- **Instalar una aplicación desde Flathub:**

  ```bash
  flatpak install flathub org.libreoffice.LibreOffice
  ```

- **Ejecutar una aplicación instalada:**

  ```bash
  flatpak run org.libreoffice.LibreOffice
  ```

- **Actualizar aplicaciones Flatpak:**

  ```bash
  flatpak update
  ```

- **Listar aplicaciones instaladas:**

  ```bash
  flatpak list
  ```

---

## 67. `appimage` – Administrador de Paquetes de Aplicaciones AppImage

AppImage permite ejecutar aplicaciones empaquetadas en un formato que incluye todas las dependencias necesarias para su ejecución.

**Ejemplos:**

- **Hacer que un archivo AppImage sea ejecutable:**

  ```bash
  chmod +x myapp.AppImage
  ```

- **Ejecutar la aplicación:**

  ```bash
  ./myapp.AppImage
  ```

---

## 68. `snap` – Administrador de Paquetes de Aplicaciones Snappy

`snap` gestiona paquetes en contenedores, conocidos como snaps, que están diseñados para ser independientes de la distribución de Linux.

**Ejemplos:**

- **Instalar un paquete:**

  ```bash
  snap install vlc
  ```

- **Ejecutar una aplicación instalada:**

  ```bash
  snap run vlc
  ```

- **Listar paquetes instalados:**

  ```bash
  snap list
  ```

- **Actualizar todos los snaps instalados:**

  ```bash
  snap refresh
  ```

---

## Comandos de Información de Sistema

Estos comandos proporcionan información sobre el sistema, incluyendo el hardware, el kernel y los detalles del sistema operativo.

### 69. `uname` – Imprimir Información del Sistema

`uname` muestra información sobre el sistema operativo y el kernel.

**Ejemplos:**

- **Imprimir toda la información disponible:**

  ```bash
  uname -a
  ```

- **Imprimir solo la versión del kernel:**

  ```bash
  uname -r
  ```

### 70. `hostname` – Mostrar o Configurar el Nombre de Host del Sistema

`hostname` muestra o configura el nombre de host del sistema Linux.

**Ejemplos:**

- **Mostrar el nombre de host actual:**

  ```bash
  hostname
  ```

- **Cambiar el nombre de host:**

  ```bash
  hostname UbuntuServer
  ```

### 71. `uptime` – Tiempo que el Sistema ha Estado Encendido

`uptime` muestra cuánto tiempo ha estado el sistema encendido desde el último reinicio.

**Ejemplo:**

```bash
uptime
```

Salida de ejemplo:

```
23:51:26 up 2 days, 4:12, 1 user, load average: 0.00, 0.01, 0.05
```

### 72. `whoami` – Imprimir ID de Usuario Activo

`whoami` muestra el nombre de usuario del usuario que está actualmente conectado.

**Ejemplo:**

```bash
whoami
```

### 73. `id` – Imprimir Identificadores de Usuario y Grupo Reales y Efectivos

`id` proporciona información sobre los IDs de usuario y grupo del usuario actual.

**Ejemplo:**

```bash
id
```

Salida de ejemplo:

```
uid=1000(john) gid=1000(john) groups=1000(john),10(wheel),998(developers)
```

### 74. `lscpu` – Mostrar Información de Arquitectura de la CPU

`lscpu` muestra detalles sobre la arquitectura de la CPU.

**Ejemplo:**

```bash
lscpu
```

Salida de ejemplo:

```
Architecture:        x86_64
CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              16
On-line CPU(s) list: 0-15
```

### 75. `lsblk` – Listar Dispositivos de Bloques

`lsblk` muestra información sobre los dispositivos de bloques disponibles, como discos y particiones.

**Ejemplo:**

```bash
lsblk
```

Salida de ejemplo:

```
NAME    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda       8:0    0   1.8T  0 disk  
|-sda1    8:1    0   512M  0 part  /boot
|-sda2    8:2    0    16M  0 part  
`-sda5    8:5    0   1.8T  0 part  
  `-lvm1 254:0    0   1.8T  0 lvm   /
```


## 76. `lsmod` – Mostrar el Estado de los Módulos en el Kernel de Linux

`lsmod` muestra los módulos del kernel que están cargados actualmente, útiles para identificar controladores y otros módulos activos.

**Ejemplo:**

```bash
lsmod
```

---

## 77. `dmesg` – Imprimir o Controlar el Buffer de Anillo del Kernel

`dmesg` muestra mensajes del buffer de anillo del kernel, que incluyen eventos del sistema y errores del kernel.

**Ejemplo:**

- **Buscar errores específicos:**

  ```bash
  dmesg | grep -i error
  ```

---

## Comandos de Administración de Sistema

### 78. `sudo` – Ejecutar un Comando Como Otro Usuario

`sudo` permite ejecutar comandos con privilegios elevados, típicamente como superusuario.

**Ejemplo:**

```bash
sudo adduser bob
```

### 79. `su` – Cambiar ID de Usuario o Convertirse en Superusuario

`su` cambia al usuario especificado o al superusuario si se usa sin argumentos.

**Ejemplo:**

```bash
su bob
```

### 80. `shutdown` – Apagar o Reiniciar Linux

`shutdown` programa un apagado o reinicio del sistema.

**Ejemplo:**

- **Reiniciar el sistema:**

  ```bash
  shutdown -r now
  ```

### 81. `reboot` – Reiniciar o Reiniciar el Sistema

`reboot` reinicia el sistema inmediatamente.

**Ejemplo:**

```bash
reboot
```

### 82. `systemctl` – Controlar el Administrador de Sistema y Servicios systemd

`systemctl` gestiona servicios bajo systemd.

**Ejemplo:**

- **Iniciar un servicio:**

  ```bash
  systemctl start apache2
  ```

### 83. `service` – Ejecuta un Script SysV Init

`service` gestiona servicios bajo el sistema init tradicional.

**Ejemplo:**

- **Iniciar un servicio:**

  ```bash
  service iptables start
  ```

---

## Otros Comandos Útiles

- **`mount`** – Montar unidades:

  ```bash
  mount /dev/sdX /mnt/point
  ```

- **`umount`** – Desmontar unidades:

  ```bash
  umount /mnt/point
  ```

- **`xargs`** – Construir y ejecutar comandos desde la entrada estándar:

  ```bash
  find . -name "*.txt" | xargs cat
  ```

- **`alias`** – Crear accesos directos para comandos:

  ```bash
  alias ll='ls -la'
  ```

- **`jobs`** – Listar trabajos en segundo plano:

  ```bash
  jobs
  ```

- **`bg`** – Reanudar un proceso en segundo plano:

  ```bash
  bg %1
  ```

- **`killall`** – Terminar procesos por nombre:

  ```bash
  killall firefox
  ```

- **`history`** – Mostrar comandos utilizados previamente:

  ```bash
  history
  ```

- **`man`** – Acceder a manuales de ayuda:

  ```bash
  man ls
  ```

- **`screen`** – Gestionar sesiones de terminal múltiples:

  ```bash
  screen
  ```

- **`ssh`** – Conectar a servidores remotos:

  ```bash
  ssh user@hostname
  ```

- **`tcpdump`** – Capturar tráfico de red:

  ```bash
  tcpdump -i eth0
  ```

- **`watch`** – Repetir comandos a intervalos:

  ```bash
  watch df -h
  ```

- **`tmux`** – Multiplexor de terminal:

  ```bash
  tmux
  ```

- **`nc`** – Abrir conexiones TCP/UDP:

  ```bash
  nc -l 1234
  ```

- **`nmap`** – Escaneo de puertos y descubrimiento de host:

  ```bash
  nmap -p 22,80,443 example.com
  ```

- **`strace`** – Depurar procesos rastreando llamadas del sistema:

  ```bash
  strace ls
  ```

---

## Consejos Clave para Usar Comandos en Linux

1. **Conoce tu shell:** Familiarízate con tu shell preferido.
2. **Domina los comandos principales:** Aprende los comandos básicos.
3. **Usa pipelines:** Combina comandos para eficiencias.
4. **Verifica antes de sobrescribir:** Revisa antes de usar `>`.
5. **Registra tus flujos de trabajo:** Documenta tus procedimientos.
6. **Crea tus propias herramientas:** Usa scripts y alias para automatizar tareas.
7. **Comienza sin sudo:** Usa una cuenta estándar para aprender.




