# eBird - API
[eBird](https://ebird.org/) es una base de datos en Internet sobre observaciones de aves. [Es el proyecto de ciencia ciudadana relacionado con biodiversidad más grande del mundo](https://ebird.org/about), con más de 100 millones de registros de aves contribuidos cada año por los _eBirders_. Una iniciativa colaborativa que cuenta con cientos de organizaciones socias, así como miles de expertos regionales, y cientos de miles de usuarios. eBird es administrado por el [Laboratorio de Ornitología de Cornell](https://www.birds.cornell.edu/).

El proyecto fue iniciado en 2002 por el Laboratorio de Ornitología de Cornell y la [National Audubon Society](https://www.audubon.org/).

eBird registra información información básica acerca de la distribución y la abundancia de aves en varias escalas espaciales y temporales. Una interfaz web (disponible también en dispositivos móviles) le permite a los participantes ingresar sus observaciones y consultar los resultados por medio de [visualizaciones estadísticas y geoespaciales](https://ebird.org/explore).

La [interfaz de programación de aplicaciones (API) de eBird](https://documenter.getpostman.com/view/664302/S1ENwy59?version=latest) permite realizar programáticamente consultas por criterios como ubicación, fecha, taxonomía y otros.

## Observaciones generales sobre el uso del API
* Para utilizar el API, primero debe [solicitarse una llave (_key_)](https://ebird.org/api/keygen), la cual estará ligada a la cuenta de usuario de eBird. Esta llave debe ser incluida en un encabezado llamado ```x-ebirdapitoken```. También puede utilizarse como un parámetro de solicitud (_request parameter_) llamado ```key```.
* El formato por defecto de las respuestas es [JavaScript Object Notation (JSON)](https://json.org/).

## Recursos
* Sitio oficial de eBird: [eBird - Discover a new world of birding...](https://ebird.org/)
* Documentación del API de eBird: [eBird API 2.0](https://documenter.getpostman.com/view/664302/S1ENwy59?version=latest)
* Interfaz en Python para el API de eBird: [eBird API - PyPI](https://pypi.org/project/ebird-api/)
* Interfaz en R para el API de eBird: [ropensci/rebird: Wrapper to the eBird API](https://github.com/ropensci/rebird)
* Mapa de _hotspots_ de eBird: [Explore Hotspots - eBird](https://ebird.org/hotspots)
* Ejemplo de uso del API de eBird desde Python y R: [Wednesday Birders - Using the ebird API, Python, and R to analyze data for our birding group - hselab.org](http://hselab.org/wednesday-birders-using-the-ebird-api-python-and-r-to-analyze-data-for-our-birding-group.html)

## Ejemplos

### Python
