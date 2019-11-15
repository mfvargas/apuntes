# _Snippets_ para Unix/Linux
Estos comandos han sido probados en [Ubuntu 18.04 (Bionic Beaver)](http://releases.ubuntu.com/18.04/).

## Administración de usuarios

### Creación de usuarios
Esta tarea debe realizarse desde la cuenta de usuario con privilegios para ejecutar sudo o desde la cuenta de root
```terminal
# Creación de un usuario
sudo adduser mfvargas

# Adición del usuario al grupo sudo
$ sudo usermod -aG sudo mfvargas
```

## Administración de paquetes

### Actualización
```terminal
$ sudo apt update
$ sudo apt upgrade -y
$ sudo reboot
```

## Otros

### Cambio del shell a bash
```terminal
# Para ver el shell actual
$ echo $SHELL

# Para hacer el cambio
$ chsh -s /bin/bash

# Es necesario reconectarse para ver los resultados
$ exit
```
