# GDAL/OGR

[Geospatial Data Abstraction Library (GDAL/OGR)](https://gdal.org/) es una biblioteca para leer y escribir datos geoespaciales en varios [formatos raster](https://gdal.org/drivers/raster/) y [vectoriales](https://gdal.org/drivers/vector/). La sigla GDAL se utiliza para referirse a la funcionalidad para datos raster y OGR para la correspondiente a los datos vectoriales. En ocasiones, GDAL puede usarse para ambos casos. De aquí en adelante, se utilizá esta última acepción.

GDAL cuenta con un único [modelo abstracto de datos raster](https://gdal.org/user/raster_data_model.html) y un único [modelo abstracto de datos vectoriales](https://gdal.org/user/vector_data_model.html), lo que permite programar aplicaciones geoespaciales sin tener que ocuparse de las particularidades de cada formato que utilicen (GeoTIFF, NetCDF, ESRI Shapefile, GeoJSON, etc.).

A pesar de que GDAL está programada en C/C++, cuenta con una interfaz de programación de aplicaciones (API) para varios lenguajes de programación, incluyendo [C](https://gdal.org/api/index.html#c-api), [C++](https://gdal.org/api/index.html#id3), [Python](https://gdal.org/python/index.html) y [Java](https://gdal.org/java/overview-summary.html). Además, ofrece un conjunto de [utilitarios de línea de comandos](https://gdal.org/programs/) cuyas [distribuciones binarias](https://gdal.org/download.html#binaries) están disponibles para varios sistemas operativos, incluyendo Windows, macOS y Linux.

La biblioteca GDAL es distribuida por [Open Source Geospatial Foundation (https://www.osgeo.org/)](https://www.osgeo.org/) con una [licencia X/MIT](https://gdal.org/license.html#license).
