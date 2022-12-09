# DigitalOcean



## Máquinas virtuales

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
