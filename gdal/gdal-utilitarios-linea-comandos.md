# Utilitarios de línea de comandos de GDAL
Los [utilitarios de línea de comandos de GDAL](https://gdal.org/programs/) permiten ejecutar tareas de geoprocesamiento y de conversión entre formatos geoespaciales sin utilizar una interfaz gráfica o un lenguaje de programación. Están disponibles para varios sistemas operativos, incluyendo Windows, macOS y Unix/Linux.

## Recursos
* Página oficial de los utilitarios de línea de comandos de GDAL: [Programs -- GDAL documentation](https://gdal.org/programs/)
* Ejemplos de comandos: [Cheat sheet for GDAL/OGR command-line tools](https://github.com/dwtkns/gdal-cheat-sheet)
* Ejemplos de comandos: [GDAL/OGR cheat sheet](https://github.com/glw/gdalcheatsheet)
* Ejemplos de comandos: [OGR2OGR Cheatsheet](https://www.bostongis.com/PrinterFriendly.aspx?content_name=ogr_cheatsheet)

## Consideraciones generales
Los utilitarios de GDAL comparten una serie de [opciones comunes](https://gdal.org/programs/raster_common_options.html#raster-common-options) que pueden visualizarse con la opción `-- help-general`. Por ejemplo:
```terminal
$ ogrinfo --help-general
```
```terminal
Generic GDAL utility command options:
  --version: report version of GDAL in use.
  --license: report GDAL license info.
  --formats: report all configured format drivers.
  --format [format]: details of one format.
  --optfile filename: expand an option file into the argument list.
  --config key value: set system configuration option.
  --debug [on/off/value]: set debug level.
  --pause: wait for user input, time to attach debugger
  --locale [locale]: install locale for debugging (i.e. en_US.UTF-8)
  --help-general: report detailed help on general options.
  ```
  
Para obtener ayuda acerca de un comando particular, puede usarse la opción `-- help`. Por ejemplo:
```terminal
$ ogrinfo --help
```

## Snippets
Se recomienda ejecutar estos ejemplos desde la línea de comandos de [Anaconda](https://www.anaconda.com/). También pueden ejecutarse en otras [distribuciones binarias de GDAL](https://gdal.org/download.html#binaries).

Para ejemplificar los comandos, se utilizarán archivos de [Natural Earth](https://www.naturalearthdata.com/). En un sistema Unix/Linux, pueden descargarse y descomprimirse con los comandos:

```terminal
$ wget https://www.naturalearthdata.com/http//www.naturalearthdata.com/download/110m/cultural/ne_110m_admin_0_countries.zip
$ unzip ne_110m_admin_0_countries.zip
```

### Datos vectoriales
Información general (ej. tipo de geometría, cantidad de registros, extensión, SRS, nombres y tipos de los campos) acerca de una fuente de datos.
```terminal
# Información acerca de una capa
$ ogrinfo -so ne_110m_admin_0_countries.shp ne_110m_admin_0_countries

# Información acerca de todas las capas
$ ogrinfo -al -so ne_110m_admin_0_countries.shp
```

Conversiones entre formatos
```terminal
# Descarga de una capa en un servicio WFS a un archivo GeoJSON
$ ogr2ogr -f "GeoJSON" -t_srs EPSG:4326 -simplify 100 provincias.geojson WFS:"http://geos.snitcr.go.cr/be/IGN_5/wfs?" limiteprovincial_5k

# Conversión de CSV a GeoJSON con especificación de columnas (cláusula -select) y filtro (cláusula -where)
ogr2ogr -f GeoJSON output.geojson occurrences.csv -select "kingdom, scientificName, stateProvince" -where "stateProvince='Heredia'" -oo X_POSSIBLE_NAMES=decimalLongitude -oo Y_POSSIBLE_NAMES=decimalLatitude
```

### Datos raster
