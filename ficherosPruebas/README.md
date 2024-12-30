# Pruebas de comandos con ficheros

## tr

1. Preparamos un fichero
```bash
-> % echo Fichero de prueba > prueba1.txt
-> % cat prueba1.txt 
Fichero de prueba
```

2. Sustiemos las e por x (El documento original no se modifica)
```bash
-> % tr e x < prueba1.txt 
Fichxro dx pruxba
```

3. Un texto màs amplio
```bash
-> % echo Mas pruebas para mostrar >> prueba1.txt 
-> % cat prueba1.txt 
Fichero de prueba
Mas pruebas para mostrar
```

- Reemplazar caaracteres hasta una palabra específica

```bash
tr a e << end
> una
> dos
> cuatro
> alfa
> end
une
dos
cuetro
elfe
```

## wc

Probamos `wc` con el anterior documento

```bash
-> % wc < prueba1.txt
 2  7 43
-> % wc < README.md 
 25  80 438
```

- Byte counts
```bash
-> % wc -c < prueba1.txt
43
```
- Character counts
```bash
-> % wc -m < prueba1.txt
43
```

- Newline counts
```bash
-> % wc -l < prueba1.txt
2
```
- max line lenght
```bash
-> % wc -L < prueba1.txt
24
```

- Word counts
```bash
-> % wc -w < prueba1.txt
7
```

- Contar lineas hasta una palabra específica

```bash
$ wc << ult
> as
> al
> be
> tr
> ult
      4       4      12
```

## Pipe

```bash
-> % cat prueba1.txt | tr a p
Fichero de pruebp
Mps pruebps pprp mostrpr
```

`tr` espera la salida de `cat` (el contenido de `prueba1.txt.`) como su entrada

```bash
-> % cat prueba1.txt | tr a p | wc
      2       7      43
```
Generamos un `pipeline` en la que combinamos más de dos comandos


## uniq

Creamos un archivo `prueba2.txt` 

```bash
-> % gedit prueba2.txt 
```

 con el siguiente texto

```
juan
juan
juan
jose
ana
ana
sebas
sebas
jose
jose
```

Usamos el comando `uniq` (solo considera filas consecutivas)

```bash
-> % cat prueba2.txt | uniq
juan
jose
ana
sebas
jose
```
Para contar la recurrencia

```bash
-> % cat prueba2.txt | uniq -c
      3 juan
      1 jose
      2 ana
      2 sebas
      2 jose
```
Solo mostrar los repetidos

```bash
-> % cat prueba2.txt | uniq -d
juan
ana
sebas
jose
```

## tee

prueba con tee

```bash
-> % ping www.google.com | tee prueba3.txt
PING www.google.com (64.233.186.103) 56(84) bytes of data.
```

## grep
Buscar la palabra `ana` en los ficheros de la caroeta de trabajo
```bash
grep ana *
prueba2.txt:ana
prueba2.txt:ana
README.md:ana
README.md:ana
README.md:ana
README.md:      2 ana
README.md:ana
```
Buscar la palabara `error` en los logs del sistema
```bash
-> % grep -s error /var/log/*.log
```

BUscar los ficheros donde aparece la palabra `error`
```bash
-> % grep -sl error /var/log/*.log
/var/log/apport.log
/var/log/auth.log
/var/log/kern.log
```
Buscar los ficheros donde aparece la palabra `error` y su concurrencia

```bash
-> % grep -sc error /var/log/*.log
/var/log/alternatives.log:0
/var/log/apport.log:1
/var/log/auth.log:107
/var/log/bootstrap.log:0
/var/log/cloud-init.log:0
/var/log/cloud-init-output.log:0
/var/log/dpkg.log:0
/var/log/fontconfig.log:0
/var/log/gpu-manager.log:0
/var/log/kern.log:3
/var/log/ubuntu-advantage-apt-hook.log:0
/var/log/vbox-setup.log:0
```
Utilizandolo con pipe
```bash
-> % ls -l | grep error
-rw-rw-r-- 1 siok siok   47 dic 29 17:21 error
```

## sort

Ordenar las lineas de un fichero
```bash
-> % sort prueba2.txt
ana
ana
jose
jose
jose
juan
juan
juan
sebas
sebas
```

Con un output
```bash
-> % sort prueba2.txt -o sort_prueba2.txt
```

Con un pipe 

```bash
-> % ls | sort            
error
prueba1.txt
prueba2.txt
prueba3.txt
README.md
sort_prueba2.txt
```

Ordenar en un orden inverso

```bash
-> % ls | sort -r         
sort_prueba2.txt
README.md
prueba3.txt
prueba2.txt
prueba1.txt
error
```

ordenar por orden numerico

```bash
-> % du -ah | sort -n  
4,0K	./error
4,0K	./prueba1.txt
4,0K	./prueba2.txt
4,0K	./prueba3.txt
4,0K	./README.md
4,0K	./sort_prueba2.txt
28K   	.
```