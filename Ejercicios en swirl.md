# Inicio

- [Inicio](#inicio)
- [Bloques básicos](#bloques-básicos)
  - [Vectores](#vectores)
  - [Obtener ayuda](#obtener-ayuda)
- [Workspace y Archivos](#workspace-y-archivos)
  - [Espacio de trabajo](#espacio-de-trabajo)
  - [Archivos](#archivos)

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

