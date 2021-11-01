# Python - creación de un ambiente Conda

```shell
$ conda update conda
$ conda create -n python
$ conda activate python
$ conda config --env --add channels conda-forge
$ conda config --env --set channel_priority strict
$ conda install python fiona shapely geopandas folium notebook jupyter-book ghp-import
```
