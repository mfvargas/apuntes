# ImageMagick

## Recursos
* Sitio oficial: [ImageMagick - Convert, Edit, or Compose Bitmap Images](https://imagemagick.org/)
* Ejemplos de cambios de tamaño y escala: [Resizing or Scaling -- IM v6 Examples](http://www.imagemagick.org/Usage/resize/)
* Ejemplos de comandos: [A few basic (but powerful) ImageMagick commands](https://medium.com/@contactsunny/a-few-basic-but-powerful-imagemagick-commands-b5809b0a1076)

## Snippets
Instalación con APT
```terminal
$ sudo apt install imagemagick
```

Instalación con Conda
```terminal
$ conda install -c conda-forge imagemagick
```

Reducción de la calidad de una imagen
```terminal
$ convert image.jpg -quality 75 output_file.jpg
```

Reducción del tamaño de una imagen (especificado en porcentaje)
```terminal
$ convert image.jpg -resize 50% output_file.jpg
```

Cambio del tamaño de una imagen (especificado en pixeles), conservando la proporción
```terminal
$ convert icono-app.png -resize 1024x1024 icono-app-1024x1024.png
```

Cambio del tamaño de una imagen (especificado en pixeles), sin conservar la proporción
```terminal
$ convert logo-proyecto-cosecha-agua.png -resize 216x216\! logo-proyecto-cosecha-agua-reducido.png
```
