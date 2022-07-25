# Unix/Linux
Estos comandos han sido probados en [Ubuntu 18.04 (Bionic Beaver)](http://releases.ubuntu.com/18.04/). Pueden funcionar en otros sistemas operativos de la familia [Debian GNU/Linux](https://www.debian.org/) como, por ejemplo, [Debian 10 (Buster)](https://wiki.debian.org/DebianBuster).

## Información general del sistema
### Información acerca de las versiones del sistema operativo, el kernel y la distribución de Linux
Información sobre el kernel de Linux
```shell
uname -mrs
```
```bash
Linux 4.15.0-70-generic x86_64
```
Versión de Debian
```bash
cat /etc/debian_version
```
```bash
buster/sid
```
Información sobre la distribución y sobre LSB (Linux Standard Base)
```bash
lsb_release -a
```
```bash
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic
```

## SSH, SCP
SSH
```bash
# Conexión a un host remoto
ssh root@159.203.94.51
```

SCP
```bash
# Copia recursiva de todos los archivos de un directorio
scp -r ~/layers/*.* mfvargas@159.203.94.51:~/layers/

# Copia de varios grupos de archivos
scp ./mammalia-cr-grp.* ./reptilia-cr-grp.* ./amphibia-cr-grp.* ./aves-cr-grp.* mfvargas@159.203.94.51:~/estimacion-biodiversidad/datos/areas-distribucion/
```

## WGET, FTP
Copia de un directorio completo  
[https://stackoverflow.com/questions/113886/how-to-recursively-download-a-folder-via-ftp-on-linux](https://stackoverflow.com/questions/113886/how-to-recursively-download-a-folder-via-ftp-on-linux)
```shell
wget -r -nH --cut-dirs=5 -nc ftp://<usuario>:<clave>@<servidor>//<ruta/absoluta/completa>
```

## Administración de usuarios
### Creación de usuarios
Esta tarea debe realizarse desde la cuenta de usuario con privilegios para ejecutar sudo o desde la cuenta de root
```bash
# Creación de un usuario
sudo adduser mfvargas

# Adición del usuario al grupo sudo
sudo usermod -aG sudo mfvargas
```

## Administración de paquetes
### APT
```bash
# Actualización
sudo apt update
sudo apt upgrade -y
sudo reboot

# Búsqueda de paquetes
sudo apt-cache search gdal-bin

# Versiones disponibles de un paquete
sudo apt-cache madison gdal-bin

# Adición de un repositorio
sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
sudo apt-get update

# Instalación de un paquete
sudo apt-get install -y gdal-bin

# Instalación de un archivo DEB
sudo dpkg -i /path/to/deb/file
# o
sudo apt-get install -f
# o
sudo apt install /path/to/package/name.deb

# Borrado de un paquete
sudo apt remove vim
sudo apt purge vim
```

### Pip
```bash
# Instalación de Pip para Python 3
sudo apt-get install -y python3-pip

# Instalación de un paquete
sudo pip3 install psycopg2-binary
```

## Manejo de procesos
```bash
# Búsqueda de un proceso en ejecución, por el nombre del proceso
ps -ef | grep postgres
```

## Cambio del shell a bash
```bash
# Para ver el shell actual
echo $SHELL

# Para hacer el cambio
chsh -s /bin/bash

# Es necesario reconectarse para ver los resultados
exit
```
