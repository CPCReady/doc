# Listado de Comandos

Podemos ejecutar **CPCReady** desde el shell con uno de los siguientes comando que estan disponibles: cpc, cpcr o bien cpcready

Disponesmos de los siguientes comandos con sus opciones

* [build](#build)
* [info](#info)
* [palette](#palette)
* [project](#project)
* [run](#run)
* [screen](#screen)
* [sprite](#sprite)
* [about](#about)
* [help](#help)

<a name="help"></a>
## help

Si queremos que nos muestre la ayuda de **CPCReady** ejecutaremos el comando

```sh
cpcready --help

Usage: cpcready [OPTIONS] COMMAND [ARGS]...

  CLI SDK for programming in Amstrad Locomotive Basic and Compiled Basic with
  Ugbasic.

Options:
  --version  Show the version and exit.
  --help     Show this message and exit.

Commands:
  build    Create project disk and cdt image.
  info     Show infor CPCReady.
  palette  Extract the color palette from the image.
  project  Create the project structure for CPCReady.
  run      Execute DSK/CDT in emulator.
  screen   Convert an image to Amstrad scr format.
  sprite   Extract the color palette from the image.

```

Si lo que queremos es que nos muestre la ayuda de cada uno de los comandos, pasaremos el parametro --help por el comando en cuestion. Por ejemplo:

```sh
cpcready palette --help

Usage: cpcready palette [OPTIONS]

  Extract the color palette from the image.

Options:
  -i, --image TEXT    Input file name  [required]
  -m, --mode [0|1|2]  Image Mode (0, 1, 2)  [required]
  --help   

```
<a name="build"></a>
## build

El comando **build** generará las imagenes DSK, CDT y archivos para la M4 Board en base a las configuraciones (cfg) y ficheros de nuestro proyecto.

```sh
cpcready build --scope all

```

| Parametro | Requerido |Opciones|Descripción |
| ------ | ------ | ------ |------ |
| `-s, --scope` | False | dsk, cdt, all|Alcance de nuestra generacion de imagenes. Si el comando le ejecutamos sin parametro se genera todo (DSK, CDT), si ponemos parametro tendremos que indicar una de las siguientes opciones dsk, cdt o all para todo.|

**parametros**

`-s, --scope`
Alcance de nuestra generacion de imagenes. Si el comando le ejecutamos sin parametro se genera todo (DSK, CDT), si ponemos parametro tendremos que indicar una de las siguientes opciones dsk, cdt o all para todo.


<a name="palette"></a>
## palette

El comando **palette** nos mostrara por consola la paleta de colores de nuestra imagen en base al mode seleccionado.

```sh
cpcready palette --image /home/amstrad/image.png --mode 0

```

**parametros**

`-i, --image`
Ruta de la imagen.

`-m, --mode` 
Mode (0,1 o 2) para el que queremos nuestra paleta de colores.

<a name="screen"></a>
## screen

El comando **screen** nos generara nuestra archivo imagen SCR preparado para ejecutar en cualquier Amstrad.

```sh
cpcready screen --image /home/amstrad/image.png --mode 0 --out /home/amstrad/scr --dsk

```

**parametros**

`-i, --image`
Ruta de la imagen.

`-m, --mode` 
Mode (0,1 o 2) para el que generaremos nuestro imagen.

`-o, --out` 
Carpeta donde se generaran los archivos resultantes de la ejecucion del comando.

`-d, dsk`
Utilizaremos este parametro si queremos que se genere dentro de una imagen de disco DSK


<a name="sprite"></a>
## sprite

El comando **sprite** generara el fichero C y ASM con el codigo de cada lenguage para poder ser utilizado por ejemplo con 8BP.

```sh
[general]
name           = Mi_Proyecto
nomenclature63 = Yes

[configurations]
concatenate =

[CDT]
files       = MAIN.BIN,MAIN.BAS

```

**parametros**

`-i, --image`
Ruta de la imagen.

`-m, --mode` 
Mode (0,1 o 2) para el que generaremos nuestro sprite.

`-o, --out` 
Carpeta donde se generaran los archivos resultantes de la ejecucion del comando.

`-h, --height`
Ancho de nuestro sprite en pixeles.

`-w, --width`
Altura de nuestro sprite en pixeles.

<a name="run"></a>
## run

El comando **run** Lanzara RetroVirtualMachine web/desktop o enviara los archivos y ejecutara en nuestra M4 Board, segun las configuraciones que tengamos establecidas en el fichero de configuracion **emulators.cfg**.

```sh
[general]
name           = Mi_Proyecto
nomenclature63 = Yes

[configurations]
concatenate =

[CDT]
files       = MAIN.BIN,MAIN.BAS

```

**parametros**

`-f, --file : `
Nombre del fichero de configuracion de nuestros emuladores. Si no se pone cogera por defecto el que se encuentre en la ruta **cfg** con el nombre **emulators.cfg**.

`-s, -setting ` 
Nombre que le hemos dado a la configuración de nuestro emulador en el fichero **emulator.cfg**

<a name="info"></a>
### info

El comando **info** muestra informacion de nuestro proyecto.

```sh
[general]
name           = Mi_Proyecto
nomenclature63 = Yes

[configurations]
concatenate =

[CDT]
files       = MAIN.BIN,MAIN.BAS

```
<a name="about"></a>
### about

El comando **about** muestra informacion de CPCReady.

```sh
[general]
name           = Mi_Proyecto
nomenclature63 = Yes

[configurations]
concatenate =

[CDT]
files       = MAIN.BIN,MAIN.BAS

```
<a name="project"></a>
### project

El comando **project** nos creara la esctructura de carpetas necesarias para trabajar con **CPCReady** en la ruta donde estemos situado:

- Primero nos solicitara si queremos activar la nomenclatura 6:3, es decir que si solo queremos trabajar en el proyecto con nombres que solo pueden tener 6 caracteres de nombre de archivo y 3 de extension. Si añadimos un archivo al projecto que tenga mas de esos caracteres, cuando compilemos para generar nuestros archivos para CPC el proceso fallara. 
- Nos solicitara el nombre del proyecto. Que recomendamos que no tenga espacios.

```sh
cpcready project 

[?] You want to activate the nomenclature 6:3?: Yes
 > Yes
   No

[?] Project name: Mi_Proyecto

👉  Create project...🍺

  CREATE  Mi_Proyecto
  CREATE  Mi_Proyecto/out
  CREATE  Mi_Proyecto/out/disc
  CREATE  Mi_Proyecto/src
  CREATE  Mi_Proyecto/cfg
  CREATE  Mi_Proyecto/lib
  CREATE  Mi_Proyecto/img
  CREATE  Mi_Proyecto/spr
  CREATE  Mi_Proyecto/docs
  CREATE  Mi_Proyecto/cfg/project.cfg (1146 bytes)
  CREATE  Mi_Proyecto/cfg/emulators.cfg (1434 bytes)
  CREATE  Mi_Proyecto/cfg/images.cfg (1045 bytes)
  CREATE  Mi_Proyecto/cfg/sprites.cfg (1114 bytes)
  CREATE  Mi_Proyecto/src/MAIN.BAS (64 bytes)
  CREATE  Mi_Proyecto/src/MAIN.UGB (65 bytes)
  CREATE  Mi_Proyecto/Makefile (1695 bytes)

🚀  Successfully creeated project Mi_Proyecto

👉  Thank you for using CPCReady 

```

Una vez finalizada la creacion del proyecto tendremos disponibles una serie de carpetas que contendran:.

- out:  Archivos DSK, CDT y ficheros para la M4 Board.
- src:  Archivos BAS y UGD (Para Basic compilado)
- cfg:  Archivos de configuracion de nuestro proyecto.
- lib:  Librerias que utilizaremos, como por ejemplo un binario o la libreria (8BP)
- img:  Imagenes en formato PNG o JPG.
- spr:  Imagenes de nuestro sprites.
- docs: Cualquier documentacion de nuestro proyecto.

## Archivos de configuracion

Disponemos de los siguientes archivos de configuracion.

> **NOTA: 
Los ficheros de configuracion son susceptibles a mayusculas y minusculas**
>

### project.cfg

El archivo **project.cfg** dispone de las siguientes opciones configurables.

```sh
[general]
name           = Mi_Proyecto
nomenclature63 = Yes

[configurations]
concatenate =

[CDT]
files       = MAIN.BIN,MAIN.BAS

```

`name=`
Nombre del proyecto. Este nombre no entra en la validacion de nomenclatura 6:3. Se recomienda que no contenga espacios.

`nomenclature63=` 
Si queremos activar en nuestro proyecto la nomenclatura 6:3. Valores admitidos: Yes or No.

`concatenate=` 
La opcion concatenate es valida si queremos trabajar en ficheros BAS independientes (No valido para Basic Compilado con ugbasic), de tal forma que tendremos nuestro codigo estructurado en varios ficheros y la compilacion lo dejara en uno solo para nuestra imagen de disco. de tal forma que si le damos un valor con un nombre de fichero concatenara todos los archivos BAS en él.

`files=`
Los ficheros en el orden en el que se cargaran en la imagen CDT.

### emulators.cfg

El archivo **emulators.cfg** dispone de las siguientes opciones con las que podemos probar nuestros proyecto por maquina o por archivo en Retro Virtual Machine.

> **NOTA: 
A fecha de hoy (18.11.23) RetroVirtualMachine Web solo esta displonible para Amstrad CPC6 6128**
>


```sh
[WEB6128]
type   = web
model  = 6128
run    = run"MAIN.BAS"
image  = out/Mi_Proyecto.DSK
path   = cfg/rvm-web.html

[CPC6128]
type   = desktop
model  = 6128
run    = run"MAIN.BAS"
image  = out/Mi_Proyecto.DSK

[CPC464]
type   = desktop
model  = 464
run    = run""
image  = out/Mi_Proyecto.CDT

[CPCM4]
type    = m4board
ip      = 0.0.0.0
execute = MAIN.BIN
folder  = Mi_Proyecto
```

`type `
El sistema donde vamos a probar, se podra elegir entre desktop, web o m4board.

`model ` 
Modelo de CPC en el que probaremos

`run ` 
Comando que se lanzara en el arranque de la maquina en RetroVirtualMAchine.

`image `
Imagen que se cargara en RetroVirtualMAchine.

`ip `
Direccion IP de la tarjeta M4 Board.

`execute `
Archivo/Programa que ejecutaremos en la M4 Board.

`folder `
Carpeta en M4 Board donde se enviaran los archivos de nuestro proyecto. ESTA CARPETA DEBE EXISTIR PREVIAMENTE.

### images.cfg

El archivo **images.cfg** contiene el modo de pantalla para el que se generara nuestra imagen SCR. Para que la generacion de nuestra Imagen de disco, cinta o archivos para la M4 Board incluya nuestra foto convertida para CPC, tiene que estar dada de alta en este fichero, si no lo esta nunca la generara, aunque existe en la carpeta img.

```sh
[screen.png]
mode = 0 
include_pal = TRUE
```

`[screen.png]`
Nombre de nuestra imagen. 

`mode ` 
Mode para el que vamos a generar nuestra paleta de colores e imagen. (0,1 o 2)

`include_pal ` 
Si queremos que en nuestra imagen de disco, cinta o archivos M4 board se incluya el archvi PAL que se genera al convertir la imagen a SCR. Valores aceptados TRUE o FALSE

### sprite.cfg

El archivo **sprite.cfg** contiene los datos para generar nuestro archivo C y ASM con los datos de nuestro sprite. Para que estos ficheros se generen la imagen tiene que estar dada de alta en este fichero, si no lo esta nunca los generara, aunque existe en la carpeta img.

```sh
[screen.png]
mode = 0
width = 16
height = 16
```

`[screen.png]`
Nombre de nuestra imagen. 

`mode ` 
Mode para el que vamos a generar nuestra paleta de colores e imagen. (0,1 o 2).

`width ` 
Ancho en pixeles de nuestro sprite.

`height ` 
Alto en pixeles de nuestro sprite.