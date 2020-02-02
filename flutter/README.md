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
* Sitio oficial: [Homepage - Material Design](https://material.io/)
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
* Generador de íconos para apps: [App Icon Generator](https://appicon.co/)

## Instalación y configuración en Linux
El procedimiento está detallado en [https://flutter.dev/docs/get-started/install/linux](https://flutter.dev/docs/get-started/install/linux).

### Configuración de acelaración de VM
El procedimiento está detallado en [https://developer.android.com/studio/run/emulator-acceleration?utm_source=android-studio#vm-linux](https://developer.android.com/studio/run/emulator-acceleration?utm_source=android-studio#vm-linux).

Para verificar si KVM está instalado:
```terminal
$ sudo apt-get install cpu-checker
$ egrep -c '(vmx|svm)' /proc/cpuinfo
12
$ kvm-ok
INFO: /dev/kvm exists
KVM acceleration can be used
```

Además, debe ejecutarse:
```terminal
$ sudo apt-get install qemu-kvm
```

Para agregar el usuario al grupo kvm:
```terminal
$ sudo adduser $USER kvm
```
Luego de esto, debe reiniciarse el sistema operativo.

### Instalación del SDK de Flutter
#### Descarga y extracción
```terminal
# La instalación se realizará en $HOME/flutter
$ cd

# Debe sustituirse el nombre del archivo por el correspondiente a la última versión
$ wget https://storage.googleapis.com/flutter_infra/releases/stable/linux/flutter_linux_v1.12.13+hotfix.5-stable.tar.xz
$ tar xf flutter_linux_v1.12.13+hotfix.5-stable.tar.xz
```

#### Modificación del PATH
```terminal
$ nano $HOME/.bashrc

# Debe agregarse la siguiente línea (y hacer la sustitución por el directorio correspondiente):
export PATH="$PATH:$HOME/flutter/bin"

# Verificación
$ echo $PATH
```

#### Pruebas
```terminal
$ flutter
$ flutter doctor
```

### Instalación de Android Studio
El procedimiento está detallado en [https://developer.android.com/studio/install#linux](https://developer.android.com/studio/install#linux).

#### Instalación de paquetes requeridos
```terminal
$ sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1 libbz2-1.0:i386
```

#### Descarga y extracción
El archivo debe descargarse de [https://developer.android.com/studio](https://developer.android.com/studio).

Para extraerlo:
```terminal
$ sudo tar xvzf <archivo-descargado> -C /opt
```

#### Ejecución del instalador
```terminal
$ sudo /opt/android-studio/bin/studio.sh
```

#### Ejecución del programa
```terminal
$ /opt/android-studio/bin/studio.sh
```

#### Instalación de complementos para Flutter
En _Configure - Settings - Plugins_ debe buscarse e instalarse el complemento **Flutter** (automáticamente se instalará también el complemento **Dart**). Luego debe reiniciarse el Android Studio y en el menú principal aparecerá la opción _Start a new Flutter project_.

#### Sugerencias para la creación de un dispositivo virtual
* Usar Nexus 6
* Activar la aceleración de hardware (VM)

#### Posibles problemas
_Licencias no aceptadas_
El problema y su solución se explican en [https://stackoverflow.com/questions/48604914/flutter-run-error-you-have-not-accepted-the-license-agreements](https://stackoverflow.com/questions/48604914/flutter-run-error-you-have-not-accepted-the-license-agreements).

El siguiente comando solucionó el problema:
```terminal
$ flutter doctor --android-licenses
```
#### Sugerencias
En _File - Settings - Languages & Frameworks - Flutter_ activar:
* _Perform hot reload on save_ (está activado por defecto)
* _Format code on save_
