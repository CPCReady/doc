## Como Empezar

Podemos ejecutar **CPCReady** desde el shell con uno de los siguientes comando que estan disponibles: cpc, cpcr o bien cpcready

## Comandos disponibles

### Ayuda

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

### project

El comando **project** nos creara la esctructura de carpetas necesarias para trabajar con **CPCReady** en la ruta donde estemos situado:

```sh
cpcready project                                        2 ✘  sdk   13:06:40  

┌─────────────────────────────────────────────────────────────────────────────────────────────────────────────┐
│ ╔═╗╔═╗╔═╗ ┌─────────────┐                                                                                   │
│ ║  ╠═╝║   │ ███ ███ ███ │                                                                                   │
│ ╚═╝╩  ╚═╝ └─────────────┘                                                                                   │
│ Ready                                                                                                       │
│ █                                                                                                   v0.0.10 │
└─────────────────────────────────────────────────────────────────────────────────────────────────────────────┘


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
