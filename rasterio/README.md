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

### Manejo de conjuntos de datos raster
Información básica
```python
>>> import rasterio

# Apertura de un conjunto de datos
>>> dataset = rasterio.open('chirps-v2.0.2019.10.tif')

# Nombre del conjunto de datos
>>> dataset.name
'chirps-v2.0.2019.10.tif'

# Dimensiones
>>> dataset.width
720
>>> dataset.height
350

# CRS
>>> dataset.crs
CRS.from_epsg(4326)

# Límites
>>> dataset.bounds
BoundingBox(left=-93.0, bottom=5.999999739229679, right=-56.9999994635582, top=23.5)

# Matriz de transformación
>>> dataset.transform
Affine(0.05000000074505806, 0.0, -93.0,
       0.0, -0.05000000074505806, 23.5)
       
# Fila y columna de esquina superior izquierda
>>> dataset.transform * (0, 0)
(-93.0, 23.5)

# Fila y columna de la esquina inferior derecha
>>> dataset.transform * (dataset.width, dataset.height)
(-56.9999994635582, 5.999999739229679)
```

Manejo de las bandas
```python
# Cantidad de bandas
>>> dataset.count
1

# Tipos de datos de las bandas
>>> {i: dtype for i, dtype in zip(dataset.indexes, dataset.dtypes)}
{1: 'float32'}

# Índices de las bandas
>>> dataset.indexes
(1,)

# El método read() retorna un arreglo N-D de Numpy. El argumento es el índice de la banda
>>> band1 = dataset.read(1)

# Datos de la banda 1
>>> band1
array([[-9999.      , -9999.      , -9999.      , ..., -9999.      ,
        -9999.      , -9999.      ],
       [-9999.      , -9999.      , -9999.      , ..., -9999.      ,
        -9999.      , -9999.      ],
       [-9999.      , -9999.      , -9999.      , ..., -9999.      ,
        -9999.      , -9999.      ],
       ...,
       [-9999.      , -9999.      , -9999.      , ..., -9999.      ,
        -9999.      , -9999.      ],
       [-9999.      , -9999.      , -9999.      , ...,    16.187757,
        -9999.      , -9999.      ],
       [-9999.      , -9999.      , -9999.      , ...,    19.232725,
        -9999.      ,    15.843171]], dtype=float32)
        
# Los valores del arreglo se pueden acceder por los índices de la fila y la columna
>>> band1[0,0]
-9999.0
```

Indexación espacial
```python
# El método index() retorna los índices correspondientes a un punto en el espacio georreferenciado
>>> row, col = dataset.index(-84, 10)
>>> row, col
(269, 179)
>>> band1[row, col]
267.6978

# El método xy() retorna las coordenadas espaciales de un pixel
>>> dataset.xy(dataset.height // 2, dataset.width // 2) # centro de la imagen
(-74.97499973140657, 14.72499986924231)
```
