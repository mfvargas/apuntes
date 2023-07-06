# Atlas of Living Australia

## Recursos
- [Living Atlases Toolkit](https://github.com/living-atlases/la-toolkit)

## Instalación con el Living Atlases Toolkit
Se detalla un procedimiento para instalar un portal de datos de biodiversidad con en el software desarrollado y compartido por el [Atlas of Living Australia (ALA)](https://www.ala.org.au/). La instalación se realiza con el [Living Atlases Toolkit](https://github.com/living-atlases/la-toolkit) en máquinas virtuales de [DigitalOcean (DO)](https://www.digitalocean.com/).

### Creación y configuración de máquinas virtuales en DO
Máquinas virtuales:

- latoolkit.crbio.xyz (Living Atlases Toolkit)
- crbio.xyz, datos01.crbio.xyz (records, records-ws, solr, branding)
- datos02.crbio.xyz (collections, logger)

#### Living Atlases Toolkit
**Creación de la máquina virtual**
```shell
# NYC1 - Ubuntu 18.04 (LTS) x64 - 1 CPU 1 GB RAM 25 GB disco - Llave crbio
doctl compute droplet create \
  --region nyc1 \
  --image ubuntu-18-04-x64 \
  --size s-1vcpu-1gb \
  --ssh-keys 36105160 \
  --tag-names ala,crbio,latoolkit \
  latoolkit.crbio.xyz
```
- Para efectos de esta guía, el IP de la máquina creada se mapea al nombre:  
  `latoolkit.crbio.xyz`
- Si no se usa un nombre, debe anotarse el IP de la máquina creada, el cual puede obtenerse con:  
  `doctl compute droplet list --format "ID,Name,PublicIPv4"`

**Conexión con el usuario root**
```shell
# Conexión con el nombre
ssh -i ~/.ssh/crbio root@latoolkit.crbio.xyz
```

**Actualización de paquetes**
```shell
# Actualización de paquetes
apt update -y && apt upgrade -y
```

**Creación y configuración del usuario ubuntu**
```shell
# Creación del usuario
adduser ubuntu --disabled-password --gecos ""

# Adición al grupo sudo
usermod -aG sudo ubuntu

# Eliminación de la clave en el comando sudo
echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/90-cloud-init-users

# Copia de la llave pública al usuario ubuntu
rsync --archive --chown=ubuntu:ubuntu ~/.ssh /home/ubuntu

# Salida para volver a la estación de trabajo
exit
```

**Conexión con el usuario ubuntu y la llave pública**
```shell
# Conexión con el usuario ubuntu y la llave pública
ssh -i ~/.ssh/crbio ubuntu@latoolkit.crbio.xyz
```

**Instalación y configuración de Docker**\
[https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script](https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script)
```shell
# Instalación
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

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

**Copia de las llaves**
```shell
# Salida para volver a la estación de trabajo (puede que sea necesario repetir el comando)
exit
exit

# Copia de las llaves (desde la estación de trabajo)
scp -o StrictHostKeyChecking=no -i ~/.ssh/crbio ~/.ssh/crbio* ubuntu@latoolkit.crbio.xyz:/data/la-toolkit/ssh
```

**Ejecución de la-toolkit**
```shell
# Conexión con el usuario ubuntu y la llave pública
ssh -o StrictHostKeyChecking=no -i ~/.ssh/crbio ubuntu@latoolkit.crbio.xyz

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
# Salida para regresar a la estación de trabajo
exit

# Creación de un tunel ssh
ssh -o StrictHostKeyChecking=no -i ~/.ssh/crbio -L 2010:127.0.0.1:2010 -L 2011:127.0.0.1:2011 -L 2012:127.0.0.1:2012 ubuntu@latoolkit.crbio.xyz -N -f
```

Si el puerto está en uso:
```shell
# Revisión del puerto 2010
sudo netstat -tulpn | grep 2010

# Debe matarse el proceso que usa el puerto 2010
sudo kill -9 <PROCESO>

# Se intenta nuevamente la creación del tunel
ssh -i ~/.ssh/crbio -L 2010:127.0.0.1:2010 -L 2011:127.0.0.1:2011 -L 2012:127.0.0.1:2012 ubuntu@latoolkit.crbio.xyz -N -f
```

El LA Toolkit debe estar disponible en:\
[http://latoolkit.crbio.zyz:2010/](http://latoolkit.crbio.xyz:2010/)

o si se usó el IP, en:\
[http://localhost:2010/](http://localhost:2010/)

**Otros**  

Ingreso al shell del contenedor la-toolkit  
```shell
# Ingreso al shell del contenedor la-toolkit
docker exec -it la-toolkit bash
```

Directorios de interés  
```shell
# Directorio de archivos de inventarios de ansible 
# ("crbio" debe sustituirse por el nombre del proyecto especificado en la interfaz gráfica de la-toolkit)
/home/ubuntu/ansible/la-inventories/crbio/crbio-inventories

# Directorio de ala-install
/home/ubuntu/ansible/ala-install/ansible
```

Modificaciones a los playbooks de Ansible  
**Nota**: parece que los playbooks se sincronizan con https://github.com/AtlasOfLivingAustralia/ala-install justo antes de ejecutarlos desde la interfaz gráfica de la-toolkit (en "pre deploy", "branding deploy", "deploy" y "post deploy"). Esto debe tenerse en cuenta si van a ejecutarse, por ejemplo, desde la línea de comandos del sistema operativo.
```yaml
# En /home/ubuntu/ansible/ala-install/ansible/roles/cassandra3/tasks/main.yml
# se actualizó el enlace al repositorio de Cassandra para apt
- name: add apt repository (Debian)
  apt_repository:
    repo: "deb https://debian.cassandra.apache.org 311x main"
    state: present
    filename: "cassandra.sources"
    update_cache: yes
  when: ansible_os_family == "Debian"
  tags:
    - packages"
    - cassandra

# En /home/ubuntu/ansible/ala-install/ansible/roles/cassandra3/tasks/main.yml
# se eliminó la opción force=yes, por estar en desuso
- name: install Cassandra (Debian)
  apt: name=cassandra state=latest update_cache=yes
  tags:
    - packages
    - cassandra
  notify:
    - restart cassandra
  when: ansible_os_family == "Debian"
```

Ejecución "manual" de "pre deploy", "branding deploy", "deploy" y "post deploy"  
```shell
# En los comandos que se muestran seguidamente,
# "crbio" debe sustituirse por el nombre del proyecto especificado en la interfaz gráfica de la-toolkit

# pre deploy
cd /home/ubuntu/ansible/la-inventories/crbio/crbio-pre-deploy
ansible-playbook -i ../crbio-inventories/crbio-inventory.ini -i inventory.yml pre-deploy.yml --tags pre-task-etc-hosts,pre-task-solr-limits,pre-task-deps --user ubuntu

# branding deploy
/home/ubuntu/ansible/la-inventories/crbio/crbio-branding/deploy.sh

# deploy
cd /home/ubuntu/ansible/la-inventories/crbio/crbio-inventories
./ansiblew --alainstall=/home/ubuntu/ansible/ala-install --nodryrun --user ubuntu all

# post deploy
cd /home/ubuntu/ansible/la-inventories/crbio/crbio-post-deploy
ansible-playbook -i ../crbio-inventories/crbio-inventory.ini -i inventory.yml post-deploy.yml --tags post-task-postfix --user ubuntu
```

#### Datos 01
```shell
# NYC1 - Ubuntu 18.04 (LTS) x64 - 8 CPU 16 GB 320 GB - Llave crbio
doctl compute droplet create \
  --region nyc1 \
  --image ubuntu-18-04-x64 \
  --size s-8vcpu-16gb \
  --ssh-keys 36105160 \
  --tag-names ala,crbio,latoolkit \
  datos01.crbio.xyz
```
- Para efectos de esta guía, el IP de la máquina creada se mapea a los nombres:  
  `crbio.xyz`, `datos01.crbio.xyz`
- Si no se usa un nombre, debe anotarse el IP de la máquina creada, el cual puede obtenerse con
  `doctl compute droplet list --format "ID,Name,PublicIPv4"`

**Conexión con el usuario root**
```shell
# Conexión con el nombre
ssh -o StrictHostKeyChecking=no -i ~/.ssh/crbio root@datos01.crbio.xyz
```

**Actualización de paquetes**
```shell
# Actualización de paquetes
apt update -y && apt upgrade -y
```

**Creación y configuración del usuario ubuntu**
```shell
# Creación del usuario ubuntu
adduser ubuntu --disabled-password --gecos ""

# Adición al grupo sudo
usermod -aG sudo ubuntu

# Eliminación de la clave en el comando sudo
echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/90-cloud-init-users

# Copia de la llave pública al usuario ubuntu
rsync --archive --chown=ubuntu:ubuntu ~/.ssh /home/ubuntu

# Salida para volver a la estación de trabajo
exit
```

**Conexión con el usuario ubuntu y la llave pública**
```shell
# Conexión con el usuario ubuntu y la llave pública
ssh -i ~/.ssh/crbio ubuntu@datos01.crbio.xyz
```

#### Datos 02
```shell
# NYC1 - Ubuntu 18.04 (LTS) x64 - 8 CPU 16 GB 320 GB - Llave crbio
doctl compute droplet create \
  --region nyc1 \
  --image ubuntu-18-04-x64 \
  --size s-8vcpu-16gb \
  --ssh-keys 36105160 \
  --tag-names ala,crbio,latoolkit \
  datos02.crbio.xyz
```
- Para efectos de esta guía, el IP de la máquina creada se mapea al nombre:  
  `datos02.crbio.xyz`
- Si no se usa un nombre, debe anotarse el IP de la máquina creada, el cual puede obtenerse con:  
  `doctl compute droplet list --format "ID,Name,PublicIPv4"`

**Conexión con el usuario root**
```shell
# Conexión con el nombre
ssh -i ~/.ssh/crbio root@datos02.crbio.xyz
```

**Actualización de paquetes**
```shell
# Actualización de paquetes
apt update -y && apt upgrade -y
```

**Creación y configuración del usuario ubuntu**
```shell
# Creación del usuario ubuntu
adduser ubuntu --disabled-password --gecos ""

# Adición al grupo sudo
usermod -aG sudo ubuntu

# Eliminación de la clave en el comando sudo
echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/90-cloud-init-users

# Copia de la llave pública al usuario ubuntu
rsync --archive --chown=ubuntu:ubuntu ~/.ssh /home/ubuntu

# Salida para volver a la estación de trabajo
exit
```

**Conexión con el usuario ubuntu y la llave pública**
```shell
# Conexión con el usuario ubuntu y la llave pública
ssh -i ~/.ssh/crbio ubuntu@datos02.crbio.xyz
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
doctl compute droplet delete <ID-DROPLET>
