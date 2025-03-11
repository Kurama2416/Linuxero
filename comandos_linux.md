
### **Administración de Archivos en Linux**

La gestión de archivos y directorios es una tarea clave en el uso de la terminal en Linux. A continuación, se presentan comandos esenciales para organizar y manipular archivos de manera eficiente.

---

## **1. `ls` – Mostrar el Contenido de un Directorio**

El comando `ls` permite listar los elementos dentro de una carpeta, mostrando archivos y subdirectorios con información adicional opcional.

**Uso básico:**
   
```fish
ls [opciones] [directorio]
```

**Opciones destacadas:**
- `-l` → Muestra detalles como permisos, propietario, tamaño y fecha de modificación.
- `-a` → Incluye archivos ocultos en la lista.
- `-R` → Muestra el contenido de los subdirectorios de manera recursiva.
- `-S` → Ordena los archivos por tamaño, de mayor a menor.
- `-t` → Organiza por fecha de modificación, mostrando primero los más recientes.

**Ejemplo:**
```fish
ls -l /home/usuario/documentos
```
Esto muestra un listado detallado del contenido dentro de `documentos`.

---

## **2. `cd` – Cambiar de Directorio**

Este comando permite moverse entre diferentes ubicaciones dentro del sistema de archivos.

**Uso básico:**
```fish
cd [directorio]
```

**Ejemplos:**
- `cd /usr/local` → Se traslada al directorio `/usr/local`.
- `cd ..` → Regresa al directorio superior.
- `cd ~/imágenes` → Se mueve a la carpeta `imágenes` dentro del directorio personal del usuario.

---

## **3. `mkdir` – Crear Directorios**

`mkdir` permite generar nuevas carpetas dentro del sistema de archivos.

**Uso básico:**
```fish
mkdir [opciones] <nombre_del_directorio>
```

**Opciones útiles:**
- `-p` → Crea una estructura de directorios de forma recursiva si no existen previamente.
- `-v` → Muestra mensajes de confirmación sobre las carpetas creadas.

**Ejemplo:**
```fish
mkdir -v ~/proyecto/codigo
```
Esto creará la carpeta `codigo` dentro de `proyecto` en el directorio personal del usuario.

---

## **4. `rmdir` y `rm` – Eliminar Directorios y Archivos**

- `rmdir` → Se usa para eliminar carpetas vacías.
- `rm` → Permite borrar archivos y carpetas, incluso si contienen información.

**Uso básico:**
```fish
rmdir [opciones] <directorio>
rm [opciones] <archivo/directorio>
```

**Opciones recomendadas:**
- `-v` → Muestra información sobre los archivos eliminados.
- `-r` → Borra directorios y su contenido recursivamente.
- `-f` → Fuerza la eliminación sin solicitar confirmación.

**Ejemplo:**
```fish
rm -rf ~/proyecto
```
Esto elimina `proyecto` y todo su contenido de manera irreversible.

---

## **5. `touch` – Crear Archivos Vacíos**

Este comando se emplea para generar archivos vacíos o actualizar la fecha de modificación de archivos existentes.

**Uso básico:**
```fish
touch [opciones] <nombre_de_archivo>
```

**Ejemplo:**
```fish
touch ~/notas.txt
```
Esto crea el archivo `notas.txt` en la carpeta personal del usuario si no existía previamente.

---

## **6. `cp` – Copiar Archivos y Directorios**

Este comando permite duplicar archivos y carpetas en otra ubicación dentro del sistema de archivos.

**Uso básico:**
```fish
cp [opciones] <origen> <destino>
```

**Opciones útiles:**
- `-r` → Copia directorios completos de forma recursiva.
- `-i` → Solicita confirmación antes de sobrescribir archivos.
- `-v` → Muestra detalles del proceso de copiado.

**Ejemplo:**
```fish
cp -r ~/documentos /backup/
```
Esto copia la carpeta `documentos` y su contenido a `/backup/`.

---

## **7. `mv` – Mover o Renombrar Archivos**

`mv` permite cambiar archivos o directorios de ubicación o modificar su nombre.

**Uso básico:**
```fish
mv [opciones] <origen> <destino>
```

**Ejemplos:**
- `mv ~/descargas/archivo.txt ~/documentos/` → Mueve el archivo `archivo.txt` de `descargas` a `documentos`.
- `mv antiguo_nombre.txt nuevo_nombre.txt` → Renombra el archivo.

---

## **8. `find` – Buscar Archivos en Directorios**

Este comando permite localizar archivos en el sistema según distintos criterios.

**Uso básico:**
```fish
find [ruta] [criterio]
```

**Opciones destacadas:**
- `-name "archivo.txt"` → Busca un archivo específico por nombre.
- `-type f` → Busca solo archivos.
- `-mtime +30` → Busca archivos modificados hace más de 30 días.
- `-user usuario` → Busca archivos pertenecientes a un usuario en particular.

**Ejemplo:**
```fish
find ~/documentos -name "*.pdf"
```
Esto busca archivos con extensión `.pdf` dentro de `documentos`.

---

## **9. `du` – Consultar el Uso del Espacio en Disco**

`du` muestra cuánto espacio ocupan archivos y carpetas en el sistema de archivos.

**Uso básico:**
```fish
du [opciones] [ruta]
```

**Opciones más usadas:**
- `-h` → Muestra los tamaños en un formato legible (por ejemplo, MB y GB).
- `-s` → Muestra solo el tamaño total de un directorio sin detalles de cada archivo.
- `-a` → Muestra el tamaño de todos los archivos dentro de un directorio.

**Ejemplo:**
```fish
du -sh ~/imágenes
```
Esto muestra el tamaño total de la carpeta `imágenes` en un formato fácil de leer.

---

---

## **10. `grep` – Buscar Texto en Archivos**

El comando `grep` permite buscar cadenas de texto dentro de archivos y mostrar solo las líneas que coinciden con el patrón especificado.

**Uso básico:**
```fish
grep [opciones] "texto" [archivo]
```

