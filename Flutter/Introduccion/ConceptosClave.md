## Conceptos Clave:

Flutter requiere mucha practica como cualquier otro lenguaje.

- Widget:
Un widget es una clase que puede tener argumentos posicionales y argumentos con nombre (Todo en flutter son widget).
Son como bloques de lego, ya cada uno tiene una aplicacion especifica.
Entonces los widget son como componentes reutilizables.

ej: AppBar(title: Text('Hola mundo'))
estanos llamando al wisget AppBar y le pasamos la prop title.

La diferencia con react es que aqui usamos el constructor en vez de usar una pseudo etiqueta HTML.

StatelessWidget=> no le importa si una propiedad cambia.
StateFullWidget=> usa estado, y puede hacer seguimiento del mismo.
es como un componente que usa useState, se puede actualizar cuando un valor cambia.(Puede redibujarse a si mismo)

class ContactoScreen {// stateFull
    String nombre = 'Gustavo'
}

class contactoScreen { // stateLess
    final nombre='Gustavo'
}// declaramos el valor como un final por lo que no puede cambiar su valor

stateless=> button o button con icon por ejemplo.

-------------------------------------

ARBOL DE WIDGETS:

Scaffold= contenedor completo engloba{
    AppBar
    TabBar
    Container{
        Text
        Row
        etc.... muchos mas widget
    }
}
El arbol de widget es como el DOM?


-------------------------------------
ESTRUCTURA DE UN PROYECTO EN FLUTTER:
(Actualmente)

.gitignore => cosas que no queremos en el repo, no tiene nada que ver con flutter si no con github.

.metada // NO TOCAR

.packages // paquetes del proyecto no tocar

pubspec.yami // es usado para muchas cosas, indicas las versionas de sdk, las dependencias, slint (para los warnings), configuras los recursos estaticos (assets) creo que es como el package.json es delicado.
EN EL HACEMOS LAS INSTALACIONES DE DEPENDENCIAS ASI QUE ES MUY IMPORTANTE.

README.md // Documentacion sobre el proyecto

pubspec.lock// es como el packagelock.json--- no se manipula

nombreApp.iml // archivo de intelig

.idea // Es una serie de extensiones preconfiguradas para el IDE, es la configuracion recomendada por el equipo de flutter

.dart_tool // cosas de flutter y editores no nos concierne

android // cuando haga el build aqui se genera el Java de mi app, es mi aplicacion transpilada a java para que pueda ser ejecutada por android, aqui tambien van las configuraciones para android de la app como permisos, etc...

ios // nuestro proyecto flutter pero en swift para que sea ejecutada por ios, tambien se gestionan configuraciones para la plataforma, es importante y git le hace seguimiento.

web // nuestro codigo transpilado para ser ejecutado por navegador, tambien se pueden manejar configuraciones especificas para cuando se ejecuta en ordenador.

test // tests, unit tests, para probar deben tener la misma estructura que los widget de la carpeta lib.

lib // AQUI VIVE NUESTRA APP
es la carpeta src de flutter
al inicio tiene un archivo main que es el punto inicial de la aplicacion.
el 99% del tiempo lo vamos a pasar aca.
Aca viven todos nuestros widgets (componentes).
Hay muchas formas de trabajar un proyecto de flutter.