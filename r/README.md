# R

## Creación de un ambiente Conda
```shell
$ conda update conda
$ conda create -n r
$ conda activate r
$ conda config --env --add channels conda-forge
$ conda config --env --set channel_priority strict
$ conda install r-base r-essentials r-ggplot2 r-plotly r-sf r-terra r-raster r-leaflet r-leaflet.providers r-leaflet.extras r-leaflet.minicharts r-leafem r-flexdashboard r-shiny r-shinydashboard r-packrat r-rsconnect
```

Algunos paquetes fueron instalados con `install.packages()` debido a que no se encontró una versión para conda:

```shell
$ install.packages("elevatr")
```

## Recursos
* Instalación en Ubuntu 16.04: [How To Install R on Ubuntu 16.04 | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-r-on-ubuntu-16-04-2)
* Instalación en Ubuntu 18.04: [How To Install R on Ubuntu 18.04 | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-r-on-ubuntu-18-04)
* Instalación de RStudio en Ubuntu 18.04: [RStudio on Ubuntu 18.04 Bionic Beaver Linux](https://linuxconfig.org/rstudio-on-ubuntu-18-04-bionic-beaver-linux)

### Blogs
* Blog de Zev Ross: [Technical Tidbits from Spatial Analysis and Data Science](https://www.zevross.com/blog/)

### Entrenamiento
* Taller de Zev Ross: [Modern Geospatial Data Analysis with R](http://files.zevross.com/workshops/spatial/slides/html/0-deck-list.html)
* Taller sobre _machine learning_: [Introduction to Machine Learning with the Tidyverse](https://education.rstudio.com/blog/2020/02/conf20-intro-ml/)
* Curso sobre R y estadística: [Teacups, Giraffes, & Statistics](https://tinystats.github.io/teacups-giraffes-and-statistics/)