**Opciones útiles:**
- `-i` → Ignora mayúsculas y minúsculas en la búsqueda.
- `-R` → Busca de forma recursiva en subdirectorios.
- `-c` → Muestra solo la cantidad de coincidencias en lugar del contenido.
- `-v` → Muestra las líneas que NO contienen el patrón buscado.

**Ejemplo:**
```fish
grep -i "error" /var/log/syslog
```
Este comando buscará la palabra "error" en el archivo `syslog`, ignorando diferencias entre mayúsculas y minúsculas.

---

## **11. `awk` – Procesamiento de Texto Basado en Patrones**

`awk` es una herramienta avanzada para procesar texto basado en estructuras de líneas y columnas. Se puede usar para extraer información de archivos de datos estructurados.

**Uso básico:**
```fish
awk 'patrón { acción }' archivo
```

**Ejemplo:**
```fish
awk '/error/ {print $1}' /var/log/syslog
```
Esto imprimirá el primer campo de cada línea donde aparezca la palabra "error" en el archivo `syslog`.

---

## **12. `sed` – Edición de Texto en Archivos**

`sed` es un editor de flujo que permite buscar, reemplazar y modificar texto dentro de archivos sin abrirlos directamente.

**Uso básico:**
```fish
sed 's/antiguo/nuevo/g' archivo
```

**Ejemplo:**
```fish
sed 's/error/ERROR/g' /var/log/syslog
```
Este comando reemplaza todas las apariciones de "error" por "ERROR" en el archivo `syslog`.

---

## **13. `sort` – Ordenar el Contenido de un Archivo**

Ordena las líneas de un archivo alfabética o numéricamente.

**Uso básico:**
```fish
sort [opciones] archivo
```

**Opciones destacadas:**
- `-n` → Ordena numéricamente.
- `-r` → Invierte el orden de clasificación.
- `-k` → Ordena según una columna específica.

**Ejemplo:**
```fish
sort -n notas.txt
```
Esto ordenará el contenido de `notas.txt` en orden numérico.

---

## **14. `uniq` – Eliminar Líneas Duplicadas en un Archivo**

Elimina líneas repetidas en archivos de texto. Se usa frecuentemente junto con `sort` para eliminar duplicados correctamente.

**Uso básico:**
```fish
uniq [opciones] archivo
```

**Ejemplo:**
```fish
sort datos.txt | uniq
```
Ordena el archivo `datos.txt` y elimina las líneas duplicadas.

---

## **15. `diff` – Comparar Archivos Línea por Línea**

Compara dos archivos y muestra sus diferencias.

**Uso básico:**
```fish
diff archivo1 archivo2
```

**Opciones útiles:**
- `-b` → Ignora diferencias en espacios en blanco.
- `-u` → Muestra las diferencias con más contexto.

**Ejemplo:**
```fish
diff original.txt actualizado.txt
```
Esto muestra las diferencias entre `original.txt` y `actualizado.txt`.

---

## **16. `wc` – Contar Líneas, Palabras y Caracteres en un Archivo**

`wc` proporciona el conteo de líneas, palabras y bytes de un archivo.

**Uso básico:**
```fish
wc [opciones] archivo
```

**Opciones más comunes:**
- `-l` → Cuenta solo las líneas.
- `-w` → Cuenta solo las palabras.
- `-c` → Cuenta solo los bytes.

**Ejemplo:**
```fish
wc -l reporte.txt
```
Este comando muestra cuántas líneas tiene `reporte.txt`.

---

## **17. `>` – Redirigir la Salida de un Comando a un Archivo**

Este operador redirige el resultado de un comando a un archivo, **sobrescribiendo** su contenido si ya existe.

**Uso básico:**
```fish
comando > archivo.txt
```

**Ejemplo:**
```fish
ls -l > lista_archivos.txt
```
Esto guarda la salida del comando `ls -l` en el archivo `lista_archivos.txt`, reemplazando cualquier contenido anterior.

---

## **18. `>>` – Agregar la Salida a un Archivo sin Sobrescribirlo**

Si quieres añadir el resultado de un comando a un archivo sin perder su contenido, usa `>>`.

**Uso básico:**
```fish
comando >> archivo.txt
```

**Ejemplo:**
```fish
echo "Nueva línea de texto" >> notas.txt
```
Esto agrega `"Nueva línea de texto"` al final del archivo `notas.txt` sin borrar lo que ya tenía.

---

## **19. `<` – Usar un Archivo como Entrada para un Comando**

El operador `<` permite que un comando tome la información de un archivo en lugar de escribirla manualmente.

**Uso básico:**
```fish
comando < archivo.txt
```

**Ejemplo:**
```fish
wc -l < documento.txt
```
Este comando cuenta las líneas de `documento.txt` sin necesidad de escribir `wc -l documento.txt`.

---

## **20. `|` – Conectar la Salida de un Comando con Otro**

El operador `|` (pipe o tubería) permite tomar la salida de un comando y usarla como entrada para otro.

**Uso básico:**
```fish
comando1 | comando2
```

**Ejemplo:**
```fish
ls -l | less
```
Esto lista los archivos con `ls -l`, pero en lugar de mostrar toda la salida en pantalla, la envía a `less`, permitiendo desplazarse línea por línea.

---

## **21. `tee` – Guardar y Mostrar la Salida de un Comando**

`tee` permite ver la salida en pantalla **y** guardarla en un archivo al mismo tiempo.

**Uso básico:**
```fish
comando | tee archivo.txt
```

**Ejemplo:**
```fish
ls -l | tee lista.txt
```
Esto muestra el resultado de `ls -l` en la terminal y lo guarda en `lista.txt` simultáneamente.

---

## **22. `tar` – Crear y Extraer Archivos Comprimidos**

El comando `tar` permite empaquetar varios archivos en un solo archivo `.tar`, con la opción de comprimirlo.

**Uso básico:**
```fish
tar [opciones] archivo.tar [archivos o directorios]
```

**Opciones comunes:**
- `-c` → Crea un nuevo archivo `.tar`.
- `-x` → Extrae el contenido de un archivo `.tar`.
- `-f` → Especifica el nombre del archivo.
- `-v` → Muestra detalles del proceso.
- `-z` → Comprime con `gzip`.

