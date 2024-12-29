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
