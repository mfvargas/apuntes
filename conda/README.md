# Conda

## Recursos
Sitio oficial: [Conda](https://conda.io/)
Manejo de ambientes: [Managing environments -- conda](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)

## Snippets
Manejo de ambientes
```terminal
# Lista de ambientes
$ conda env list

# Creación de un ambiente
$ conda create -n myenv python
$ conda create -n myenv scipy=0.15.0

# Activación de un ambiente
$ conda activate myenv

# Lista de paquetes en un ambiente
$ conda list -n myenv

# Instalación de paquetes en un ambiente
conda install -n myenv scipy
conda install -n myenv scipy=0.15.0
```
