# Atlas of Living Australia

## Recursos
- [Living Atlases Toolkit](https://github.com/living-atlases/la-toolkit)

## Instalación con el Living Atlases Toolkit

### Creación y configuración de máquinas virtuales en DO

#### Instalador
**Creación de la máquina virtual**
```shell
# NYC1 - Ubuntu 18.04 (LTS) x64 - 1 CPU 512 MB 10 GB
# NYC1 - Ubuntu 18.04 (LTS) x64 - 4 CPU 8 GB 160 GB
doctl compute droplet create \
  --region nyc1 \
  --image ubuntu-18-04-x64 \
  --size s-4vcpu-8gb \
  --ssh-keys 36105160 \
  --tag-names ala,crbio \
  living-atlas-toolkit
```
Debe anotarse el IP de la máquina creada. Puede obtenerse con `doctl compute droplet list --format "ID,Name,PublicIPv4"`.

**Conexión con el usuario root**
```shell
# Conexión el usuario root
ssh root@000.000.000.000
```

**Actualización de paquetes**
```shell
# Actualización de paquetes
apt update -y
apt upgrade -y
```

**Creación y configuración del usuario ubuntu**
```shell
# Creación del usuario
adduser ubuntu --disabled-password

# Adición al grupo sudo
usermod -aG sudo ubuntu

# Eliminación de la clave en el comando sudo
echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/90-cloud-init-users

# Creación del directorio .ssh y del archivo authorized_keys
mkdir -p /home/ubuntu/.ssh
touch /home/ubuntu/.ssh/authorized_keys
chmod 700 /home/ubuntu/.ssh
chmod 644 /home/ubuntu/.ssh/authorized_keys
chown -R ubuntu:ubuntu /home/ubuntu/.ssh
```

**Copia de la llave pública**
```shell
# Salida para regresar a la estación de trabajo
exit

# Copia de la llave pública
cat ~/.ssh/crbio.pub | ssh root@000.000.000.000 "cat >> /home/ubuntu/.ssh/authorized_keys"

# Prueba de la conexión con el usuario ubuntu y la llave pública
ssh ubuntu@000.000.000.000
```

**Instalación y configuración de Docker**\
[https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script](https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script)
```shell
# Instalación
curl -fsSL https://get.docker.com -o get-docker.sh
DRY_RUN=1 sudo sh ./get-docker.sh

# Prueba
sudo docker version

# Adición del usuario ubuntu al grupo docker, para así ejecutar docker sin sudo
sudo usermod -aG docker $USER
# Activación de cambios en el grupo
newgrp docker
# Prueba
docker run hello-world
```

**Creación de directorios**
```shell
# Creación de directorios
sudo mkdir -p /data/la-toolkit/config/ /data/la-toolkit/logs/ /data/la-toolkit/ssh/ /data/la-toolkit/mongo /data/la-toolkit/backups
sudo chmod -R 777 /data
```

**Instalación de xdg-utils**
```shell
sudo apt install -y xdg-utils
```

```shell
git clone https://github.com/living-atlases/la-toolkit.git
```

## Otros

### Comandos del API de DO
```shell
# Lista de tamaños
doctl compute size list

# Lista de llaves SSH
doctl compute ssh-key list

# Lista de imágenes (distribuciones)
doctl compute image list-distribution

# Lista de droplets
doctl compute droplet list --format "ID,Name,PublicIPv4"

# Borrado de un droplet
doctl compute droplet delete 000000000
