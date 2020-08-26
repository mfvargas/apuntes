# Hugo

## Recursos
* Sitio oficial de Hugo: [The world’s fastest framework for building websites | Hugo](https://gohugo.io/)
* Instalación en Ubuntu 18.04/Debian 10: [Install and Use Hugo On Ubuntu 18.04/Debian 10](https://computingforgeeks.com/how-to-install-hugo-on-ubuntu-debian/)

## Instalación
### Ubuntu
El procedimiento está descrito en [https://computingforgeeks.com/how-to-install-hugo-on-ubuntu-debian/](https://computingforgeeks.com/how-to-install-hugo-on-ubuntu-debian/)
```shell
$ curl -s https://api.github.com/repos/gohugoio/hugo/releases/latest \
 | grep  browser_download_url \
 | grep Linux-64bit.deb \
 | grep -v extended \
 | cut -d '"' -f 4 \
 | wget -i -
 
$ sudo dpkg -i hugo*_Linux-64bit.deb
```
Para que los cambios hagan efecto, parece que es necesario salir y volver a entrar a la terminal.

## Creación de un sitio y hospedaje en GitHub Pages
Se muestra la creación de un sitio web 
