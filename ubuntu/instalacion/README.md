# Instalación de software en Dell Alienware m18 R2

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
```
