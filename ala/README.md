# Atlas of Living Australia

## Recursos
- [Living Atlases Toolkit](https://github.com/living-atlases/la-toolkit)

## Instalación con el Living Atlases Toolkit
Se detalla un procedimiento para instalar un portal de datos de biodiversidad con en el software desarrollado y compartido por el [Atlas of Living Australia (ALA)](https://www.ala.org.au/). La instalación se realiza con el [Living Atlases Toolkit](https://github.com/living-atlases/la-toolkit) en máquinas virtuales de [DigitalOcean (DO)](https://www.digitalocean.com/).

### Creación y configuración de máquinas virtuales en DO
Máquinas virtuales:

- Living Atlases Toolkit
- Servidor 1
- Servidor 2

#### Liviing Atlases Toolkit
**Creación de la máquina virtual**
```shell
# NYC1 - Ubuntu 18.04 (LTS) x64 - 2 CPU 4 GB 80 GB
doctl compute droplet create \
  --region nyc1 \
  --image ubuntu-18-04-x64 \
  --size s-2vcpu-4gb \
  --ssh-keys 36105160 \
  --tag-names ala,crbio \
  living-atlas-toolkit
```
Debe anotarse el IP de la máquina creada. Puede obtenerse con `doctl compute droplet list --format "ID,Name,PublicIPv4"`.

**Conexión con el usuario root**
```shell
# Conexión el usuario root
ssh root@<DIRECCION-IP>
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
cat ~/.ssh/crbio.pub | ssh root@<DIRECCION-IP> "cat >> /home/ubuntu/.ssh/authorized_keys"

# Prueba de la conexión con el usuario ubuntu y la llave pública
ssh ubuntu@<DIRECCION-IP>
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
sudo usermod -aG docker ubuntu
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

**Ejecución de la-toolkit**
```shell
# Clonación del repositorio
cd
git clone https://github.com/living-atlases/la-toolkit.git

# Ejecución
cd la-toolkit
docker compose up -d

# Revisión de los contenedores creados (la-toolkit, la-toolkit-mongo y la-toolkit-watchtower)
docker ps
```

**Acceso desde otra computadora**
```shell
# Creación de un tunel ssh
ssh -L 2010:127.0.0.1:2010 -L 2011:127.0.0.1:2011 -L 2012:127.0.0.1:2012 ubuntu@<DIRECCION-IP> -N -f
```

Si el puerto está en uso:
```shell
sudo netstat -tulpn | grep 2010
kill -9 <PROCESO>
```

El LA Toolkit debe estar disponible en:\
[http://localhost:2010/](http://localhost:2010/)

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
doctl compute droplet delete <ID-DROPLET>
