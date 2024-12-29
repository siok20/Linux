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