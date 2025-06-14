# QGIS

## Recursos
* Sitio oficial: [QGIS](https://qgis.org/)

## Instalación en un ambiente Conda
```shell
# Actualización de Conda
conda update conda

# Creación del ambiente
conda create -n qgis-ltr

# Activación del ambiente
conda activate qgis-ltr

# Configuración del ambiente
conda config --env --add channels conda-forge
conda config --env --set channel_priority strict

# Instalación de mamba
conda install mamba -c conda-forge

# Instalación de módulos
mamba install -c conda-forge/label/qgis_ltr qgis

# Ejecución
qgis &
```