**Ejemplo:**
```fish
tar -cvzf respaldo.tar.gz /home/usuario/documentos
```
Esto empaqueta y comprime la carpeta `documentos` en `respaldo.tar.gz`.

Para extraerlo:
```fish
tar -xvzf respaldo.tar.gz
```

---

## **23. `gzip` – Comprimir Archivos**

`gzip` reduce el tamaño de archivos individuales usando el algoritmo LZ77.

**Uso básico:**
```fish
gzip archivo
```

**Ejemplo:**
```fish
gzip informe.txt
```
Esto convierte `informe.txt` en `informe.txt.gz`, reduciendo su tamaño.

Para descomprimir:
```fish
gunzip informe.txt.gz
```

---

## **24. `zip` – Crear Archivos ZIP**

`zip` comprime archivos y carpetas en un solo `.zip`.

**Uso básico:**
```fish
zip [opciones] archivo.zip archivos
```

**Ejemplo:**
```fish
zip -r comprimido.zip carpeta/
```
Esto empaqueta y comprime la carpeta `carpeta/` en `comprimido.zip`.

Para descomprimir:
```fish
unzip comprimido.zip
```

---

## **25. `scp` – Copiar Archivos de Forma Segura Entre Computadoras**

`scp` (Secure Copy) transfiere archivos entre equipos a través de SSH.

**Uso básico:**
```fish
scp [archivo] usuario@servidor:/ruta/destino
```

**Ejemplo:**
```fish
scp documento.txt usuario@192.168.1.10:/home/usuario/
```
Esto copia `documento.txt` al equipo con IP `192.168.1.10`.

Para copiar un archivo desde el servidor al equipo local:
```fish
scp usuario@192.168.1.10:/home/usuario/documento.txt .
```

---

## **26. `rsync` – Sincronizar Archivos y Directorios**

`rsync` copia archivos entre ubicaciones de manera eficiente, transfiriendo solo los cambios.

**Uso básico:**
```fish
rsync [opciones] origen destino
```

**Opciones comunes:**
- `-a` → Copia en **modo archivo** (mantiene permisos y fechas).
- `-v` → Muestra detalles del proceso.
- `-h` → Muestra tamaños en un formato legible.
- `-z` → Comprime los archivos durante la transferencia.

**Ejemplo:**
```fish
rsync -avh ~/documentos usuario@192.168.1.10:/backup/
```
Esto sincroniza `documentos` con el servidor `192.168.1.10`, manteniendo permisos y mostrando detalles.

---

## **27. `sftp` – Transferencia de Archivos Segura con SSH**

`sftp` permite subir y descargar archivos de forma interactiva a través de SSH.

**Uso básico:**
```fish
sftp usuario@servidor
```

**Comandos útiles dentro de `sftp`:**
- `get archivo-remoto` → Descarga un archivo.
- `put archivo-local` → Sube un archivo.
- `ls` → Lista los archivos en el servidor.

**Ejemplo:**
```fish
sftp usuario@192.168.1.10
put reporte.pdf
get respaldo.zip
```
Esto sube `reporte.pdf` y descarga `respaldo.zip`.

---

## **28. `wget` – Descargar Archivos desde Internet**

`wget` obtiene archivos desde servidores web usando HTTP, HTTPS o FTP.

**Uso básico:**
```fish
wget URL
```

**Ejemplo:**
```fish
wget https://ejemplo.com/archivo.iso
```
Esto descarga `archivo.iso` desde la web.

 **Opciones útiles:**
- `-c` → Reanuda descargas interrumpidas.
- `-r` → Descarga de forma recursiva (para sitios web).
- `-O archivo` → Guarda con un nombre específico.

---

## **29. `curl` – Transferir Datos con URL**

`curl` permite obtener información de URLs, interactuar con APIs y descargar archivos.

**Uso básico:**
```fish
curl [opciones] URL
```

**Ejemplo:**
```fish
curl -L https://ejemplo.com
```
Esto obtiene la página de `ejemplo.com`, siguiendo redirecciones (`-L`).

 **Opciones útiles:**
- `-o archivo` → Guarda la salida en un archivo.
- `-I` → Muestra solo los encabezados HTTP.
- `-L` → Sigue redirecciones.

---

## **30. `chmod` – Modificar Permisos de Archivos y Directorios**

`chmod` cambia los permisos de acceso de archivos y carpetas, controlando quién puede leer, escribir o ejecutar un archivo.

**Uso básico:**
```fish
chmod [modo] archivo
```

**Modos de permisos numéricos:**
Cada permiso tiene un valor:
- `4` → Lectura (`r`)
- `2` → Escritura (`w`)
- `1` → Ejecución (`x`)

Se suman para definir los permisos de usuario, grupo y otros:
- `chmod 755 archivo.txt` → Propietario tiene **rwx (7)**, grupo y otros tienen **r-x (5)**.
- `chmod 644 archivo.txt` → Propietario tiene **rw- (6)**, grupo y otros tienen **r-- (4)**.

**Ejemplo:**
```fish
chmod 755 script.sh
```
Esto permite que el propietario ejecute, lea y escriba el archivo, mientras que otros solo pueden ejecutarlo y leerlo.

**Modo simbólico:**
```fish
chmod g+w archivo.txt
```
Esto añade permiso de escritura (`+w`) al grupo del archivo.

---

## **31. `chown` – Cambiar Propietario y Grupo de un Archivo**

`chown` permite asignar un nuevo propietario y grupo a un archivo o directorio.

**Uso básico:**
```fish
chown usuario:grupo archivo
```

**Ejemplo:**
```fish
chown juan:desarrolladores archivo.txt
```
Esto asigna al usuario `juan` como propietario y al grupo `desarrolladores`.

Para cambiar solo el propietario:
```fish
chown juan archivo.txt
```

---

## **32. `umask` – Definir Permisos Predeterminados para Nuevos Archivos**

`umask` establece los permisos con los que se crean archivos y directorios nuevos.

**Uso básico:**
```fish
umask valor
```

