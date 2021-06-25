# Indice

- [Indice](#indice)
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
- [Vectores](#vectores-1)
  - [Vectores atómicos](#vectores-atómicos)
    - [Vectores lógicos](#vectores-lógicos)
    - [Vectores de de carácter](#vectores-de-de-carácter)
- [Valores ausentes](#valores-ausentes)
  - [Valores NaN](#valores-nan)
- [Subsetting de valores con vectores índice](#subsetting-de-valores-con-vectores-índice)
  - [Vectores índice lógicos](#vectores-índice-lógicos)
    - [Extracción de valores que no son NA](#extracción-de-valores-que-no-son-na)
  - [Vectores índice lógicos](#vectores-índice-lógicos-1)
  - [Vectores índice integrales positivos](#vectores-índice-integrales-positivos)
  - [Vectores integrales negativos](#vectores-integrales-negativos)
  - [Vectores índice de secuencias de carácteres](#vectores-índice-de-secuencias-de-carácteres)
- [Matrices y Data Frames](#matrices-y-data-frames)

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

```R
z <- c(1.1, 9 , 3.14)
```

Se pueden combinar vectores para hacer nuevos vectores. Si tenemos el vector z que es `c(1.1, 9 , 3.14)`, podemos hacer lo siguiente `c(z, 555, z)` que nos genera:

```R
[1]   1.10   9.00   3.14 555.00   1.10   9.00   3.14
```

Se pueden hacer también operaciones aritméticas con vectores, por ejemplo ejemplo hacer `> z * 2 + 100
`
  y esto genera lo siguiente:

```R
[1] 102.20 118.00 106.28
```

De manera que se multiplica cada elemento del vector de z * 2 y luego se le suma 100.

Se puede también hacer la raíz cuadrada de `z - 1` y almacenar en la variable mysqrt de la siguiente manera:

```R
> my_sqrt <- sqrt(z - 1)
```

Cuando se tienen 2 vectores del mismo largo R hace las operaciones de cada elemento por cada elemento de los vectores, si el vector es de menor largo, R recicla las operaciones hasta que alcance el largo necesario.


## Obtener ayuda

En R siempre que se tenga duda sobre lo que hace una función, se puede teclear `?`acompañado de la función sobre la que se quiere saber más. Por ejemplo, para conocer más sobre la función de concatenar `c()`, es suficiente poner en la consola:

```R
?c
```
# Workspace y Archivos

## Espacio de trabajo

Para conocer el directorio que está usando actualmente la sesión de R podemos usar la siguiente función:

```R
getwd()
```

Para conocer los objetos que se encuentran actualmente en el workspace de la sesión de R se usa la siguiente función:

```R
ls()
```

Si lo que se quiere es conocer las carpetas o archivos que se encuentran en el directorio de trabajo usamos:

```R
dir() o list.files()
```

Una manera de conocer lso argumentos que pueden usarse en una función es usando la función `args()`. Para conocer los argumentos que se pueden usar en list.files() colocamos:

```R
args(list.files)
```

Se puede asignar el espacio de trabajo actual a una variable en caso de que se vaya a cambiar y se quiera guardar para su referencia, por ejemplo:

```R
> old.dir <- getwd()
```

Se puede crear un directorio de trabajo dentro del directorio que te encuentras con la función `dir.create()` colocando el nombre del directorio entre comillas dentro del paréntesis:

```R
> dir.create("testdir")
```

Para asignar el nuevo directorio de trabajo "testdir" al que vamos a estar usando se utiliza el comandon `setwd()`de la siguiente manera:

```R
setwd("testdir")
```

## Archivos

Se pueden crear archivos dentro del directorio de trabajo con la función `file.create()`, creando el archivo "mytest.R" de la siguiente forma:

```R
file.create("mytest.R")
```

Para ver que se haya creado adecuadamente usamos la función `dir()`ó `list.files()`.

Para verificar si un archivo existe se puede usar una función lógica como `file.exists()` de la siguiente manera `file.exists("mytest.R")`.

Obtener información del archivo creado se hace con la función `file.info()`de la siguiente manera:

```R
file.info("mytest.R")
```

Se puede cambiar el nombre del archivo con la función `file.rename`de la siguiente manera, cambiando el nombre a mytest2.R:

```R
> file.rename("mytest.R", "mytest2.R")
```

Se pueden remover los archivos con `file.remove()` por ejemplo:

```R
file.remove('mytest.R')
```

Para hacer copias del archivo se usa la función `file.copy()` de la siguiente manera creando una copia de mytest2.R con el nombre de mytest3.R:

```R
>  file.copy("mytest2.R", "mytest3.R")
```

Para obtener la ruta relativa de un archivo se usa la función file.path() de la siguiente manera:

```R
> file.path("mytest3.R")
[1] "mytest3.R"
```

Se puede usar `file.path()`para construir rutas a directorios y archivos independientes del sistema operativo que se usa en R colocando los argumentos `'folder1'`y `'folder2'` como argumentos en `file.path()` para hacer el nombre de una ruta independiente de plataforma.

```R
> file.path('folder1', 'folder2')
[1] "folder1/folder2"
```

Para poder crear directorios anidados con la función `dir.create()`es necesario que el argumento `recursive`sea `= TRUE`. Retomando la función `file.path()` junto con `dir.create()`. Crear por ejemplo un directorio llamado "testdir2" y dentro de este un "testdir3" necesitaría que se escriba el siguiente comando:

```R
> dir.create(file.path('testdir2','testdir3'), recursive = TRUE)
```

Regresar a nuestro primer directorio de trabajo basta con poner el siguiente código de la ruta almacenada previamente en `old.dir`:

```R
> setwd(old.dir)
```

# Creación de secuencias numéricas

## Operador `:`

La forma sencilla de crear una secuencia de números en R es con el símbolo `:`, por ejemplo para crear una secuencia del 1 al 20:

```R
> 1:20
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
```

Los números que se obtienen son **integrales**, una clasificación de datos para R. 

Si lo que se quiere es obtener una secuencia de números **reales** se puede realizar de la siguiente forma integrando un número que tiene decimales `pi:10`:

```R
> pi:10
[1] 3.141593 4.141593 5.141593 6.141593 7.141593 8.141593 9.141593
```
Debido a que el límite superior es 10 y el siguiente número será mayor a 10, la secuencia se detiene en el 9.

También se pueden obtener secuencias de regreso o en disminución, por ejemplo `15:1`sería:

```R
> 15:1
 [1] 15 14 13 12 11 10  9  8  7  6  5  4  3  2  1
```
Para **dudas** en caso de algunas funciones de operadores se puede utilizar el comando de la siguiente manera:

```R
> ?`:`
```

## Función `seq()`

En su función más básica nos permite realizar las mismas funciones que `:`

```R
> seq(1, 20)
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
```

Por otro lado, si lo que queremos es una secuencia de números del 1 al 10 pero que sea en una frecuencia de 0.5 se utilizaría de la siguiente manera:

```R
> seq(0, 10, by = 0.5)
 [1]  0.0  0.5  1.0  1.5  2.0  2.5  3.0  3.5  4.0  4.5  5.0  5.5  6.0  6.5  7.0
[16]  7.5  8.0  8.5  9.0  9.5 10.0
```

También se le puede pedir a la función que haga una secuencia de números del 1 al 10, pero con una secuencia de 30 números hasta llegar al 10: 

```R
> my_seq <- seq(5, 10, length = 30)
```

En este caso lo almacenamos en la variable my_seq.

Para comprobar el largo del objeto podemos utilizar la función de `length`:

```R
> length(my_seq)
[1] 30
```

Ahora que se conoce que el largo del objeto "my_seq" es de 30, podemos usarlo para generar secuencias que lleguen hasta 30 de distintas formas. 

1. Usando el comando `:`y la función `lenght()`: 

```R
> 1:length(my_seq)
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27
[28] 28 29 30
```

2. Usando la función `seq()` con el argumento `along.with`:

```R
> seq(along.with = my_seq)
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27
[28] 28 29 30
```

3. La más sencilla es usando la función `seq_along()`:

```R
> seq_along(my_seq)
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27
[28] 28 29 30
```

## Uso de la función replicar para crear una secuencia de números `rep()`

En caso de que se desee repetir un número una cantidad determinada de veces se usa la función `rep()`con el argumento `times =`de la siguiente forma:

```R
> rep(0, times = 40)
 [1] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
```

Si en lugar de eso queremos que nuestro vector tenga 10 repeticiones del vector `c(0, 1, 2)`, se hace de la siguiente forma:

```R
> rep(c(0, 1, 2), times = 10)
 [1] 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2
```

Para ahora hacer que se repita cada número del vector `c(0, 1, 2)`10 veces, hacemos lo siguiente:

```R
> rep(c(0, 1, 2), each = 10)
 [1] 0 0 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 
```

# Vectores

La estructura de dato más sencilla en R se llama **vector**. Los vectores pueden representarse de 2 maneras en R:

1. Atómicos: Solamente contienen un tipo o clase objeto. 
2. Listas: Contiene múltiples tipos de datos. 

## Vectores atómicos

Los vectores atómicos se clasifican en R de la siguiente manera:

- Numéricos: Vectores que contienen números que usan decimales. 
- Integrales: Vectores que contienen números que son enteros.
- Lógicos: Contienen los valores `FALSE`, `TRUE` ó `NA`, se generan como resultado de condiciones lógicas.
- Complejos
- Carácter: Vectores que contienen letras y con comillas `" "`.

### Vectores lógicos

Para entender como funcionen los vectores lógicos vamos a generar un vector numérico:

```R
> num_vect <- c(0.5, 55, -10, 6)
```

Posteriormente se creará la variable `tf`que contenga el resultado de la condición lógica `num_vect < 1`, es decir si alguno de los números almacenados en ese vector son menores a 1:

```R
> tf <- num_vect < 1
> tf
[1]  TRUE FALSE  TRUE FALSE
```

Por lo tanto `tf`es un vector lógico de longitud 4, con los valores `TRUE FALSE  TRUE FALSE`.

Otra manera es ver si algún valor del vector es mayor o igual a 6 de la siguiente manera:

```R
> num_vect >= 6
[1] FALSE  TRUE FALSE  TRUE
```
Los operadores lógicos con los que se pueden realizar esas operaciones condicionales son: `<`, `>=`, `>`, `<=`, `==` (para igualdad exacta) y `!=` (para desigualdades).

Para dos expresiones lógicas, A y B, se puede preguntar **si una es verdadera** con `A | B` (lógica 'o' a.k.a 'unión') ó **si ambas son verdaderas** con `A & B` (lógica 'y' a.k.a 'intersección'). La negación de A es `!A` y es verdadera cuando A es `FALSE` y es falsa cuando A `TRUE`.

> El símbolo de `!`niega todo lo que viene después de el.

### Vectores de de carácter

Se usan las comillas dobles `" "`para distinguir los objetos que son caractéres. Para crear un vector de carácter con el siguiente contenido `"My", "name", "is"` usamos lo siguiente: 

```R
> my_char <- c("My", "name", "is")
> my_char
[1] "My"   "name" "is" 
```

Es un vector con una longitud de 3, ya que tienes 3 carácteres diferentes identificados cada uno con las dos comillas. Para unirlos podemos usar la función de `paste()`con su argumento `collapse = " "`, las dos comillas y el espacio del argumento colapse le dicen a R que cuando pegue los caractéres los separe con espacio:

```R
> paste(my_char, collapse = " ")
[1] "My name is"
```

Falta agregar el nombre a "My name is" y esto lo haremos guardándolo en la variable `my_name <–` de la siguiente manera: 

```R
> my_name <- c(my_char, "Julio")
> my_name
[1] "My"    "name"  "is"    "Julio"
```

Ahora hay que pegar los objetos con la función `paste()` y el argumento `collapse = " "`. 

```R
> paste(my_name, collapse = " ")
[1] "My name is Julio"
```

Otro argumento de la función `paste()` es el de `sep =`que nos puede ayudar a juntar objetos de carácter muy simples de longitud 1 cada uno. de la siguiente manera:

```R
> paste("Hello", "world!", sep = " ")
[1] "Hello world!"
```

También podemos pegar vectores que son de diferente **clase** y de la misma longitud. Por ejemplo vamos a pegar un vector integral con la secuencia 1:3 con un vector de carácter que tiene c("X", "Y", "Z") de la siguiente manera y sin dejar espacio en el argumento `sep`:

```R
> paste(c(1:3), c("X", "Y", "Z"), sep = "")
[1] "1X" "2Y" "3Z"
```

Si pegamos vectores de diferente longitud ocurre algo que se mencioná en los ejemplos anteriores, **se reciclan** los vectores. Por ejemplo, al usar usar `paste(LETTERS, 1:4, sep = "-")`, `LETTERS` es un argumento que contiene todas las letras del alfabeto en inglés, por lo que es un vector grande. Mientras que el vector de `1:4`es solamente de longitud de 4. Esto hace que los numeros se _reciclen_ entre las letras del alfabeto:

```R
> paste(LETTERS, 1:4, sep = "-")
 [1] "A-1" "B-2" "C-3" "D-4" "E-1" "F-2" "G-3" "H-4" "I-1" "J-2" "K-3" "L-4" "M-1"
[14] "N-2" "O-3" "P-4" "Q-1" "R-2" "S-3" "T-4" "U-1" "V-2" "W-3" "X-4" "Y-1" "Z-2"
```

# Valores ausentes

En el lenguaje de R se usa `NA`para denotar que un valor no se encuentra disponible o está ausente. En R todas las operaciones aritméticas que se hagan con un `NA` dan como resultado `NA`. 

```R
> x <- c(44, NA, 5, NA)
> x * 3
[1] 132  NA  15  NA
```

La función `is.na()`nos ayuda a ver si un vector con tiene algún objeto que sea NA. Por ejemplo:

Creamos un vector de 1000 elementos de una distribución estándar normal `y <- rnorm(1000)`, posteriormente hacemos otro vector que tenga 1000 NA `z <- rep(NA, 1000)`. Posteriormente vamos a seleccionar 100 elementos aleatorios de estos 2000 valores creados almacenándolo en `my_data` con lo siguiente `> my_data <- sample(c(y, z), 100)`. Ahora para saber dónde se encuentran los NA en nuestros datos tenemos usamos la función `is.na()` en `my_data`, asignando el resultado a `my_na`:

```R
> my_na <- is.na(my_data)
> my_na
  [1] FALSE FALSE  TRUE FALSE  TRUE  TRUE  TRUE FALSE FALSE FALSE  TRUE FALSE FALSE
 [14]  TRUE  TRUE FALSE  TRUE FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE FALSE  TRUE
 [27] FALSE FALSE  TRUE FALSE  TRUE  TRUE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE
 [40] FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE  TRUE
 [53] FALSE FALSE FALSE  TRUE FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE
 [66] FALSE  TRUE FALSE FALSE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE
 [79]  TRUE  TRUE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE  TRUE  TRUE FALSE FALSE
 [92]  TRUE FALSE  TRUE FALSE  TRUE  TRUE  TRUE FALSE  TRUE
```

Todos los **TRUE** significan que hay un NA, los **FALSE** indican que ahí no hay NA. 

Es importante tener cuidado al usar operadores lógicos con vectores que tienen NAs ya que la presencia de uno sólo puede provocar que todo el vector de como resultado que todos son NA. 

Ahora que tenemos el objeto `my_na` podemos contar el número de **NA** que se encuentran en el. Bajo la superficie es importante saber que para R los **TRUE** son **1**, mientras que los **FALSE** son **0**. Si hacemos una suma del total de TRUE y FALSE podemos obtener la cantidad de NA en los datos.

Para esto podemos usar la función `sum()`con `my_na` lo que nos dará como resultado la cantidad de NA:

```R
> sum(my_na)
[1] 49
```
## Valores NaN 

Los valores NAN significan _not a number_ y se generan por ejemplo haciendo operaciones que no dan un resultado como:

```R
> 0 / 0
[1] NaN
```

Otro ejemplo es que para R `Inf`representa un valor infinito, si hacemos la diferencia de `Inf - Inf`:

```R
> Inf - Inf
[1] NaN
```

# Subsetting de valores con vectores índice

En el caso de R, **subsetting** se refiere a la extracción de valores específicos de un vector dependiendo de algunas condiciones. 

Supongamos que tenemos el siguiente vector con 20 números y 20 NA:

```R
> x
 [1]          NA  1.35954896          NA -0.81664922 -0.85922400          NA
 [7] -2.45294623          NA          NA  0.07564971          NA          NA
[13]          NA -0.82627086  0.45857193 -0.74819678  0.65014088          NA
[19]          NA -0.62306322          NA          NA          NA          NA
[25]          NA          NA  0.10665745 -0.02834942 -1.72736205          NA
[31]  0.15754476          NA -1.13329540          NA -1.03587386  1.39174943
[37]  0.75355579          NA -1.05937151  0.13258668
```

La manera de decirle a R que queremos solamente una porción de datos del vector (subset), es colocando `[ ]` inmediatamente después del vector, con el rango que nos interesa, dendo de los corchetes se coloca el rango de números `[num:num]` que se llama **vector índice**.

Para extraer los primeros 10 elementos del vector x podemos usar `x[1:10]`:

```R
> x[1:10]
 [1]          NA  1.35954896          NA -0.81664922 -0.85922400          NA
 [7] -2.45294623          NA          NA  0.07564971
```

Existen 4 tipos de vectores índice:

- Vectores lógicos
- Vectores de integrales positivos
- Vectores de integrales negativos
- Vectores de secuencias de caracteres

## Vectores índice lógicos 

### Extracción de valores que no son NA
Cuando se trabaja con bases de datos reales es frecuente encontrar que trabajan con valores `NA` y lo que se quiere es extraer todos los elementos de la base de datos que no sean `NA`. Usar `is.na()`nos da un vector con los valores `TRUE (NA)` ó `FALSE (no es NA)` del largo del vector que se coloque en el paréntesis.

Usar `is.na()` en un subsetting de un vector particular de ínteres, genera otro vector con el largo de números `NA` que tenga. Por ejemplo, para extraer solamente los `NA`del vector `x`:

```R
> x[is.na(x)]
 [1] NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA
```

Recordando que el operador lógico `!` es la negación de una expresión lógica, podemos decir que `!is.na()` buscará los valores que **no** sean `NA`. Por lo que para crear un vector que contenga solamente los valores que no son `NA` del vector `x`usamos:

```R
> y <- x[!is.na(x)]
> y
 [1]  1.35954896 -0.81664922 -0.85922400 -2.45294623  0.07564971 -0.82627086
 [7]  0.45857193 -0.74819678  0.65014088 -0.62306322  0.10665745 -0.02834942
[13] -1.72736205  0.15754476 -1.13329540 -1.03587386  1.39174943  0.75355579
[19] -1.05937151  0.13258668
```

## Vectores índice lógicos

Tenemos el vector `y`con algunos valores de los cuáles queremos extraer algunos que sigan una condición lógica. En este caso será `y > 0`. Si lo hicieramos solamente así nos regresaría un vector del largo de `y` con `TRUE` y `FALSE` el número de veces que un valor sea mayor o menor a 0. 

Por otro lado, como en el caso anterior si usamos `y[y > 0]`, nos regresará un vector con contiene todos los valores positivos y por lo tanto `> 0`:

```R
> y[y > 0]
[1] 1.35954896 0.07564971 0.45857193 0.65014088 0.10665745 0.15754476 1.39174943
[8] 0.75355579 0.13258668
```

Es importante recordar que usar operadores lógicos con un vector que contiene `NA`, regresará un vector con los `NA`, por lo que es mejor primero remover los `NA` del vector` antes de usar el operador lógico:

```R
> x[x > 0]
 [1]         NA 1.35954896         NA         NA         NA         NA 0.07564971
 [8]         NA         NA         NA 0.45857193 0.65014088         NA         NA
[15]         NA         NA         NA         NA         NA         NA 0.10665745
[22]         NA 0.15754476         NA         NA 1.39174943 0.75355579         NA
[29] 0.13258668
```

Debido a que `NA`no es un valor, si no una etiqueta para un valor ausente, nos regresa los números mayores a 0 y los `NA`.

Así regresando al vector de `x`si queremos pedirle que nos regrese un vector de valores que no sean NA y mayores a 0 podemos hacer lo siguiente combinando los operadores que hemos usado:

```R
> x[!is.na(x) & x > 0]
[1] 1.35954896 0.07564971 0.45857193 0.65014088 0.10665745 0.15754476 1.39174943
[8] 0.75355579 0.13258668
```

## Vectores índice integrales positivos

Así como se usa la secuencia `x[1:10]`para extraer los primeros 10 valores del vector `x`, podemos pedir que se extraigan solamente ciertos valores, por ejemplo el `3, 5 y 7`. Lo hacemos creando el vector `c(3, 5, 7)` y aplicándoselo a `x` con el operador para hacer subsetting `[ ]`:

```R
> x[c(3, 5, 7)]
[1]        NA -0.859224 -2.452946
```

## Vectores integrales negativos

Si queremos extraer todos los elementos del vector `x` pero no  el `2`y `10` podemos usar un vector integrales negativos, en este caso `c(-2, -10)`que lo pondríamos dentro del operador para hacer subsetting `[ ]`:

```R
> x[c(-2, -10)]
 [1]          NA          NA -0.81664922 -0.85922400          NA -2.45294623
 [7]          NA          NA          NA          NA          NA -0.82627086
[13]  0.45857193 -0.74819678  0.65014088          NA          NA -0.62306322
[19]          NA          NA          NA          NA          NA          NA
[25]  0.10665745 -0.02834942 -1.72736205          NA  0.15754476          NA
[31] -1.13329540          NA -1.03587386  1.39174943  0.75355579          NA
[37] -1.05937151  0.13258668
```

Si se va a usar un vector con varios integrales negativos podemos poner el `-`antes de `c()`de la siguiente manera `x[-c(2, 10)]`. 

## Vectores índice de secuencias de carácteres

Estos se usan cuando los vectores tienen elementos con **nombre**, por ejemplo vamos a hacer un vector que tiene valores unidos a unos nombres:

```R
> vect <- c(foo = 11, bar = 2, norf = NA)
```

Podemos ver al imprimir `vect` que cada elemento tiene un nombre:

```R
> vect
 foo  bar norf 
  11    2   NA 
```

Para obtener solamente los nombres del vector `vect`usamos la función `names()`:

```R
> names(vect)
[1] "foo"  "bar"  "norf"
```

También podemos crear un vector sin nombre `> vect2 <- c(11, 2, NA)` y después añadirle el nombre a sus elementos con la función `names()`:

```R
> names(vect2) <- c("foo", "bar", "norf")
```

Podemos ver si ambos vectores son iguales con la función `identical()`:

```R
> identical(vect, vect2)
[1] TRUE
```

Ahora que los elementos de los vectores `x`y `y`están asociados a nombres, podemos hacer un subsetting por carácteres en el que pidamos un determinado valor dentro del vector. Por ejemplo para pedir el elemento que se llama `bar`:

```R
> vect["bar"]
bar 
  2 
```

También podemos pedirle con un vector de nombres:

```R
> vect[c("foo", "bar")]
foo bar 
 11   2 
```

# Matrices y Data Frames