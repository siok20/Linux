# Practica inodos

## Hard Links

Crea un archivo simple con un texto

```bash
siok@PYT [18:37:49] [~/ManualLinux/inodo] [main *]
-> % echo Hola > file1.txt

siok@PYT [18:38:51] [~/ManualLinux/inodo] [main *]
-> % ls -l
total 4
-rw-rw-r-- 1 siok siok 5 dic 27 18:38 file1.txt
```

El nombre `file1.txt` apunta a un bloque de datos 

Creamos con un hard link con el comando `ln [TARGET] [LINK NAME]`

```bash
siok@PYT [18:38:52] [~/ManualLinux/inodo] [main *]
-> % ln file1.txt hard_file1.txt

siok@PYT [18:42:41] [~/ManualLinux/inodo] [main *]
-> % ls -l                      
total 8
-rw-rw-r-- 2 siok siok 5 dic 27 18:38 file1.txt
-rw-rw-r-- 2 siok siok 5 dic 27 18:38 hard_file1.txt
```

Comprobar el número de inodo con el comando `ls -li` 

```bash
siok@PYT [18:46:10] [~/ManualLinux/inodo] [main *]
-> % ls  -li          
total 12
3414894 -rw-rw-r-- 2 siok siok   5 dic 27 18:38 file1.txt
3414894 -rw-rw-r-- 2 siok siok   5 dic 27 18:38 hard_file1.txt
```

Comprobar cambio de contenido

Agregamos contenido a `file1.txt`

```bash
% echo Adios >> file1.txt
```

Comprobamos el contenido en ambos ficheros

```bash
siok@PYT [18:53:34] [~/ManualLinux/inodo] [main *]
-> % cat file1.txt     
Hola
Adios

siok@PYT [18:53:36] [~/ManualLinux/inodo] [main *]
-> % cat hard_file1.txt
Hola
Adios
```

## Soft Links

Creamos el enlace simbólico con el comando `ln -s` (symbolic)

```bash 
% ln -s file1.txt soft_file1.txt
```

Comprobamos el tipo de archivo

```bash
siok@PYT [18:56:49] [~/ManualLinux/inodo] [main *]
-> % ls -li
total 12
3414894 -rw-rw-r-- 2 siok siok  11 dic 27 18:48 file1.txt
3414894 -rw-rw-r-- 2 siok siok  11 dic 27 18:48 hard_file1.txt
3414896 -rw-rw-r-- 1 siok siok 949 dic 27 18:47 README.md
3414903 lrwxrwxrwx 1 siok siok   9 dic 27 18:56 soft_file1.txt -> file1.txt
```