# Inicio

- [Inicio](#inicio)
- [Bloques básicos](#bloques-básicos)
  - [Vectores](#vectores)
  - [Obtener ayuda](#obtener-ayuda)
- [Workspace y Archivos](#workspace-y-archivos)
  - [Espacio de trabajo](#espacio-de-trabajo)
  - [Archivos](#archivos)
- [Creación de secuencias numéricas](#creación-de-secuencias-numéricas)
  - [Operador `:`](#operador-)
  - [Función `seq()`](#función-seq)
  - [Uso de la función replicar para crear una secuencia de números `rep()`](#uso-de-la-función-replicar-para-crear-una-secuencia-de-números-rep)

# Bloques básicos

R funciona en su forma más básica como una calculadora:

`5 + 7 = 12`

Aunque también se le puede asignar ese resultado a una letra para facilitar más las cosas

`x <- 5 + 7`

Después se pueden hacer operaciones usando esa letra con el resultado de la suma. 

`y <- x - 3` Dejando el resultado de y como el resultado de la operación `12 - 3 = 9`

## Vectores

Cualquier objeto que contenga objetos en R se conoce como una estructura de datos. Es así que un vector en R es:

> La estructura de datos más simple y con objetos de la misma clase, por lo tanto incluso un sólo numero es un vector de largo 1

La manera más sencilla de crear un vector es con la función `c()`, que tiene una "c" que significa concatenar o combinar. 

Por ejemplo como ejercicio se puede crear un vector con los datos 1.2, 1.1, 9 y 3.14 almacenado en la letra z de la siguiente forma:

```
z <- c(1.1, 9 , 3.14)
```

Se pueden combinar vectores para hacer nuevos vectores. Si tenemos el vector z que es `c(1.1, 9 , 3.14)`, podemos hacer lo siguiente `c(z, 555, z)` que nos genera:

```
[1]   1.10   9.00   3.14 555.00   1.10   9.00   3.14
```

Se pueden hacer también operaciones aritméticas con vectores, por ejemplo ejemplo hacer `> z * 2 + 100
`
  y esto genera lo siguiente:

```
[1] 102.20 118.00 106.28
```

De manera que se multiplica cada elemento del vector de z * 2 y luego se le suma 100.

Se puede también hacer la raíz cuadrada de `z - 1` y almacenar en la variable mysqrt de la siguiente manera:

```
> my_sqrt <- sqrt(z - 1)
```

Cuando se tienen 2 vectores del mismo largo R hace las operaciones de cada elemento por cada elemento de los vectores, si el vector es de menor largo, R recicla las operaciones hasta que alcance el largo necesario.


## Obtener ayuda

En R siempre que se tenga duda sobre lo que hace una función, se puede teclear `?`acompañado de la función sobre la que se quiere saber más. Por ejemplo, para conocer más sobre la función de concatenar `c()`, es suficiente poner en la consola:

```
?c
```
# Workspace y Archivos

## Espacio de trabajo

Para conocer el directorio que está usando actualmente la sesión de R podemos usar la siguiente función:

```
getwd()
```

Para conocer los objetos que se encuentran actualmente en el workspace de la sesión de R se usa la siguiente función:

```
ls()
```

Si lo que se quiere es conocer las carpetas o archivos que se encuentran en el directorio de trabajo usamos:

```
dir() o list.files()
```

Una manera de conocer lso argumentos que pueden usarse en una función es usando la función `args()`. Para conocer los argumentos que se pueden usar en list.files() colocamos:

```
args(list.files)
```

Se puede asignar el espacio de trabajo actual a una variable en caso de que se vaya a cambiar y se quiera guardar para su referencia, por ejemplo:

```
> old.dir <- getwd()
```

Se puede crear un directorio de trabajo dentro del directorio que te encuentras con la función `dir.create()` colocando el nombre del directorio entre comillas dentro del paréntesis:

```
> dir.create("testdir")
```

Para asignar el nuevo directorio de trabajo "testdir" al que vamos a estar usando se utiliza el comandon `setwd()`de la siguiente manera:

```
setwd("testdir")
```

## Archivos

Se pueden crear archivos dentro del directorio de trabajo con la función `file.create()`, creando el archivo "mytest.R" de la siguiente forma:

```
file.create("mytest.R")
```

Para ver que se haya creado adecuadamente usamos la función `dir()`ó `list.files()`.

Para verificar si un archivo existe se puede usar una función lógica como `file.exists()` de la siguiente manera `file.exists("mytest.R")`.

Obtener información del archivo creado se hace con la función `file.info()`de la siguiente manera:

```
file.info("mytest.R")
```

Se puede cambiar el nombre del archivo con la función `file.rename`de la siguiente manera, cambiando el nombre a mytest2.R:

```
> file.rename("mytest.R", "mytest2.R")
```

Se pueden remover los archivos con `file.remove()` por ejemplo:

```
file.remove('mytest.R')
```

Para hacer copias del archivo se usa la función `file.copy()` de la siguiente manera creando una copia de mytest2.R con el nombre de mytest3.R:

```
>  file.copy("mytest2.R", "mytest3.R")
```

Para obtener la ruta relativa de un archivo se usa la función file.path() de la siguiente manera:

```
> file.path("mytest3.R")
[1] "mytest3.R"
```

Se puede usar `file.path()`para construir rutas a directorios y archivos independientes del sistema operativo que se usa en R colocando los argumentos `'folder1'`y `'folder2'` como argumentos en `file.path()` para hacer el nombre de una ruta independiente de plataforma.

```
> file.path('folder1', 'folder2')
[1] "folder1/folder2"
```

Para poder crear directorios anidados con la función `dir.create()`es necesario que el argumento `recursive`sea `= TRUE`. Retomando la función `file.path()` junto con `dir.create()`. Crear por ejemplo un directorio llamado "testdir2" y dentro de este un "testdir3" necesitaría que se escriba el siguiente comando:

```
> dir.create(file.path('testdir2','testdir3'), recursive = TRUE)
```

Regresar a nuestro primer directorio de trabajo basta con poner el siguiente código de la ruta almacenada previamente en `old.dir`:

```
> setwd(old.dir)
```

# Creación de secuencias numéricas

## Operador `:`

La forma sencilla de crear una secuencia de números en R es con el símbolo `:`, por ejemplo para crear una secuencia del 1 al 20:

```
> 1:20
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
```

Los números que se obtienen son **integrales**, una clasificación de datos para R. 

Si lo que se quiere es obtener una secuencia de números **reales** se puede realizar de la siguiente forma integrando un número que tiene decimales `pi:10`:

```
> pi:10
[1] 3.141593 4.141593 5.141593 6.141593 7.141593 8.141593 9.141593
```
Debido a que el límite superior es 10 y el siguiente número será mayor a 10, la secuencia se detiene en el 9.

También se pueden obtener secuencias de regreso o en disminución, por ejemplo `15:1`sería:

```
> 15:1
 [1] 15 14 13 12 11 10  9  8  7  6  5  4  3  2  1
```
Para **dudas** en caso de algunas funciones de operadores se puede utilizar el comando de la siguiente manera:

```
> ?`:`
```

## Función `seq()`

En su función más básica nos permite realizar las mismas funciones que `:`

```
> seq(1, 20)
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
```

Por otro lado, si lo que queremos es una secuencia de números del 1 al 10 pero que sea en una frecuencia de 0.5 se utilizaría de la siguiente manera:

```
> seq(0, 10, by = 0.5)
 [1]  0.0  0.5  1.0  1.5  2.0  2.5  3.0  3.5  4.0  4.5  5.0  5.5  6.0  6.5  7.0
[16]  7.5  8.0  8.5  9.0  9.5 10.0
```

También se le puede pedir a la función que haga una secuencia de números del 1 al 10, pero con una secuencia de 30 números hasta llegar al 10: 

```
> my_seq <- seq(5, 10, length = 30)
```

En este caso lo almacenamos en la variable my_seq.

Para comprobar el largo del objeto podemos utilizar la función de `length`:

```
> length(my_seq)
[1] 30
```

Ahora que se conoce que el largo del objeto "my_seq" es de 30, podemos usarlo para generar secuencias que lleguen hasta 30 de distintas formas. 

1. Usando el comando `:`y la función `lenght()`: 
```
> 1:length(my_seq)
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27
[28] 28 29 30
```
2. Usando la función `seq()` con el argumento `along.with`:
```
> seq(along.with = my_seq)
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27
[28] 28 29 30
```
3. La más sencilla es usando la función `seq_along()`:
```
> seq_along(my_seq)
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27
[28] 28 29 30
```
## Uso de la función replicar para crear una secuencia de números `rep()`

En caso de que se desee repetir un número una cantidad determinada de veces se usa la función `rep()`con el argumento `times =`de la siguiente forma:

```
> rep(0, times = 40)
 [1] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
```

Si en lugar de eso queremos que nuestro vector tenga 10 repeticiones del vector `c(0, 1, 2)`, se hace de la siguiente forma:

```
> rep(c(0, 1, 2), times = 10)
 [1] 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2
```

Para ahora hacer que se repita cada número del vector `c(0, 1, 2)`10 veces, hacemos lo siguiente:

```
> rep(c(0, 1, 2), each = 10)
 [1] 0 0 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 
```