# Flutter
[Flutter](https://flutter.dev/) es un SDK (_Software Development Kit_) de código abierto utilizado en la actualidad principalmente en aplicaciones móviles y basado en el lenguaje de programación [Dart](https://dart.dev/). Tanto Flutter como Dart fueron creados por Google. Flutter permite el desarrollo de aplicaciones tanto para [Android](https://www.android.com/) como para [iOS](https://www.apple.com/ios/) a partir de una misma base de código fuente.

## Recursos
### Flutter
* Sitio oficial: [Flutter - Beautiful native apps in record time](https://flutter.dev/)
* Documentación oficial: [Flutter Documentation - Flutter](https://flutter.dev/docs)
* Instalación: [Install - Flutter](https://flutter.dev/docs/get-started/install)
* Recursos del curso en Udemy de London App Brewery: [Flutter-Course-Resources The Complete Flutter Development Bootcam](https://github.com/londonappbrewery/Flutter-Course-Resources)

#### Recetas
* Libro de recetas: [Cookbook - Flutter](https://flutter.dev/docs/cookbook)
* Navegación con rutas nombradas: [Navigate with named routes - Flutter](https://flutter.dev/docs/cookbook/navigation/named-routes)

#### Widgets de Material
* Documentación general: [material library - Dart API](https://api.flutter.dev/flutter/material/material-library.html)
* StatelessWidget: [StatelessWidget class - material library](https://api.flutter.dev/flutter/widgets/StatelessWidget-class.html)
* StatefulWidget: [StatefulWidget class - material library](https://api.flutter.dev/flutter/widgets/StatefulWidget-class.html)
* Scaffold: [Scaffold class - material library](https://api.flutter.dev/flutter/material/Scaffold-class.html)
* AppBar: [AppBar class - material library](https://api.flutter.dev/flutter/material/AppBar-class.html)
* Text: [Text class - material library](https://api.flutter.dev/flutter/widgets/Text-class.html)
* FlatButton: [FlatButton class - material library](https://api.flutter.dev/flutter/material/FlatButton-class.html)
* RaisedButton: [RaisedButton class - material library](https://api.flutter.dev/flutter/material/RaisedButton-class.html)

#### Paquetes
* Lista de paquetes: [Top packages](https://pub.dev/packages/)
* geolocator (servicios de geolocalización): [geolocator | Flutter Package](https://pub.dev/packages/geolocator)
* http (solicitudes http para API): [http | Flutter Package](https://pub.dev/packages/http)
* flutter_spinkit (animaciones para indicar carga de datos): [flutter_spinkit | Flutter Package](https://pub.dev/packages/flutter_spinkit)
* firebase_core (complemento para el acceso al API central de Firebase) [firebase_core | Flutter Package](https://pub.dev/packages/firebase_core)
* firebase_auth (complemento para el acceso al API de autenticación de Firebase) [firebase_auth | Flutter Package](https://pub.dev/packages/firebase_auth)
* cloud_firestore (complemento para el acceso al API de Cloud Firestore) [cloud_firestore | Flutter Package](https://pub.dev/packages/cloud_firestore)

### Dart
* Sitio oficial: [Dart programming language | Dart](https://dart.dev/)
* Documentación oficial: [Dart Documentation | Dart](https://dart.dev/guides)
* "Tour" del lenguaje: [Language tour | Dart](https://dart.dev/guides/language/language-tour)
* Guía de estilo: [Effective Dart: Style | Dart](https://dart.dev/guides/language/effective-dart/style)
* Consola en línea: [DartPad](https://dartpad.dartlang.org/)

### FlutterFire
* FlutterFire: [flutterfire/README.md](https://github.com/FirebaseExtended/flutterfire/blob/master/README.md)

### Otros
* Sitio oficial de Material: [Homepage - Material Design](https://material.io/)

## Instalación
### Linux
El procedimiento está detallado en [https://flutter.dev/docs/get-started/install/linux](https://flutter.dev/docs/get-started/install/linux).

#### Instalación del SDK de Flutter ####
##### Descarga y extracción #####
```terminal
# La instalación se realizará en $HOME/flutter
$ cd

# Debe sustituirse el nombre del archivo por el correspondiente a la última versión
$ wget https://storage.googleapis.com/flutter_infra/releases/stable/linux/flutter_linux_v1.12.13+hotfix.5-stable.tar.xz
$ tar xf flutter_linux_v1.12.13+hotfix.5-stable.tar.xz
```

##### Modificación del PATH #####
```terminal
$ nano $HOME/.bashrc

# Debe agregarse la siguiente línea (y hacer la sustitución por el directorio correspondiente):
export PATH="$PATH:$HOME/flutter/bin"

# Verificación
$ echo $PATH
```

##### Pruebas
```terminal
$ flutter
$ flutter doctor
```

### Instalación de Android Studio
