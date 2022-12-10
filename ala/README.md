# Atlas of Living Australia

## Recursos
- [Living Atlases Toolkit](https://github.com/living-atlases/la-toolkit)

## Instalación con el Living Atlases Toolkit

### Creación de máquinas virtuales en DO

#### Instalador
```shell
# NYC1 - Ubuntu 18.04 (LTS) x64 - 1 CPU 512 MB 10 GB
doctl compute droplet create \
  --region nyc1 \
  --image ubuntu-18-04-x64 \
  --size s-1vcpu-512mb-10gb \
  --ssh-keys 36105160 \
  --tag-names tag1,tag2 \
  nombre
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
```