**Ejemplo:**
```fish
umask 027
```
Esto hace que los nuevos archivos tengan permisos `640` (rw-r-----) y los directorios `750` (rwxr-x---).

---

## **33. `ps` – Mostrar Procesos en Ejecución**

`ps` proporciona una lista de los procesos activos en el sistema.

**Uso básico:**
```fish
ps [opciones]
```

 **Opciones útiles:**
- `aux` → Muestra todos los procesos del sistema.
- `-e` → Lista todos los procesos en ejecución.
- `--forest` → Muestra los procesos en formato de árbol.

**Ejemplo:**
```fish
ps aux | grep firefox
```
Esto filtra los procesos que contienen la palabra `firefox`.

---

## **34. `top` – Monitoreo de Procesos en Tiempo Real**

`top` muestra información dinámica sobre los procesos, como uso de CPU y memoria.

**Uso básico:**
```fish
top
```

 **Opciones útiles:**
- `-u usuario` → Muestra solo los procesos de un usuario.
- `q` → Sale del programa.

**Ejemplo:**
```fish
top -u root
```
Esto muestra solo los procesos ejecutados por `root`.

---

## **35. `htop` – Alternativa Interactiva a `top`**

`htop` ofrece una interfaz mejorada para visualizar y gestionar procesos.

**Uso básico:**
```fish
htop
```

**Diferencias con `top`:**
✔️ Permite desplazarse por los procesos.
✔️ Muestra gráficos de uso de CPU y memoria.
✔️ Permite matar procesos con un clic.

---

## **36. `kill` – Terminar un Proceso**

`kill` finaliza procesos en ejecución usando su ID (PID).

**Uso básico:**
```fish
kill [señal] PID
```

**Ejemplo:**
```fish
kill -9 12345
```
Esto fuerza la terminación del proceso con PID `12345`.

---

## **37. `pkill` – Finalizar Procesos por Nombre**

`pkill` permite matar procesos basándose en su nombre.

**Uso básico:**
```fish
pkill nombre_proceso
```

**Ejemplo:**
```fish
pkill firefox
```
Esto finaliza todos los procesos de `firefox`.

---

## **38. `nohup` – Ejecutar Comandos que Sobrevivan a la Cierre de Sesión**

`nohup` ejecuta un comando sin que se detenga al cerrar la terminal.

**Uso básico:**
```fish
nohup comando &
```

**Ejemplo:**
```fish
nohup python script.py &
```
Esto ejecuta `script.py` en segundo plano sin interrupciones.

---

## **39. `df` – Ver Espacio en Disco**

`df` muestra información sobre el uso del disco en los sistemas de archivos montados.

**Uso básico:**
```fish
df [opciones]
```

**Ejemplo:**
```fish
df -h
```
Esto muestra el uso del disco en un formato legible.

---

## **40. `free` – Ver Uso de Memoria RAM**

`free` muestra información sobre la memoria RAM y el espacio de intercambio (swap).

**Uso básico:**
```fish
free [opciones]
```

**Ejemplo:**
```fish
free -h
```
Esto muestra el uso de memoria en un formato fácil de entender.

---

## **41. `vmstat` – Monitorear el Rendimiento del Sistema**

`vmstat` muestra estadísticas de CPU, memoria, entrada/salida y procesos.

**Uso básico:**
```fish
vmstat [intervalo] [veces]
```

**Ejemplo:**
```fish
vmstat 5 10
```
Esto muestra información cada 5 segundos, 10 veces.

---

## **42. `iostat` – Ver Estadísticas de CPU y Disco**

`iostat` informa sobre el uso del procesador y la actividad de los discos.

**Uso básico:**
```fish
iostat [opciones]
```

**Ejemplo:**
```fish
iostat -d -x 5
```
Esto muestra estadísticas detalladas de los discos cada 5 segundos.

---

## **43. `sar` – Analizar el Uso de Recursos del Sistema**

`sar` recopila datos sobre CPU, memoria, discos y red en tiempo real.

**Uso básico:**
```fish
sar [opciones] [intervalo] [veces]
```

**Ejemplo:**
```fish
sar -u 5 10
```
Muestra estadísticas de uso de CPU cada 5 segundos, 10 veces.

---

## **44. `uptime` – Ver el Tiempo de Actividad del Sistema**

`uptime` muestra cuánto tiempo ha estado encendido el sistema.

**Uso básico:**
```fish
uptime
```

 **Ejemplo de salida:**
```
10:45:23 up 3 days, 4:12, 2 users, load average: 0.15, 0.12, 0.10
```
Esto indica que el sistema ha estado encendido **3 días, 4 horas y 12 minutos**.

---

## **45. `who` – Ver Usuarios Conectados al Sistema**

`who` muestra qué usuarios están conectados actualmente.

**Uso básico:**
```fish
who
```

 **Ejemplo de salida:**
```
usuario1  tty1  2024-03-10 09:20
usuario2  pts/0  2024-03-10 10:00
```
Esto indica que `usuario1` y `usuario2` están conectados.

---

## **46. `w` – Mostrar Actividad de los Usuarios Conectados**

`w` proporciona información detallada sobre los usuarios en el sistema, como el tiempo que llevan conectados y qué procesos están ejecutando.

**Uso básico:**
```fish
w
```

 **Ejemplo de salida:**
```
USER     TTY      FROM           LOGIN@   IDLE   JCPU   PCPU WHAT
usuario1 pts/0    192.168.1.2    10:20    1:10   0.23s  0.15s fish
```
Muestra que `usuario1` está en `pts/0`, lleva conectado desde las 10:20 y está ejecutando `fish`.

---

## **47. `whoami` – Mostrar el Usuario Actual**

`whoami` imprime el nombre del usuario que ejecuta el comando.

**Uso básico:**
```fish
whoami
```

**Ejemplo:**
```fish
whoami
```
Salida:
```
usuario1
```
Esto indica que el usuario actual es `usuario1`.

---

## **48. `id` – Mostrar Identificadores del Usuario**

`id` muestra el UID (User ID), GID (Group ID) y los grupos a los que pertenece un usuario.

