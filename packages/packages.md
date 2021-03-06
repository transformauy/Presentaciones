Guía creación de paquetes - R Packages
========================================================
author: 
date: 
autosize: true

Guía
========================================================

Pasos para crear un paquete nuevo:

- Funciones
- Proyecto
- Documentación
- Repositorio

Librerías necesarias
========================================================


```r
# devtools
install.packages("devtools")
library("devtools")

# roxygen2
devtools::install_github("klutometis/roxygen")
library(roxygen2)
```

Funciones
========================================================

Dos formas:
- Crear un script con todas las funciones del paquete.
- Crear un script para cada función del paquete (preferible).

Guardar script/s en ruta provisoria. 



Proyecto: Abrir nuevo proyecto
========================================================

![New Project](NewProject.png)

***

![Project Type](ProjectType.png)


Proyecto (cont.)
========================================================

![Create R Package](CreateRPackage.png)
***
- Editar nombre del paquete.
- Cargar script con funciones generado en paso previo.

Crear paquete.



Proyecto (cont.)
========================================================


Automaticamente se generan los archivos:
- NAMESPACE
- DESCRIPTION

y la carpeta:
- man



Proyecto (cont.)
========================================================

NAMESPACE

Fundamental para paquetes que quieran cargarse en CRAN. Se especifican qué variables 
del paquete deben ser exportadas para disponibilidad del usuario y qué variables 
deben importarse de otros paquetes.

Se deja código por defecto:

```text
exportPattern("^[[:alpha:]]+")
```


DESCRIPTION

Descripción básica del paquete, se edita el archivo que viene por defecto, actualizando Nombre, 
Fecha, Autor, Descripción, Depends (librerías necesarias), Encoding, ...



Documentación
========================================================
![R Documentation](RDocumentation.png)
***
Carpeta: man <br /> 

En esta carpeta se guardan los archivos de documentación .Rd generados manualmente 
para cada función del paquete. 

File >>> New File >>> R Documentation


```text
Nombre de archivo = Nombre función
```

Editar template, de acuerdo a la información de la función: 
Título, Descripción, Valor, Referencias, Autor, etc.



Documentación (cont.)
========================================================


- data-raw: <br />
Incluye archivos originales (.csv, .xlsx, .txt, ...) y scripts para generar archivos
.rda, a través de la función:

```text
devtools::use_data()
```


- data: <br />
Incluye archivos .rda (Rdata) generados en scripts de data-raw.

- R: <br />
En la carpeta R, además de los scripts para cada función ya creados, se genera el 
script data.R, que incluye la documentación de los archivos guardados en data. Se
incorpora el comando #' para que sea detectado por la función de roxygen2.

En la documentación de archivos, se incorpora información sobre la descripción del
df, el formato y descripción de las variables que incluye, etc.


```text
roxygen2::roxygenise('~/paquete', 'R/data.R')
```

Los archivos de documentación (help files), se guardan directamente en la carpeta man.
(Roxygen sobrescribe archivo NAMESPACE, actualizar!)



Repositorio
========================================================
 <br /> <br />
Desde Github:
- Crear nuevo repositorio.
- Crear archivo README.md con información relevante del paquete.

En el proyecto se crea repositorio:

```text
git init
git add 
git commit
```
Crear archivo .gitignore, para configurar los archivos que se desean ignorar.

Se asocia repositorio del proyecto con Github

```text
git remote add origin https://github.com/transformauy/paquete.git
git push -u origin master
```



Bibliografía
========================================================

- Guía rápida: Hilary Parker <br />
http://hilaryparker.com/2014/04/29/writing-an-r-package-from-scratch/

- Guía rápida: In Song Kim, Phil Martin, Nina McMurry & Andy Halterman <br />
http://web.mit.edu/insong/www/pdf/rpackage_instructions.pdf

- Libro completo: Hadley Wickham <br />
http://r-pkgs.had.co.nz/

- Tutorial: Pedro J. Pérez & Francisco G. Morillas <br />
https://perezp44.github.io/pkg4albacete/

- Minimal Tutorial: Karl Broman <br />
http://kbroman.org/pkg_primer/  <br />
http://kbroman.org/github_tutorial/pages/init.html

- Completo (CRAN R) <br />
https://cran.r-project.org/doc/manuals/r-release/R-exts.html

