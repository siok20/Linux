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

`more` : Display the contents of a file in a terminalqqq

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
siok@PYT [21:20:04] [~/ManualLinux] [main]
-> % sudo -i
root@PYT:~# 
root@PYT:~# exit
cerrar sesión
```

### Usuario Normal

- Los crea el root
- `/home`: su directorio

### Usuarios especiales

- Para ejecutar diversos procesos en el sistema. Ejm:
`bin`
- No tienen shell, usuarios de sesión `no login`

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

