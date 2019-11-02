# Snippets

## Linux/Unix

### Administración de usuarios

#### Creación de usuarios
Esta tarea debe realizarse desde la cuena de usuario con privilegios para ejecutar sudo o desde la cuenta de root
```
$ sudo useradd mfvargas -c 'Manuel Vargas' -m
$ sudo passwd mfvargas

# Para agregar al grupo sudo
$ sudo adduser mfvargas sudo
```
