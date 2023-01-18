# Git
[Git](https://git-scm.com/) es sistema distribuido de control de versiones. Su objetivo es mantener un registro de cambios en archivos de computadora y coordinar el trabajo que varias personas realizan en archivos compartidos. Fue creado para coordinar el trabajo entre programadores, pero puede ser utilizado para rastrear cambios en cualquier tipo de archivos (ej. textos).

Git fue creado en 2005 por [Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds), con el propósito de coordinar el desarrollo del [kernel de Linux](https://en.wikipedia.org/wiki/Linux_kernel).

## Recursos
* Sitio oficial de Git: [Git](https://git-scm.com/)
* Ayuda y flujos de trabajo: [Using Git - GitHub Help](https://help.github.com/en/github/using-git)
* Historia de Git: [The History of Git: The Road to Domination in Software Version Control](https://www.welcometothejungle.com/en/articles/btc-history-git)

## Snippets
### Configuración de git
```shell
git config --global user.name "Manuel Vargas"
git config --global user.email "mfvargas@gmail.com"
```

### Creación de un repositorio
```shell
mkdir repositorio
cd repositorio
git init
git add .
git commit -m "Commit inicial"

# El repositorio estimacion-biodiversidad/estimacion-biodiversidad-qgis-plugin debe ser creado en GitHub (https://github.com/)
git remote add origin https://github.com/estimacion-biodiversidad/estimacion-biodiversidad-qgis-plugin

git push -u origin master
```

### Clonación de un repositorio
```shell
git clone https://github.com/estimacion-biodiversidad/estimacion-biodiversidad-qgis-plugin.git
```

### Aplicar cambios a un repositorio remoto
```shell
git status
git add .
git commit -m "Comentario"
git push -u origin master
```

### Aplicar cambios desde un repositorio remoto
Recursos:
* [Getting changes from a remote repository - GitHub Help](https://help.github.com/en/github/using-git/getting-changes-from-a-remote-repository)

```shell
git pull origin master
```

### Ejecutar un comando de SSH antes del comando Git
```shell
GIT_SSH_COMMAND='ssh -i ~/.ssh/id_rsa' git push
```
