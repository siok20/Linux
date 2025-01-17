# Manual Linux - Ubuntu 
Linux recibe las instrucciones como un string.
Una entrada estándar de teclado entra como `stdin(0)`
al proceso Linux y se puede obtener una salida e monitor `stdout(1)`
o con un error `stderr(2)`. Se pueden cambiar las entradas y salidas estándar

Ejemplo de escribir un error :
El `2` indica que se escriba el error en caso exista
```bash
-> % cat doc 2> error
-> % cat error
cat: doc: No existe el archivo o el directorio
```

Se puede hacer similar con el `1` para salidas exitosas

Para no recibir ninguna salida se puede enviar al directorio `/dev/null`

```bash
-> % cat doc 2> /dev/null
```

Los comandos Linux manejan entrada estandar y salida estandar

```bash
siok@PYT [14:41:15] [~/ManualLinux] [main *]
-> % echo Hola
Hola

siok@PYT [14:41:20] [~/ManualLinux] [main *]
-> % cat ejj
cat: ejj: No existe el archivo o el directorio
```

Comandos como `cat` pueden tener entrada de ficheros


Para redireccionar la salida de un comando a un fichero se usa `>` (sobreescribe) o `>>` (agrega)

## Comandos simples

`sudo -i` : acceder a consola superusuario

`exit` : cerrar sesión del terminal

`free -mh` : Visualizar memoria

`top`: ver procesos

`htop`: visualizacón más gráfica de los procesos

`pwd`: Print Working Directory

`ls`: List, lista el contenido de un directorio

`ls [OPCIONES] [RUTA]`

`cd`: Change Directory

`clear`: limpiar la pantalla del terminal

`file` : retorna el tipo de archivo

`mkdir` : Make Directory

`mkdir [RUTA] [RUTA] ...`

`touch` : Crea un archivo vacío

`touch [RUTA] [RUTA] ...`

`cat` : Concatenate, escribe el contenido de archivos

`echo` : Imprime en la terminal o fichero

`echo Hola Linux` o `echo Hola Linux > message.txt` (Reescribe el contenido)

`echo Hola Linux >> message.txt` (Escribe en la ultima linea)


`cp` : Copy, Copia un archivo

`cp -r` :  Copy recursive, Copia un directorio recursivamente

`cp [Archivo a copiar] [RUTA DESTINO]`

`mv` : Move. Mueve ficheros

`mv [SOURCE] [DESTINY]`

`rm` : Remove files or directories `-r`

`rmdir` : Remove empty directories

`man`: Manual, visualizar documentacion de cada comando

`man [COMANDO]`

## Otros Comandos

`tail` : output the last part of files (10 lines). Para ver *x* lineas `-n x`, `-f` : Follow, muestra el cambio del contedio

`head` : Sigue la misma logica de `tail` para las primera lineas

`more` : Display the contents of a file in a terminal

`less` : Similar to more, but it has many more feature

`tree` : List contents of directories in a tree

`ln` : Make links betwwen file

`du` : Disk usage, Return the estimate file space usage

`df` : Disk free, report file system space usage

`ps` : Muestra el shell que tienes abierto

`type` : Muestra si un comando es interno o externo del shell de Linux

`history <n>` : Retorna el historial de comandos usado en la terminal (los n ultimos), `-d <n>` elimina del historial el comando de numero n

`!!` : ejecuta el ultimo comando ejecutado

`!<n>` : ejecuta el comando de numero n

`gedit <file_name>` : Abre un editor de texto (Similar al de windows)

`which <name>` : Retorna el path de name

`whereis <name>` : Retorna la ubicacion del binario, la fuente y manual de uso

`alias` : Crear un macro que apunta al comando que elijamos
Para hacerlo permanente, se debe agregar a la configuración del shell
`alias tam = 'du -sm /home/siok' `

Ten cuidado con las comillas si tienes variables en el comando: si usas comillas dobles, la variable se resuelve en el momento de definición. Si usas comillas simples, se resuelve en el momento de la invocación.

