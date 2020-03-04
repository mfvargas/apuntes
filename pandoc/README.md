# Pandoc

## Recursos
Sitio oficial: [Pandoc: a universal document converter](https://pandoc.org/)

## Snippets
Instalación
```terminal
$ sudo apt install texlive-latex-base
```

Conversión de MD a Beamer
```terminal
$ pandoc -t beamer input.md -o output.pdf
```

input.md
```
% Título
% Autor
% Fecha
# Diapositiva 1
# Diapositiva 2
```
