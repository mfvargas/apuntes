# Rasterio
[Rasterio](https://github.com/mapbox/rasterio) es una biblioteca de Python para leer y escribir datos raster.

## Recursos
* Página oficial: [Rasterio](https://github.com/mapbox/rasterio)
* Documentación: [Rasterio: access to geospatial raster data -- rasterio documentation](https://rasterio.readthedocs.io/)
* Guía de inicio rápido: [Python Quickstart -- rasterio documentation](https://rasterio.readthedocs.io/en/stable/quickstart.html)
* Referencia del API: [Python API Reference -- rasterio documentation](https://rasterio.readthedocs.io/en/stable/api/)

## Instalación
Hay instrucciones para varios ambientes en [Installation -- rasterio documentation](https://rasterio.readthedocs.io/en/stable/installation.html).

### Anaconda
Las instrucciones están en [https://github.com/conda-forge/rasterio-feedstock](https://github.com/conda-forge/rasterio-feedstock).
```terminal
# Adición del canal conda-forge
$ conda config --add channels conda-forge

# Instalación
$ conda install rasterio

# Listado de versiones disponibles en el canal
$ conda search rasterio --channel conda-forge
```

## Snippets
Se recomienda ejecutar estos ejemplos en la distribución de Python de [Anaconda](https://www.anaconda.com/), aunque también puede funcionar en otras distribuciones.

Para ejemplificar los comandos, se utilizarán archivos de [Climate Hazards Group InfraRed Precipitation with Station data (CHIRPS)](https://www.chc.ucsb.edu/data/chirps). En un sistema Unix/Linux, pueden descargarse y descomprimirse con los comandos:

```terminal
$ wget ftp://ftp.chg.ucsb.edu/pub/org/chg/products/CHIRPS-2.0/camer-carib_monthly/tifs/chirps-v2.0.2019.10.tif.gz
$ gunzip chirps-v2.0.2019.10.tif.gz
```

### Básicos
```python
import rasterio

# Apertura de un conjunto de datos
dataset = rasterio.open('chirps-v2.0.2019.10.tif')

# Nombre del conjunto de datos
dataset.name

# Cantidad de bandas
dataset.count
```