`tr` : Translate or delete characters

```bash
-> % tr a o
hola
holo
```

`wc` : print new line, word and byte counts for each file

`ping` : send request to network hosts

`ping www.google.com`

## Comandos de tiempo

`time` :  run programs and summarize system resource usage

`time [COMMAND]`

`cal` : `sudo apt-get install bsdmainutils` , nos da un calendario

`cal <año>`

`ncal` : Entrega el calendario en otro formato

`date` : print or set the system date and time

`date +'%<> %<> ...'`

`date ddmmhhmmyyyy` : Actualizar la fecha y hora del sistema

`uptime` : Tell how long the system has been running

## Comandos filtros
Necesitan entrada de otras instrucciones
`wc`, `grep`, `sort`, `diff`, `cut`, `uniq`

`uniq` : Report or emit repeated lines

`tee` : read from standard input and write to standard output and files

`grep` : escribe lineasbuscadas en ficheros

`sort` : sort lines of text files

`cut` : remove sections from each line of files

`du -a | cut -f1`

`cat /etc/passwd | cut -d ':' -f5`

`ls -l | cut -d ' ' -f3`

`ls -l | cut -c 1-10`

## Pipe

`|` Permite enviar la salida de un comando hacia otro

- Ejm: Contar la cantidad de commits en un repositorio de git

```bash
-> % git log --oneline | wc -l
12
```
## Comandos de búsqueda

`sudo apt-get plocate`

`locate` : Busca un fichero en una base de datos preindexada

`sudo updatedb` : Crea o actualiza la base de datos

`find` : search for files in a directory hierarchy

`find [OPTION] [HEAD] -name "<file_name>"`

```bash
-amin n
              File was last accessed less than, more than or exactly n minutes ago.

-atime n
              File was last accessed less than, more than or exactly  n*24  hours  ago

-executable
              Matches files which are executable and directories which are  searchable 

-user uname
              File is owned by user uname 

-size n[cwbkMG]
              File  uses  less  than, more than or exactly n units of space, rounding up.  The
              following suffixes can be used:

              `b'    for 512-byte blocks (this is the default if no suffix is used)

              `c'    for bytes

              `w'    for two-byte words

              `k'    for kibibytes (KiB, units of 1024 bytes)

              `M'    for mebibytes (MiB, units of 1024 * 1024 = 1048576 bytes)

              `G'    for gibibytes (GiB, units of 1024 * 1024 * 1024 = 1073741824 bytes)

              The + and - prefixes signify greater than and less than

-type c
              File is of type c:

              b      block (buffered) special

              c      character (unbuffered) special

              d      directory

              p      named pipe (FIFO)

              f      regular file

              l      symbolic  link; this is never true if the -L option or the -follow option
                     is in effect, unless the symbolic link is broken.  If you want to  search
                     for symbolic links when -L is in effect, use -xtype.

              s      socket

              D      door (Solaris)

              To  search  for  more than one type at once, you can supply the combined list of
              type letters separated by a comma `,' 
```

## TAR

Empaqueta archivos (Tape ARchive, porque originalmente se usaba para almacenar archivos en cintas magnéticas), actualmente puede comprimir archivos

`tar` : an archiving utility

```bash
Operation mode

-c, --create
              Create a new archive.  Arguments supply the names of the files to  be  archived.
              Directories are archived recursively, unless the --no-recursion option is given.

-t, --list
              List the contents of an archive.

-u, --update
              Append files which are newer than the corresponding copy in the archive.

-x, --extract, --get
              Extract files from an archive.  Arguments are optional
```

```bash
OPTIONS

--ignore-failed-read
              Do not exit with nonzero on unreadable files.

-f, --file=ARCHIVE
              Use archive file or device ARCHIVE.
