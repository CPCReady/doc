# Como Empezar

Podemos ejecutar **CPCReady** desde el shell con uno de los siguientes comando que estan disponibles: cpc, cpcr o bien cpcready

Disponemos de los siguientes comandos para trabajar.

## Ayuda

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

## project

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

`[general] name:`
Nombre del proyecto. Este nombre no entra en la validacion de nomenclatura 6:3. Se recomienda que no contenga espacios.

`[general] nomenclature63:` 
Si queremos activar en nuestro proyecto la nomenclatura 6:3. Valores admitidos: Yes or No.

`[configurations] concatenate:` 
La opcion concatenate es valida si queremos trabajar en ficheros BAS independientes (No valido para Basic Compilado con ugbasic), de tal forma que tendremos nuestro codigo estructurado en varios ficheros y la compilacion lo dejara en uno solo para nuestra imagen de disco. de tal forma que si le damos un valor con un nombre de fichero concatenara todos los archivos BAS en él.

`[CDT] files:`
Los ficheros en el orden en el que se cargaran en la imagen CDT.