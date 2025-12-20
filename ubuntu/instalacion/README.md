# Instalación de software en Ubuntu 24.04

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

### Limpiar espacio

```bash
# Observar cuanto espacio en disco está usando Docker
docker system df -v

# Limpiar TODO lo no usado (contenedores, imágenes, redes y volúmenes)
# -a = imágenes no usadas por ningún contenedor
# --volumes = volúmenes no referenciados por contenedores
docker system prune -a --volumes -f

# Limpiar caché de compilación (BuildKit/Buildx)
# (los builds dejan capas/cachés que no desaparecen con el paso anterior)
# Para Docker con BuildKit (actual por defecto)
docker builder prune -a -f

# Verificar el ahorro
docker system df -v
du -sh /var/lib/docker/* 2>/dev/null
```

## Miniconda

```bash
# Requisitos mínimos
sudo apt update && sudo apt install -y wget bzip2

# Descargar (x86_64)
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh
cd

# (Opcional) Verificar la integridad
sha256sum ~/miniconda.sh

# Instalación silenciosa en el HOME
bash ~/miniconda.sh -b -p $HOME/miniconda3

# Inicializar el shell
$HOME/miniconda3/bin/conda init bash

# Activar cambios en la sesión actual (bash)
source ~/.bashrc

# Prueba
conda --version

# Actualizar conda
conda update -n base -c defaults conda -y

# Instalar mamba
conda install -n base mamba -c conda-forge
```

## VS Code

```bash
# Actualizar la lista de paquetes
sudo apt update

# Instalar utilidades
sudo apt install -y wget gpg apt-transport-https

# Descargar la clave pública de Microsoft
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo gpg --dearmor -o /usr/share/keyrings/ms_vscode.gpg

# Declarar el repositorio oficial de VS Code para APT
echo "deb [arch=amd64,arm64 signed-by=/usr/share/keyrings/ms_vscode.gpg] https://packages.microsoft.com/repos/code stable main" | \
  sudo tee /etc/apt/sources.list.d/vscode.list

# Volver a actualizar el índice de paquetes para incluir el nuevo repo de VS Code
sudo apt update

# Instalar VS Code
sudo apt install -y code
```

Para actualizar:

```bash
# Revisar la versión actual
code --version

# Actualizar
sudo apt update
sudo apt install --only-upgrade code

# Revisar la versión recién instalada
code --version
```

### Extensiones

#### Markdown

- Markdown All in One
- markdownlint

#### Docker

- Docker

## LibreOffice

```bash
# Actualizar la lista de paquetes
sudo apt update

# Instalar LibreOffice
sudo apt install -y libreoffice libreoffice-help-es libreoffice-l10n-es hunspell-es hyphen-es mythes-es

# Verificación
libreoffice --version
```

## QGIS

```bash
# Instalar la llave con el keyring
sudo mkdir -m755 -p /etc/apt/keyrings
sudo wget -O /etc/apt/keyrings/qgis-archive-keyring.gpg https://download.qgis.org/downloads/qgis-archive-keyring.gpg
sudo chmod 644 /etc/apt/keyrings/qgis-archive-keyring.gpg

# Apuntar el archivo con el keyring a la LTR
sudo tee /etc/apt/sources.list.d/qgis.sources >/dev/null <<'EOF'
Types: deb deb-src
URIs: https://qgis.org/ubuntu-ltr
Suites: noble
Architectures: amd64
Components: main
Signed-By: /etc/apt/keyrings/qgis-archive-keyring.gpg
EOF

# Actualizar la lista de paquetes
sudo apt update

# Instalar QGIS
sudo apt install -y qgis qgis-plugin-grass
```

## Zoom

```bash
# Actualizar la lista de paquetes
sudo apt update

# Descargar el paquete
wget https://zoom.us/client/latest/zoom_amd64.deb

# Instalar
sudo apt install ./zoom_amd64.deb
```

## VLC Media Player

```bash
sudo apt update
sudo apt install vlc
```

## Node.js

```bash
# Actualizar la lista de paquetes
sudo apt update

# Instalar dependencias útiles para compilar módulos nativos
sudo apt install -y curl build-essential python3

# Instalar NVM (Node Version Manager)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
# Cargar nvm en el shell actual
source ~/.bashrc

# Instalar la última LTS (22.x al 2025-08-23) y fijarla por defecto
nvm install --lts
nvm alias default lts/*

# Verificar
node -v && npm -v
```

## Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```
