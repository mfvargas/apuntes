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
