# Atlas of Living Australia

## Recursos
- [Living Atlases Toolkit](https://github.com/living-atlases/la-toolkit)

## Instalación con el Living Atlases Toolkit

### Creación y configuración de máquinas virtuales en DO

#### Instalador
Creación de la máquina virtual
```shell
# NYC1 - Ubuntu 18.04 (LTS) x64 - 1 CPU 512 MB 10 GB
doctl compute droplet create \
  --region nyc1 \
  --image ubuntu-18-04-x64 \
  --size s-1vcpu-512mb-10gb \
  --ssh-keys 36105160 \
  --tag-names ala,crbio \
  living-atlas-toolkit
```
Debe anotarse el IP de la máquina creada. Puede obtenerse con `doctl compute droplet list --format "ID,Name,PublicIPv4"`.

Conexión con el usuario root
```shell
# Conexión el usuario root
ssh root@000.000.000.000
```

Actualización de paquetes
```shell
# Actualización de paquetes
apt update -y
apt upgrade -y
```

# Creación y configuración del usuario ubuntu
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

# Prueba de conexión
exit
ssh root@000.000.000.000
```

Instalación de Docker
[https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script](https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script)
```shell
# Instalación de Docker
curl -fsSL https://get.docker.com -o get-docker.sh
DRY_RUN=1 sudo sh ./get-docker.sh
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
