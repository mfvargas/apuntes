# _Snippets_ para Unix/Linux
Estos comandos han sido probados en [Ubuntu 18.04 (Bionic Beaver)](http://releases.ubuntu.com/18.04/). Pueden funcionar en otros sistemas operativos de la familia [Debian GNU/Linux](https://www.debian.org/) como, por ejemplo, [Debian 10 (Buster)](https://wiki.debian.org/DebianBuster).

## Información general del sistema
### Información acerca de las versiones del sistema operativo, el kernel y la distribución de Linux
Información sobre el kernel de Linux
```terminal
$ uname -mrs
```
```terminal
Linux 4.15.0-70-generic x86_64
```
Versión de Debian
```terminal
$ cat /etc/debian_version
```
```terminal
buster/sid
```
Información sobre la distribución y sobre LSB (Linux Standard Base)
```terminal
$ lsb_release -a
```
```terminal
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic
```

## SSH, SCP
SSH
```terminal
# Conexión a un host remoto
$ ssh root@159.203.94.51
```

SCP
```terminal
# Copia recursiva de todos los archivos de un directorio a un host remoto
$ scp -r ~/layers/*.* mfvargas@159.203.94.51:~/layers/
```

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

### APT
```terminal
# Actualización
$ sudo apt update
$ sudo apt upgrade -y
$ sudo reboot

# Búsqueda de paquetes
$ sudo apt-cache search gdal-bin

# Versiones disponibles de un paquete
$ sudo apt-cache madison gdal-bin

# Adición de un repositorio
$ sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
$ sudo apt-get update

# Instalación de un paquete
sudo apt-get install -y gdal-bin
```

### Pip
```terminal
# Instalación de Pip para Python 3
$ sudo apt-get install -y python3-pip

# Instalación de un paquete
$ sudo pip3 install psycopg2-binary
```

## Cambio del shell a bash
```terminal
# Para ver el shell actual
$ echo $SHELL

# Para hacer el cambio
$ chsh -s /bin/bash

# Es necesario reconectarse para ver los resultados
$ exit
```
