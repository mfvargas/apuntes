# Instalación de software en Ubuntu 22.04

## Docker

```bash
# Actualizar la lista de paquetes
sudo apt update
sudo apt upgrade -y

# Instalar paquetes necesarios para usar repositorios HTTPS
sudo apt install -y ca-certificates curl gnupg lsb-release

# Agregar la clave GPG oficial de Docker
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg \
  | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Agregar el repositorio oficial de Docker
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" \
  | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Instalar Docker Engine, CLI y containerd
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Verificar que Docker funciona
sudo docker run hello-world

# (Opcional, pero recomendado) Ejecutar Docker sin sudo
sudo usermod -aG docker $USER
# Debe cerrarse la sesión y volver a entrar para que el cambio surja efecto
# (fue necesario reiniciar la computadora).
```

## Miniconda

```bash
# 1) Requisitos mínimos
sudo apt update && sudo apt install -y wget bzip2

# 2) Descargar (x86_64)
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh
cd

# (Opcional) Verificar la integridad
sha256sum ~/miniconda.sh

# 3) Instalación silenciosa en el HOME
bash ~/miniconda.sh -b -p $HOME/miniconda3

# 4) Inicializar el shell
$HOME/miniconda3/bin/conda init bash

# 5) Activar cambios en la sesión actual (bash)
source ~/.bashrc

# 6) Prueba
conda --version

# 7) Actualizar conda
conda update -n base -c defaults conda -y

# 8) Instalar mamba
conda install -n base mamba -c conda-forge
```
