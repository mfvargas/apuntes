# ImageMagick

## Recursos
* Sitio oficial: [ImageMagick - Convert, Edit, or Compose Bitmap Images](https://imagemagick.org/)
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

Reducción del tamaño de una imagen
```terminal
$ convert image.jpg -resize 50% output_file.jpg
```