```

## Compresores

`gzip` : No comprime directorios, solo ficheros

`gzip -k <namefile>.tar`

`gzip -l <name>` : Información de los archivos comprimidos

`gunzip` : descomprime

`bzip2` : compresses  files using the Burrows-Wheeler block sorting text compression algo‐
       rithm, and Huffman coding

`zip` : package and compress (archive) files (Compatible con Windows)

`zip -r <name> <directorio>`

`unzip <file>`

Comprimir y empaquetar:

`tar cvfz <name>.tar.gz <files>`

## Procesos
 - Un programa que se esta ejecutando
 - Linux es multitarea y multiusuario
 - Estructura jerárquica `padre-hijo`
 - Estados: 
    - Normal
    - Daemon : servicios en segundo plano
    - Zombie : procesos eliminados, aún no limpiados

- Propiedades : 
    - PID (Process ID): código único de proceso
    - UID, GID, USer ID y Group ID
    - PPID: PID del proceso Padre, excepto el proceso 1, PID1 , Systemd o init
    - Contexto: Direcciones, codigo variables, etc

- Proceso hijo: 
    - Se crean mediante `fork` del padre
    - El proceso hijo hereda algunas características del padre

    `Proceso padre (shell) -fork-> Proceso hijo (ls)`

### Comandos de procesos

`ps` : Process status
`ps -f` y `ps -f`

Todos los procesos
`ps -ef`

En forma de árbol 
`ps -ejH`

`pstree` : display a tree of processes

`sleep <time(s)>` : Pausa el proceso unos segundos

`kill` : send a signal to process

`kill -l` : list signal names

`kill -<n_signal> <PID>`

`jobs` : Muestra los trabajos que el sistema esta realizando

Un job se crea generando un proceso en segundo plano con `&`

`fg <n_job>` : traer a primer plano un job

### PRIORIDAD
`-20` la más alta hasta `+19` la más baja

`renice <new_priority> <PID>` : Cambia la prioridad de un proceso


## Abrir otra sesion

`ctrl + alt + F[3456]` : Abre una sesion de terminal virtual

Nos da la opcion de loguearnos como otro usuario además del entorno gráfico

`who` : Nos retorna los usuarios con sesion abierta

## Metacaracteres

`/usr/bin`: Fichero en el que se encuentran los metacaracteres

`*` : Reemplaza cualquier caracter(es) (Regex)

`?` : reemplza solo *un* carácter

`[]` : Reemplaza solo uno de los caracteres dentro

## Usuarios

1. `root`
2. usuarios normales
3. usuarios de sistema

`home`: directorio del usuario

Cada usuario pertenece almenos a un grupo


### Root
- `/root` : su directorio de trabajo
- Privilegios totales de sistema
- No se recomienda trabajar habitualmente con él
- Su prompt comienza con `#`

```bash
-> % sudo -i
root@PYT:~# 
root@PYT:~# exit
cerrar sesión
```

### Usuario Normal

- Los crea el root
- `/home`: su directorio

`less /etc/paswd` : Ver todos los uduarios y su id

`less /etc/group` : Ver todos los gruposq y su id

`id` : Muestra el id del usuario activo

`useradd` : Crear un usuario

`(sudo) useradd -b /home/<username>`

Cambiar la contraseña de un usuario

`(sudo) sudo passwd <username>`


#### Permisos de archivos

tipo de fichero: 
-   `-` : ficheros
-   `l` : enlaces
-   `d` : directorio
-   `b` : bloque

Permisos: 
-   `r` : Read, permiso de leer el archivo
-   `w` : Write, permiso de modificar el archivo
-   `x` : Archivo ejecutable
-   `-` : permiso inactivo

Permisos de un archivo:
 Compuesto por 9 caracteres, el primero indica el tipo de archivo, los 3 siguientes indican los permisos para el propietario del archivo, los 3 siguientes son los permisos para el grupo del autor y los últimos 3 son los permisos para otros usuarios

 `drwxr-xr-x`

 Representación numérica (octal): 
 `r = 4` , `w = 2`, `x = 1`, Suma los valores para definir el permiso

 #### Cambiar modo

 `chmod` : Change mod. Change file mode bits

 `chmod <ugoa><+-><rwx> file` 

 `chmod <representacion_octal> file`

