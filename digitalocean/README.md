# DigitalOcean

## Comandos para listar opciones de configuración

### Lista de tamaños
```shell
doctl compute size list
```

### Lista de droplets
```shell
doctl compute droplet list --format "ID,Name,PublicIPv4"
```

## Creación de máquinas virtuales

### NYC1 - Ubuntu 22.04 (LTS) x64 - 1 CPU 512 MB 10 GB
```shell
doctl compute droplet create \
  --region nyc1 \
  --image ubuntu-22-04-x64 \
  --size s-1vcpu-512mb-10gb \
  --ssh-keys 36947975 \
  --tag-names tag1,tag2 \
  nombre
```

## Tareas posteriores

### Conexión
```shell
ssh mfvargas@999.999.999.999
```

### Actualización de paquetes
```shell
apt update -y
apt upgrade -y
```

### Creación del usuario ubuntu
```shell
# Creación del usuario ubuntu (debe decidirse si se usa o no el password)
adduser ubuntu --disabled-password

# Adición al grupo sudo
usermod -aG sudo ubuntu

# Eliminación de la clave en el comando sudo
echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/90-cloud-init-users

# Creación del directorio .ssh y del archivo authorized_keys del usuario ubuntu
mkdir -p /home/ubuntu/.ssh
touch /home/ubuntu/.ssh/authorized_keys
chmod 700 /home/ubuntu/.ssh
chmod 644 /home/ubuntu/.ssh/authorized_keys
chown -R ubuntu:ubuntu /home/ubuntu/.ssh
```

### Copia de la llave
```shell
# Copia de la llave pública (desde la estación de trabajo)
cat ~/.ssh/ubuntu.pub | ssh root@999.999.999.999 "cat >> /home/ubuntu/.ssh/authorized_keys"

# Prueba de la conexión con el usuario ubuntu y la llave pública
ssh ubuntu@999.999.999.999
```