**Uso básico:**
```fish
id [usuario]
```

**Ejemplo:**
```fish
id usuario1
```
Salida:
```
uid=1001(usuario1) gid=1001(usuario1) groups=1001(usuario1),27(sudo)
```
Indica que `usuario1` tiene UID 1001, pertenece al grupo `sudo` y tiene GID 1001.

---

## **49. `passwd` – Cambiar la Contraseña de un Usuario**

`passwd` permite modificar la contraseña del usuario actual o de otro usuario si se tienen permisos de administrador.

**Uso básico:**
```fish
passwd [usuario]
```

**Ejemplo:**
```fish
passwd
```
Solicita una nueva contraseña para el usuario actual.

Para cambiar la contraseña de otro usuario (requiere permisos de root):
```fish
sudo passwd usuario2
```

---

## **50. `groupadd` – Crear un Nuevo Grupo de Usuarios**

`groupadd` permite añadir un nuevo grupo al sistema.

**Uso básico:**
```fish
sudo groupadd nombre_grupo
```

**Ejemplo:**
```fish
sudo groupadd desarrolladores
```
Esto crea un grupo llamado `desarrolladores`.

---

## **51. `usermod` – Modificar un Usuario**

`usermod` permite cambiar las características de un usuario, como su grupo principal o su directorio home.

**Uso básico:**
```fish
sudo usermod [opciones] usuario
```

**Ejemplo:**
```fish
sudo usermod -aG desarrolladores usuario1
```
Esto agrega `usuario1` al grupo `desarrolladores` sin eliminarlo de sus otros grupos.

---

## **52. `deluser` y `delgroup` – Eliminar Usuarios y Grupos**

Para borrar un usuario:
```fish
sudo deluser usuario
```

Para borrar un grupo:
```fish
sudo delgroup grupo
```

**Ejemplo:**
```fish
sudo deluser usuario1
sudo delgroup desarrolladores
```
Estos comandos eliminan `usuario1` y el grupo `desarrolladores`.

---

## **53. `history` – Ver Comandos Ejecutados Anteriormente**

`history` muestra una lista de los últimos comandos usados en la terminal.

**Uso básico:**
```fish
history
```

**Ejemplo:**
```fish
history | grep ssh
```
Muestra los comandos anteriores que contienen la palabra `ssh`.

Para borrar el historial:
```fish
history -c
```

---

## **54. `alias` – Crear Alias para Comandos**

`alias` permite definir comandos personalizados para simplificar tareas repetitivas.

**Uso básico:**
```fish
alias nombre='comando'
```

**Ejemplo:**
```fish
alias actualizar='sudo apt update && sudo apt upgrade -y'
```
Ahora, al escribir `actualizar`, el sistema ejecutará `sudo apt update && sudo apt upgrade -y`.

Para eliminar un alias:
```fish
unalias nombre
```

---

## **55. `echo` – Mostrar Texto o Variables en la Terminal**

`echo` imprime texto o variables en la pantalla.

**Uso básico:**
```fish
echo "Hola, mundo"
```

**Ejemplo:**
```fish
echo $HOME
```
Esto muestra la ruta del directorio personal del usuario.

Para escribir en un archivo:
```fish
echo "Texto de prueba" > archivo.txt
```

---

## **56. `env` – Mostrar Variables de Entorno**

`env` lista las variables de entorno del sistema.

**Uso básico:**
```fish
env
```

**Ejemplo:**
```fish
env | grep PATH
```
Muestra el valor de la variable `PATH`.

---

## **57. `export` – Definir Variables de Entorno**

`export` establece variables de entorno para usarlas en la sesión actual de la terminal.

**Uso básico:**
```fish
export NOMBRE=valor
```

**Ejemplo:**
```fish
export EDITOR=nano
echo $EDITOR
```
Esto define `nano` como editor de texto predeterminado y lo muestra con `echo`.

Para hacer permanente la variable, agrégala a `~/.fishrc` o `~/.profile`.

---

## **58. `source` – Aplicar Cambios en Archivos de Configuración**

`source` ejecuta el contenido de un archivo en la terminal sin necesidad de reiniciar la sesión.

**Uso básico:**
```fish
source archivo
```

**Ejemplo:**
```fish
source ~/.fishrc
```
Esto aplica los cambios recientes en `.fishrc` sin cerrar la terminal.

---

## **59. `locate` – Buscar Archivos en el Sistema**

`locate` encuentra archivos rápidamente usando una base de datos actualizada periódicamente.

**Uso básico:**
```fish
locate nombre_archivo
```

**Ejemplo:**
```fish
locate documento.pdf
```
Esto muestra todas las rutas donde existe `documento.pdf`.

Si `locate` no encuentra nada, actualiza la base de datos con:
```fish
sudo updatedb
```

---

## **60. `which` – Encontrar la Ruta de un Comando**

`which` muestra la ubicación exacta de un comando ejecutable.

**Uso básico:**
```fish
which comando
```

**Ejemplo:**
```fish
which python
```
Salida posible:
```
/usr/bin/python
```
Esto indica dónde está instalado `python`.

---

## **61. `time` – Medir el Tiempo de Ejecución de un Comando**

`time` calcula cuánto tarda en ejecutarse un comando.

**Uso básico:**
```fish
time comando
```

**Ejemplo:**
```fish
time ls -R /
```
Esto mide el tiempo que toma listar todo el sistema de archivos.

---

## **62. `tr` – Reemplazar Caracteres en Texto**

`tr` sustituye, elimina o comprime caracteres en un flujo de texto.

**Uso básico:**
```fish
echo "texto" | tr 'a-z' 'A-Z'
```

**Ejemplo:**
```fish
echo "hola mundo" | tr ' ' '-'
```
Salida:
```
hola-mundo
```
Reemplaza espacios por guiones.

---

## **63. `cut` – Extraer Columnas de un Archivo**

`cut` selecciona partes de líneas basadas en delimitadores.

**Uso básico:**
```fish
cut -d'delimitador' -f# archivo
```

**Ejemplo:**
```fish
echo "nombre,edad,ciudad" | cut -d',' -f2
```
Salida:
```
edad
```
Extrae el segundo campo (`edad`).

