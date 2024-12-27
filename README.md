# Manual Linux - Ubuntu 

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