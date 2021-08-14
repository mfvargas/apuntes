# Jupyter Book

## Recursos

* Sitio oficial: [Books with Jupyter](https://jupyterbook.org/)

## Instalación
### Creación de un ambiente Conda
```shell
# Actualización de Conda
$ conda update -n base -c defaults conda

# Creación del ambiente
$ conda create -n ambiente-jupyterbook

# Activación del ambiente
$ conda activate ambiente-jupyterbook

# Instalación de módulos
$ conda config --env --add channels conda-forge
$ conda config --env --set channel_priority strict
$ conda install jupyter-book
$ conda install ghp-import

# Deactivación del ambiente
$ conda deactivate
```

## Uso
```shell
$ conda activate ambiente-jupyterbook

# Creación de un proyecto
$ jupyter-book create nuevo-libro/

# Generación de archivos HTML
$ jupyter-book build nuevo-libro/

# Publicación de archivos HTML

# En el directorio nuevo-libro, debe configurarse un repositorio git
$ cd nuevo-libro
$ git init
$ git add .
$ git commit -m "Commit inicial"
$ git branch -M main
$ git remote add origin https://github.com/curso-python-imn/curso-python-imn.github.io.git
$ git push -u origin main

# Con ghp-import, se crea una rama gh-pages para almacenar el sitio HTML
$ ghp-import -n -p -f _build/html

$ conda deactivate
```

