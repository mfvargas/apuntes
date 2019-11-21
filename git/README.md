# Git
[Git](https://git-scm.com/) es sistema distribuido de control de versiones. Su objetivo es mantener un registro de cambios en archivos de computadora y coordinar el trabajo que varias personas realizan en archivos compartidos. Fue creado para coordinar el trabajo entre programadores, pero puede ser utilizado para rastrear cambios en cualquier tipo de archivos (ej. textos).

Git fue creado en 2005 por [Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds), con el propósito de coordinar el desarrollo del [kernel de Linux](https://en.wikipedia.org/wiki/Linux_kernel).

## Recursos
Sitio oficial: [Git](https://git-scm.com/)

## Snippets
### Configuración de git
```terminal
$ git config --global user.name "Manuel Vargas"
$ git config --global user.email "mfvargas@gmail.com"
```

### Creación de un repositorio
```terminal
$ mkdir repositorio
$ cd repositorio
$ git init
$ git add .
$ git commit -m "Commit inicial"

# El repositorio estimacion-biodiversidad/estimacion-biodiversidad-qgis-plugin debe ser creado en GitHub (https://github.com/)
$ git remote add origin git@github.com:estimacion-biodiversidad/estimacion-biodiversidad-qgis-plugin

$ git push -u origin master
```

### Clonación de un repositorio
```terminal
$ git clone https://github.com/estimacion-biodiversidad/estimacion-biodiversidad-qgis-plugin.git
```

### Actualización de un repositorio
```terminal
$ git status
$ git add .
$ git commit -m "Comentario"
$ git push -u origin master
```