---

## **64. `basename` – Obtener el Nombre de un Archivo desde una Ruta**

`basename` extrae el nombre de un archivo desde su ruta completa.

**Uso básico:**
```fish
basename ruta/del/archivo
```

**Ejemplo:**
```fish
basename /home/usuario/documento.txt
```
Salida:
```
documento.txt
```
Solo muestra el nombre del archivo sin la ruta.

---

## **65. `dirname` – Obtener el Directorio de un Archivo**

`dirname` devuelve solo la ruta sin el nombre del archivo.

**Uso básico:**
```fish
dirname ruta/del/archivo
```

**Ejemplo:**
```fish
dirname /home/usuario/documento.txt
```
Salida:
```
/home/usuario
```
Solo muestra la carpeta donde está el archivo.

---

## **66. `mktemp` – Crear Archivos o Directorios Temporales**

`mktemp` genera archivos o directorios temporales con nombres únicos.

**Uso básico:**
```fish
mktemp
```

**Ejemplo:**
```fish
mktemp /tmp/archivoXXXXXX
```
Salida:
```
/tmp/archivoA1B2C3
```
Se genera un archivo temporal con un nombre aleatorio.

Para crear un directorio temporal:
```fish
mktemp -d
```

---

## **67. `xargs` – Ejecutar Comandos con Entradas en Lote**

`xargs` permite ejecutar comandos usando múltiples entradas.

**Uso básico:**
```fish
comando | xargs otro_comando
```

**Ejemplo:**
```fish
echo "archivo1 archivo2 archivo3" | xargs rm
```
Esto eliminará `archivo1`, `archivo2` y `archivo3`.

Otro uso común:
```fish
find . -name "*.log" | xargs rm
```
Esto busca y elimina todos los archivos `.log` en el directorio actual.

---

## **68. `tee` – Mostrar y Guardar Salida de un Comando**

`tee` guarda la salida de un comando en un archivo **y también la muestra en pantalla**.

**Uso básico:**
```fish
comando | tee archivo
```

**Ejemplo:**
```fish
ls -l | tee lista.txt
```
Esto lista los archivos y guarda la salida en `lista.txt`.

Para añadir en vez de sobrescribir:
```fish
comando | tee -a archivo
```

---

## **69. `yes` – Generar una Respuesta Automática en Bucle**

`yes` imprime repetidamente una cadena hasta que se detiene manualmente.

**Uso básico:**
```fish
yes [texto]
```

**Ejemplo:**
```fish
yes "Confirmado"
```
Salida infinita:
```
Confirmado
Confirmado
Confirmado
...
```
Para detenerlo, presiona `Ctrl + C`.

Se usa para responder automáticamente a comandos que piden confirmación:
```fish
yes | sudo apt upgrade
```
Esto confirma todas las preguntas de `apt upgrade`.

---

## **70. `watch` – Ejecutar un Comando Repetidamente**

`watch` corre un comando a intervalos regulares y muestra la salida en tiempo real.

**Uso básico:**
```fish
watch [comando]
```

**Ejemplo:**
```fish
watch df -h
```
Esto muestra el uso del disco y lo actualiza cada 2 segundos.

Para cambiar el intervalo de actualización:
```fish
watch -n 5 free -h
```
Esto ejecuta `free -h` cada 5 segundos.

---

## **71. `nohup` – Ejecutar un Comando que Sobreviva al Cierre de la Terminal**

`nohup` ejecuta procesos que siguen corriendo incluso si cierras la terminal.

**Uso básico:**
```fish
nohup comando &
```

**Ejemplo:**
```fish
nohup python script.py &
```
Esto ejecuta `script.py` en segundo plano sin interrupciones.

La salida se guarda en `nohup.out` si no se especifica otro archivo.

---

## **72. `jobs` – Ver Procesos en Segundo Plano**

`jobs` muestra los procesos que se están ejecutando en segundo plano en la terminal.

**Uso básico:**
```fish
jobs
```

 **Ejemplo de salida:**
```
[1]   Running   python script.py &
[2]   Stopped   nano documento.txt
```
Esto indica que el primer proceso (`script.py`) está corriendo y el segundo (`nano`) está pausado.

Para reanudar un proceso detenido:
```fish
fg %2
```
Esto trae `nano` al primer plano.

---

## **73. `bg` – Reanudar un Proceso en Segundo Plano**

Si tienes un proceso pausado, `bg` lo reanuda en segundo plano.

**Uso básico:**
```fish
bg %número
```

**Ejemplo:**
```fish
bg %2
```
Esto reanuda el segundo proceso (`nano documento.txt`) sin traerlo al primer plano.

---

## **74. `fg` – Traer un Proceso en Segundo Plano al Primer Plano**

`fg` permite continuar un proceso en primer plano.

**Uso básico:**
```fish
fg %número
```

**Ejemplo:**
```fish
fg %1
```
Esto trae el proceso 1 (`script.py`) de vuelta al primer plano.

---

## **75. `disown` – Desvincular un Proceso de la Terminal**

`disown` elimina un proceso de la lista de trabajos, permitiendo que continúe ejecutándose incluso si cierras la terminal.

**Uso básico:**
```fish
disown %número
```

**Ejemplo:**
```fish
disown %1
```
Esto desvincula el proceso `1` de la terminal, evitando que se cierre si cierras la sesión.

Para desvincular todos los procesos en segundo plano:
```fish
disown -a
```

---

## **76. `pkill` – Terminar Procesos por Nombre**

`pkill` permite matar procesos basándose en su nombre, sin necesidad de conocer su PID.

**Uso básico:**
```fish
pkill nombre_proceso
```

**Ejemplo:**
```fish
pkill firefox
```
Esto finaliza todos los procesos de `firefox`.

Para cerrar un proceso con confirmación interactiva:
```fish
pkill -i firefox
```

---

## **77. `killall` – Matar Todos los Procesos con un Nombre Específico**

`killall` finaliza todos los procesos que coincidan con un nombre determinado.

**Uso básico:**
```fish
killall nombre_proceso
```

