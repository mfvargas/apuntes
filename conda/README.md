# Conda

## Recursos
* Sitio oficial: [Conda](https://conda.io/)
* Manejo de ambientes: [Managing environments -- conda](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)

## Snippets
Manejo de ambientes

```shell
# Lista de ambientes
conda env list

# Creación de un ambiente
conda create -n myenv python
conda create -n myenv scipy=0.15.0

# Activación de un ambiente
conda activate myenv

# Lista de paquetes en un ambiente
conda list -n myenv

# Instalación de paquetes en un ambiente
conda install -n myenv scipy
conda install -n myenv scipy=0.15.0

# Borrado de un ambiente
conda env remove --name myenv
```

## Ambientes conda

### python
Ambiente para tareas generales con Python.

```shell
# Actualización de Conda
conda update conda

# Borrado del ambiente (si es que existe)
# conda remove -n python --all

# Creación del ambiente
conda create -n python

# Activación del ambiente
conda activate python

# Configuración del ambiente
conda config --env --add channels conda-forge
conda config --env --set channel_priority strict

# Instalación de mamba
conda install -c conda-forge mamba

# Instalación de módulos
mamba install git python jupyter jupyterlab numpy pandas matplotlib plotly dash gdal fiona shapely geopandas rasterio folium

# Instalación de pytorch
mamba install pytorch torchvision torchaudio cpuonly -c pytorch

# Desactivación del ambiente
conda deactivate
```

### r
Ambiente para tareas generales con R.

```shell
# Actualización de Conda
conda update conda

# Borrado del ambiente (si es que existe)
# conda remove -n r --all

# Creación del ambiente
conda create -n r

# Activación del ambiente
conda activate r

# Configuración del ambiente
conda config --env --add channels conda-forge
conda config --env --set channel_priority strict

# Instalación de mamba
conda install -c conda-forge mamba

# Instalación de módulos
mamba install git r-base r-essentials r-quarto r-bookdown r-blogdown r-xaringan r-distill r-tidyverse r-ggthemes r-palmerpenguins r-plotly r-dt r-sf r-rmapshaper r-terra r-raster r-rgdal r-leaflet r-leaflet.providers r-leaflet.extras r-leaflet.minicharts r-leafem r-flexdashboard r-shiny r-shinydashboard r-packrat r-rsconnect

# NOTA: parece que RStudio debe instalarse fuera de conda (descargándose del sitio web de la iniciativa). Al ejecutarse rstudio desde la línea de comandos del ambiente conda, se abrirá la versión de RStudio que se instaló.

# Desactivación del ambiente
conda deactivate
```
