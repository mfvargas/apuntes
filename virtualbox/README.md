# VirtualBox

## Recursos
- [Oracle VM VirtualBox](https://www.virtualbox.org/)
- [How to Install VirtualBox on Ubuntu 20.04](https://linuxize.com/post/how-to-install-virtualbox-on-ubuntu-20-04/)

## Instalación
Junto con el software base, se recomienda instalar el **Extension Pack**.

### Ubuntu 20.04
Este es el procedimiento para la instalación desde los repositorios de Oracle.

Software base:
```shell
# Instalación de llaves
$ wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
$ wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -

# Adición del repositorio APT
$ echo "deb [arch=amd64] http://download.virtualbox.org/virtualbox/debian $(lsb_release -cs) contrib" | \
      sudo tee -a /etc/apt/sources.list.d/virtualbox.list
      
# Instalación
$ sudo apt update
$ sudo apt install virtualbox-6.1
```

Extension Pack:
```shell
# Descarga
$ wget https://download.virtualbox.org/virtualbox/6.1.8/Oracle_VM_VirtualBox_Extension_Pack-6.1.8.vbox-extpack

# Instalación
$ sudo VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-6.1.8.vbox-extpack
```
