# Fiona

## Recursos
Sitio oficial  
[Fiona reads and writes geographic data files](https://github.com/Toblerity/Fiona)

## Snippets

### Recorrido de una fuente de datos

```python
import fiona
print("Versión de Fiona:", fiona.__version__)

with fiona.open('datos/provincias_snit_crtm05.geojson', 'r') as provincias:
    
    # Recorrido de los registros
    for registro_provincia in provincias:
        print(registro_provincia['properties']['nom_prov'])

```
