# ImageMagick

## Recursos
* Sitio oficial: [ImageMagick - Convert, Edit, or Compose Bitmap Images](https://imagemagick.org/)
* Ejemplos de cambios de tamaño y escala: [Resizing or Scaling -- IM v6 Examples](http://www.imagemagick.org/Usage/resize/)
* Ejemplos de comandos: [A few basic (but powerful) ImageMagick commands](https://medium.com/@contactsunny/a-few-basic-but-powerful-imagemagick-commands-b5809b0a1076)

## Snippets
Instalación
```terminal
$ sudo apt install imagemagick
```

Reducción de la calidad de una imagen
```terminal
$ convert image.jpg -quality 75 output_file.jpg
```

Reducción del tamaño de una imagen (en porcentaje)
```terminal
$ convert image.jpg -resize 50% output_file.jpg
```
Reducción del tamaño de una imagen (en pixeles)
```terminal
$ convert icono-app.png -resize 1024x1024 icono-app-1024x1024.png
```