**Ejemplo:**
```fish
killall python
```
Esto detiene **todos** los procesos de `python` en ejecución.

Para confirmar antes de matar cada proceso:
```fish
killall -i python
```

---

## **78. `uptime` – Mostrar el Tiempo de Actividad del Sistema**

`uptime` muestra cuánto tiempo lleva encendido el sistema.

**Uso básico:**
```fish
uptime
```

**Ejemplo de salida:**
```
10:45:23 up 3 days, 4:12, 2 users, load average: 0.15, 0.12, 0.10
```
Esto indica que el sistema ha estado encendido **3 días, 4 horas y 12 minutos**.

---

## **79. `hostname` – Mostrar o Cambiar el Nombre del Equipo**

`hostname` imprime o cambia el nombre de la máquina en la red.

**Uso básico:**
```fish
hostname
```

**Ejemplo:**
```fish
hostname
```
Salida:
```
mi-servidor
```
Esto muestra el nombre del equipo.

Para cambiar el hostname temporalmente:
```fish
sudo hostname nuevo-nombre
```

Para hacerlo permanente, edita `/etc/hostname`:
```fish
echo "nuevo-nombre" | sudo tee /etc/hostname
```

---

## **80. `uname` – Mostrar Información del Sistema**

`uname` imprime datos sobre el kernel y la arquitectura del sistema.

**Uso básico:**
```fish
uname [opciones]
```

 **Opciones útiles:**
- `-a` → Muestra toda la información del sistema.
- `-r` → Muestra la versión del kernel.
- `-m` → Muestra la arquitectura del procesador.

**Ejemplo:**
```fish
uname -a
```
Salida posible:
```
Linux mi-servidor 5.15.0-60-generic x86_64 GNU/Linux
```
Esto indica la versión del kernel, arquitectura y sistema operativo.

---

## **81. `lsb_release` – Mostrar Información de la Distribución de Linux**

`lsb_release` proporciona detalles sobre la distribución de Linux instalada.

**Uso básico:**
```fish
lsb_release [opciones]
```

 **Opciones útiles:**
- `-a` → Muestra toda la información.
- `-d` → Solo muestra la descripción de la distribución.

**Ejemplo:**
```fish
lsb_release -a
```
Salida posible:
```
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy
```
Esto indica que el sistema usa Ubuntu 22.04 LTS.

---

## **82. `df` – Ver Espacio Disponible en Disco**

`df` muestra información sobre el uso del disco en los sistemas de archivos montados.

**Uso básico:**
```fish
df [opciones]
```

**Ejemplo:**
```fish
df -h
```
Salida posible:
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       50G   20G   30G   40% /
```
Muestra el espacio en un formato legible (`-h`).

---

## **83. `du` – Ver el Tamaño de Archivos y Directorios**

`du` muestra cuánto espacio ocupa un archivo o carpeta específica.

**Uso básico:**
```fish
du [opciones] [archivo/directorio]
```

**Ejemplo:**
```fish
du -sh ~/Descargas
```
Salida posible:
```
2.5G    /home/usuario/Descargas
```
Esto indica que la carpeta `Descargas` pesa **2.5 GB**.

---

## **84. `mount` – Montar un Sistema de Archivos**

`mount` se usa para montar dispositivos de almacenamiento en un punto del sistema de archivos.

**Uso básico:**
```fish
sudo mount dispositivo punto_de_montaje
```

**Ejemplo:**
```fish
sudo mount /dev/sdb1 /mnt/usb
```
Esto monta la partición `/dev/sdb1` en `/mnt/usb`.

Para desmontarlo:
```fish
sudo umount /mnt/usb
```

---

## **85. `blkid` – Mostrar Información de Dispositivos de Almacenamiento**

`blkid` muestra los UUID y etiquetas de los discos y particiones.

**Uso básico:**
```fish
blkid
```

 **Ejemplo de salida:**
```
/dev/sda1: UUID="1234-ABCD" TYPE="ext4"
/dev/sdb1: UUID="5678-EFGH" TYPE="vfat"
```
Esto permite identificar discos por su **UUID**, útil en configuraciones de `fstab`.

---

## **86. `fdisk` – Administrar Particiones de Disco**

`fdisk` permite crear, modificar y eliminar particiones en discos.

**Uso básico:**
```fish
sudo fdisk /dev/sdX
```
**Ejemplo:**
```fish
sudo fdisk -l
```
Esto lista todas las particiones del sistema.

⚠️ **Precaución:** Modificar particiones puede borrar datos.

---

## **87. `mkfs` – Formatear un Sistema de Archivos**

`mkfs` crea un nuevo sistema de archivos en una partición o dispositivo de almacenamiento.

**Uso básico:**
```fish
sudo mkfs -t tipo /dev/sdX
```

**Ejemplo:**
```fish
sudo mkfs.ext4 /dev/sdb1
```
Esto formatea la partición `/dev/sdb1` con el sistema de archivos **ext4**.

⚠️ **Precaución:** Esto borra todos los datos del dispositivo.

---

## **88. `fsck` – Comprobar y Reparar un Sistema de Archivos**

`fsck` verifica la integridad de un sistema de archivos y lo repara si es necesario.

**Uso básico:**
```fish
sudo fsck /dev/sdX
```

**Ejemplo:**
```fish
sudo fsck -y /dev/sdb1
```
Esto revisa y repara automáticamente (`-y`) la partición `/dev/sdb1`.

⚠️ **Precaución:** No usar en discos montados.

Para revisar la raíz en el próximo reinicio:
```fish
sudo touch /forcefsck
```

---

## **89. `tune2fs` – Ajustar Opciones de un Sistema de Archivos ext4**

`tune2fs` permite modificar opciones avanzadas en particiones **ext2, ext3 o ext4**.

**Uso básico:**
```fish
sudo tune2fs [opciones] /dev/sdX
```

**Ejemplo:**
```fish
sudo tune2fs -m 5 /dev/sdb1
```
Esto reserva el **5%** del espacio de `/dev/sdb1` para root.

Para cambiar el número de montajes antes de una revisión automática:
```fish
sudo tune2fs -c 50 /dev/sdb1
```

---

## **90. `parted` – Administrar Particiones de Disco**

`parted` es una herramienta avanzada para crear, modificar y eliminar particiones.

**Uso básico:**
```fish
sudo parted /dev/sdX
```

**Ejemplo:**
```fish
sudo parted /dev/sdb print
```
Esto muestra la tabla de particiones de `/dev/sdb`.

Para crear una nueva partición de 10 GB:
```fish
sudo parted /dev/sdb mkpart primary ext4 1MiB 10GiB
```

---

## **91. `df` vs `du` – Diferencia Entre Ambos Comandos**

**`df`** muestra el **espacio total y disponible en disco**.
**`du`** muestra el **tamaño real de archivos o carpetas específicas**.

**Ejemplo de `df`:**
```fish
df -h
```
Salida:
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       50G   20G   30G   40% /
```