`umask` : get file mode creation mask

`umask <n>` : set file mode creation mask

Valor máximo para ficheros `666`, se le resta la máscara `002` (en mi equipo) para darnos el valor por defecto `664`

Valor máximo para directorios `777`, se le resta la máscara `002` (en mi equipo) para darnos el valor por defecto `775`


#### Cambiar propietario y grupo

`chown` : Change file owner and group

Necesitamos permisos de `w` para modificar o ser `superusuario`

```bash
EXAMPLES
       chown root /u
              Change the owner of /u to "root".

       chown root:staff /u
              Likewise, but also change its group to "staff".

       chown -hR root /u
              Change the owner of /u and subfiles to "root".
```
`chgrp` : Cambia el grupo de un archivo


```bash
EXAMPLES
       chgrp staff /u
              Change the group of /u to "staff".

       chgrp -hR staff /u
              Change the group of /u and subfiles to "staff".
```

### Usuarios especiales

- Para ejecutar diversos procesos en el sistema. Ejm:
`bin`
- No tienen shell, usuarios de sesión `no login`

## Variables de Entorno

`printenv` : Print all or part of enviroment 

`set` : Establece o borra los valores de las opciones de shell y los parámetros
posicionales.

Para escribir el valor de una variable `printenv PWD` o `echo $PWD` (recomendado)

`$<variable>` : Reemplaza el nombre por el valor de la variable

`v=10` : Crear una variable que dura solo en la sesión del shell (no es permanente)

`$PATH` : variable de entorno en Linux que contiene una lista de directorios donde 
el sistema busca ejecutables cuando se ejecuta un comando en la terminal

para añadir un nuevo directorio en la shell

`PATH=$PATH:<Directory>`

Modificar el PROMPT(texto que aparece en la terminal y que indica que está lista para recibir comandos):

corresponde a la varibale de entorno `$PS1`



## Ficheros
Forma de guardar los datos. Usa una estructura tipo árbol


### Sistema de ficheros

`Windows`: FAT, FAT-32, EXFAT, NTFS

`Linux`: EXT2, EXT4 ...

#### EXT4
`Cuarto Sistema de Archivos Extendido`

Minix fue creado inicialmente en 1987 por Andrew S. Tanenbaum como herramienta educativa para su libro "Operating Systems Design and Implementation". Este sistema de archivos motivó a Linus Torvalds a desarrollar Linux, y algunos de sus primeros trabajos fueron escritos en MINIX.

`EXT`: (Extended) fue compuesto por Rémy Card y lanzado con el sistema operativo Linux en 1992 para superar las limitaciones de tamaño del sistema de archivos Minix. Fue rápidamente sustituido por el sistema de archivos EXT2.

`EXT2`: tiene esencialmente las mismas estructuras de metadatos que el sistema de archivos EXT. Sin embargo, EXT2 es más sencillo si tienes en cuenta la cantidad de espacio en disco que queda entre las estructuras de metadatos para su próximo uso.

`EXT3`: tenía el objetivo expreso de superar las grandes porciones de tiempo que el programa fsck necesitaba para recuperar completamente una estructura de disco saboteada. La función de registro en el diario disminuye el tiempo necesario para comprobar el disco duro en busca de incoherencias después de un fallo, pasando de días a sólo unos minutos, como máximo.  

## Enlaces

- Enlaces físicos (hard)
- Enlaces simólicos (soft)

### inodo

Fichero -> inodo (almacena información de un fichero) -> Número de inodo (Metadatos)

### Enlace físico
Identifica al mismo contenido con diferentes nombres. No es una copia separada, está apuntando al inodo

### Enlace simbólico
No contiene los datos del archivo. Apunta al registro del sitema de archivos donde encuentra los datos. Si borramos el fichero origina el enlace no funciona

