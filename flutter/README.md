# Flutter
[Flutter](https://flutter.dev/) es un SDK (_Software Development Kit_) de código abierto utilizado en la actualidad principalmente en aplicaciones móviles y basado en el lenguaje de programación [Dart](https://dart.dev/). Tanto Flutter como Dart fueron creados por Google. Flutter permite el desarrollo de aplicaciones tanto para [Android](https://www.android.com/) como para [iOS](https://www.apple.com/ios/) a partir de una misma base de código fuente.

## Recursos
### Flutter
* Sitio oficial: [Flutter - Beautiful native apps in record time](https://flutter.dev/)
* Documentación oficial: [Flutter Documentation - Flutter](https://flutter.dev/docs)
* Instalación: [Install - Flutter](https://flutter.dev/docs/get-started/install)

#### Entrenamiento
* Recursos del curso en Udemy de London App Brewery: [Flutter-Course-Resources The Complete Flutter Development Bootcam](https://github.com/londonappbrewery/Flutter-Course-Resources)

#### Recetas
* Libro de recetas: [Cookbook - Flutter](https://flutter.dev/docs/cookbook)
* Navegación con rutas nombradas: [Navigate with named routes - Flutter](https://flutter.dev/docs/cookbook/navigation/named-routes)
* Temas: [Use themes to share colors and font styles - Flutter](https://flutter.dev/docs/cookbook/design/themes)

#### Widgets
* Catálogo general: [Widget catalog - Flutter](https://flutter.dev/docs/development/ui/widgets)

#### Widgets de Material
* Sitio oficial de Material: [Homepage - Material Design](https://material.io/)
* Documentación general: [material library - Dart API](https://api.flutter.dev/flutter/material/material-library.html)
* Paletas, íconos y colores: [Material Palette](https://www.materialpalette.com/)
* AppBar: [AppBar class - material library](https://api.flutter.dev/flutter/material/AppBar-class.html)
* FlatButton: [FlatButton class - material library](https://api.flutter.dev/flutter/material/FlatButton-class.html)
* Icons: [Icons class - material library](https://api.flutter.dev/flutter/material/Icons-class.html)
* RaisedButton: [RaisedButton class - material library](https://api.flutter.dev/flutter/material/RaisedButton-class.html)
* Scaffold: [Scaffold class - material library](https://api.flutter.dev/flutter/material/Scaffold-class.html)
* StatefulWidget: [StatefulWidget class - material library](https://api.flutter.dev/flutter/widgets/StatefulWidget-class.html)
* StatelessWidget: [StatelessWidget class - material library](https://api.flutter.dev/flutter/widgets/StatelessWidget-class.html)
* Text: [Text class - material library](https://api.flutter.dev/flutter/widgets/Text-class.html)

#### Paquetes
* Lista de paquetes: [Top packages](https://pub.dev/packages/)
* cloud_firestore (complemento para el acceso al API de Cloud Firestore) [cloud_firestore | Flutter Package](https://pub.dev/packages/cloud_firestore)
* firebase_auth (complemento para el acceso al API de autenticación de Firebase) [firebase_auth | Flutter Package](https://pub.dev/packages/firebase_auth)
* firebase_core (complemento para el acceso al API central de Firebase) [firebase_core | Flutter Package](https://pub.dev/packages/firebase_core)
* flutter_spinkit (animaciones para indicar carga de datos): [flutter_spinkit | Flutter Package](https://pub.dev/packages/flutter_spinkit)
* geolocator (servicios de geolocalización): [geolocator | Flutter Package](https://pub.dev/packages/geolocator)
* http (solicitudes http para API): [http | Flutter Package](https://pub.dev/packages/http)
* provider (manejo del estado): [provider | Flutter Package](https://pub.dev/packages/provider)

### Dart
* Sitio oficial: [Dart programming language | Dart](https://dart.dev/)
* Documentación oficial: [Dart Documentation | Dart](https://dart.dev/guides)
* "Tour" del lenguaje: [Language tour | Dart](https://dart.dev/guides/language/language-tour)
* Palabras clave ("keywords"): [Language tour - Keywords | Dart](https://dart.dev/guides/language/language-tour#keywords)
* Guía de estilo: [Effective Dart: Style | Dart](https://dart.dev/guides/language/effective-dart/style)
* Consola en línea: [DartPad](https://dartpad.dartlang.org/)

### FlutterFire
* FlutterFire: [flutterfire/README.md](https://github.com/FirebaseExtended/flutterfire/blob/master/README.md)

### Otros
* Generador de íconos para apps: [App Icon Generator](https://appicon.co/)
* Uso de los comandos de Flutter en el sistema operativo: [Flutter and the Command Line — a Love Story](https://medium.com/flutter-community/flutter-and-the-command-line-a-love-story-a3648ef2411)
* Uso de Google Maps: [Adding Google Maps to a Flutter App](https://codelabs.developers.google.com/codelabs/google-maps-in-flutter/)
* Diseños para páginas web y aplicaciones móviles: [Dribbble - Discover the World's Top Designers & Creative Professionals](https://dribbble.com/)
* Como cambiar el nombre bajo el ícono de la aplicació: [Flutter - Change App Launcher Icon & Name](https://www.woolha.com/tutorials/flutter-change-app-launcher-icon-name-android-ios)
* Shortcuts para Flutter en Android Studio: [Flutter — IDE Shortcuts for Faster Development](https://medium.com/flutter-community/flutter-ide-shortcuts-for-faster-development-2ef45c51085b)

## Instalación y configuración en Linux
El procedimiento está detallado en [https://flutter.dev/docs/get-started/install/linux](https://flutter.dev/docs/get-started/install/linux).

### Configuración de acelaración de VM
**Ya no estoy tan seguro de que tan necesaria es esta parte**  
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
**Esta parte se modificó para hacerla con Snap**
```terminal
# Instalación mediante Snap
$ sudo snap install flutter --classic
```

#### Pruebas
```terminal
$ flutter
$ flutter --version
$ flutter sdk-path
$ flutter doctor
```

#### Downgrade
**Por si se desea usar una versión más baja**
https://stackoverflow.com/questions/49468321/how-to-downgrade-flutter-sdk-dart-1-x
```terminal
$ flutter downgrade 1.22.6
```

### Instalación de Android Studio
El procedimiento está detallado en [https://developer.android.com/studio/install#linux](https://developer.android.com/studio/install#linux).

**NOTA**: aunque se utilice otro IDE, la instalación de Android Studio siempre es necesaria, para realizar tareas como configuración de emuladores.

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
* Usar Nexus 6 (también vale la pena revisar los Pixel, que traen el símbolo de Play, lo que significa que tienen algunas aplicaciones, como Google Maps, instaladas ya.)
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

#### _Shortcuts_
Estos _shortcuts_ son aportados por los complementos de Flutter para Android Studio y están disponibles también para otros editores e IDE (ej. [Visual Studio Code](https://code.visualstudio.com/)).

**Para declarar un Stateless Widget o un Stateful Widget**:

```st```

**Para ver el código fuente de un Widget**:

```Ctrl-clic``` sobre el widget

**Para ver las opciones disponibles (ej. parámetros)**:

```Ctrl-espacio``` (ej. entre los paréntesis del encabezado de la función)

## Interfaz de línea de comandos
Se recomienda leer [Flutter and the Command Line — a Love Story](https://medium.com/flutter-community/flutter-and-the-command-line-a-love-story-a3648ef2411).

Para obtener ayuda general sobre los comandos de Flutter
```terminal
$ flutter help
```

Para revisar y corregir el estado de la instalación de Flutter
```terminal
$ flutter doctor
```

Para crear y ejecutar un nuevo proyecto
```terminal
$ flutter create proyecto_flutter
$ cd proyecto_flutter
$ flutter run
```

# Snippets
## Aplicación básica (main.dart)
```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter App',
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Flutter App'),
      ),
      body: Center(
        child: Text('Widget Playground!'),
      ),
    );
  }
}
```

## Conversiones entre tipos
### Textos y números
```dart
// Texto a número
print(double.parse("123.5"));

// Número a texto con cantidad fija de decimales
var numero = 123.5444;
print(numero.toStringAsFixed(2));
```

### Formatos de fechas
La lista completa está en:
[DateFormat class - intl library - Dart API](https://pub.dev/documentation/intl/latest/intl/DateFormat-class.html)
```dart
import 'package:intl/intl.dart';

var hoy = DateTime.now();
print(DateFormat.yMMMd().format(hoy));
```
