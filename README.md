# Snippets

## Linux/Unix

### Administración de usuarios

#### Creación de usuarios
Esta tarea debe realizarse desde la cuena de usuario con privilegios para ejecutar sudo o desde la cuenta de root
```console
$ sudo useradd mfvargas -c 'Manuel Vargas' -m
$ sudo passwd mfvargas

# Para agregar al grupo sudo
$ sudo adduser mfvargas sudo
```

### Administración de paquetes

#### Actualización
```terminal
$ sudo apt update
$ sudo apt upgrade -y
$ sudo reboot
```

### Otros

#### Cambio del shell a bash
```terminal
# Para ver el shell actual
$ echo $SHELL

# Para hacer el cambio
$ chsh -s /bin/bash

# Es necesario reconectarse para ver los resultados
$ exit
```
