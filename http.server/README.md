# http.server

El módulo [http.server](https://docs.python.org/3/library/http.server.html) de Python implementa un servidor de [Protocolo de transferencia de hipertexto (en inglés: Hypertext Transfer Protocol o HTTP)](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol). Este servidor puede manejarse desde la línea de comandos del sistema operativo y no requiere de configuración, por lo que puede ser apropiado para efectos de pruebas, desarrollo y experimentación.

## Recursos
* Documentación oficial de Python: [http.server -- HTTP servers -- Python 3 documentation](https://docs.python.org/3/library/http.server.html)

## Snippets
Se recomienda ejecutar estos ejemplos desde la línea de comandos de [Anaconda](https://www.anaconda.com/). También pueden ejecutarse en otras [distribuciones binarias de GDAL](https://gdal.org/download.html#binaries).

Inicio del servidor en el puerto 8888
```terminal
$ python -m http.server 8888
```

El comando anterior inicia un servidor local que puede accederse en la dirección [http://localhost:8888/](http://localhost:8888/)