**Ejemplo de `du`:**
```fish
du -sh ~/Descargas
```
Salida:
```
2.5G    /home/usuario/Descargas
```

Usa `df` para ver **el uso global del disco** y `du` para ver **cuánto ocupa una carpeta específica**.

---

## **92. `mount` vs `umount` – Montar y Desmontar Dispositivos**

**`mount`** se usa para montar sistemas de archivos.
**`umount`** desmonta un dispositivo de almacenamiento.

**Ejemplo de `mount`:**
```fish
sudo mount /dev/sdb1 /mnt/usb
```
Esto monta la partición `/dev/sdb1` en `/mnt/usb`.

**Ejemplo de `umount`:**
```fish
sudo umount /mnt/usb
```
Esto desmonta el dispositivo para retirarlo con seguridad.

---

## **93. `lsblk` – Mostrar Información de Dispositivos de Bloque**

`lsblk` lista los discos y particiones del sistema en formato de árbol.

**Uso básico:**
```fish
lsblk
```

 **Ejemplo de salida:**
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0  500G  0 disk
├─sda1   8:1    0  100G  0 part /
├─sda2   8:2    0  300G  0 part /home
└─sda3   8:3    0  100G  0 part [SWAP]
```
Muestra los discos, particiones y puntos de montaje.

Para ver los tamaños en formato legible:
```fish
lsblk -o NAME,SIZE,MOUNTPOINT
```

---

## **94. `fdisk` vs `parted` – Administrar Particiones**

**`fdisk`** se usa en discos con tabla **MBR** (más antiguo).
**`parted`** soporta **GPT** y es más moderno.

**Ejemplo de `fdisk`:**
```fish
sudo fdisk -l
```
Esto lista las particiones del sistema.

**Ejemplo de `parted`:**
```fish
sudo parted /dev/sdb print
```
Esto muestra las particiones de `/dev/sdb`.

**Usa `fdisk` si trabajas con MBR y `parted` para GPT**.

---

## **95. `hwinfo` – Mostrar Información del Hardware**

`hwinfo` proporciona detalles sobre el hardware del sistema.

**Uso básico:**
```fish
sudo hwinfo --short
```

 **Ejemplo de salida:**
```
cpu:
 Intel(R) Core(TM) i7-10750H CPU @ 2.60GHz
graphics card:
 NVIDIA GeForce GTX 1650
network:
 Intel Wi-Fi 6 AX201
```
Esto muestra un resumen del hardware del equipo.

Para ver información específica, usa:
```fish
sudo hwinfo --cpu
```
```fish
sudo hwinfo --disk
```

---

## **96. `lscpu` – Mostrar Información del Procesador**

`lscpu` detalla las características del CPU.

**Uso básico:**
```fish
lscpu
```

 **Ejemplo de salida:**
```
Architecture: x86_64
CPU(s): 8
Model name: Intel(R) Core(TM) i7-10750H CPU @ 2.60GHz
```
Esto muestra arquitectura, núcleos y modelo del procesador.

---

## **97. `lsusb` – Ver Dispositivos USB Conectados**

`lsusb` muestra información sobre los dispositivos USB conectados al sistema.

**Uso básico:**
```fish
lsusb
```

 **Ejemplo de salida:**
```
Bus 002 Device 003: ID 8087:0026 Intel Corp.
Bus 001 Device 002: ID 046d:c534 Logitech USB Receiver
```
Muestra los IDs y nombres de los dispositivos USB.

---

## **98. `lspci` – Mostrar Dispositivos PCI Conectados**

`lspci` lista los dispositivos PCI del sistema, como tarjetas gráficas, de sonido y de red.

**Uso básico:**
```fish
lspci
```

 **Ejemplo de salida:**
```
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics
00:14.0 USB controller: Intel Corporation Device
01:00.0 3D controller: NVIDIA Corporation GP108M [GeForce MX250]
```
Esto muestra información sobre los componentes PCI instalados.

Para obtener más detalles:
```fish
lspci -v
```

---

## **99. `dmidecode` – Ver Información del Hardware desde el BIOS**

`dmidecode` extrae datos del BIOS sobre el hardware del equipo.

**Uso básico:**
```fish
sudo dmidecode
```

**Ejemplo:**
```fish
sudo dmidecode -t system
```
Esto muestra información sobre el sistema, como el fabricante y modelo del equipo.

Para ver solo la memoria RAM instalada:
```fish
sudo dmidecode -t memory
```

---

## **100. `uptime` vs `w` – Información sobre el Tiempo de Actividad del Sistema y Usuarios**

**`uptime`** muestra cuánto tiempo lleva encendido el sistema.
**`w`** muestra información sobre los usuarios conectados y qué están haciendo.

**Ejemplo de `uptime`:**
```fish
uptime
```
Salida:
```
10:45:23 up 3 days, 4:12, 2 users, load average: 0.15, 0.12, 0.10
```

**Ejemplo de `w`:**
```fish
w
```
Salida:
```
USER     TTY      FROM           LOGIN@   IDLE   WHAT
usuario1 pts/0    192.168.1.2    10:20    1:10   fish
```
Esto muestra qué usuarios están conectados y qué comandos ejecutan.

---
