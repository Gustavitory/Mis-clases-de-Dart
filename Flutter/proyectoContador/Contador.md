*****************************
# App contador anotaciones de clases:

- La app la creas directo desde vsc gracias a las extensiones.
 command + shift + p => flutter: create project
 coomand + shift + p => flutter: select device
 f5 => inicia el proyecto en el dispositivo seleccionado

#### Primera parte:
    - main.dart no se debe cambiar de posicion, es el index del proyecto
    - primero debemos crear la funcion main y esa funcion main va a desplegar un widget.
    
    void main(){
        runApp(app)
    }

    runApp esta importado de package:flutter/material.dart.
    app es el widget (sera como el componente app en react que engloba la app);

    class MyApp extends StatelessWidget/StatefullWidget{

    }
    SI NO SE HACE EL EXTENDS A STATELESS O STATEFULL FLUTTER NO LO VA A RECONOCER COMO UN WIDGET SI NO COMO UNA CLASE CORRIENTE Y POR ENDE NO VA A PODER SER USADO COMO PARAMETRO PARA runApp
    Supongamos que es Stateless:

    NOTA: Para ver los errores o informacion que puede ayudar sobre algo (en vsc), hacer command + . con el mouse sobre el error y te dara las recomendaciones e incluso si haces click en alguno te dara el fragmento de codigo base que te falta

    class MyApp extends StatelessWidget{
        // las clases que son widget deben tener el metodo build @override ya que existe y lo estamos reescribiendo, y este metodo build //debe de retornar un widget.
        
        @override
        Widget build(BuildContext context){
            return MaterialApp(
                home: Text('Hola mundo')
            )
        }
    }

    widgets vistos:{
        Text=> p
        Center=> un div centrado, reclibe un key llamado child que recibe widget
    }


---------------------------------------------------

Para optimizar debemos declarar constructores del widget o clase con const.

class MyApp extends StatelessWidget{ //esto es un widget
        @override
        Widget build(BuildContext context){
            return MaterialApp( // MaterialApp es un widget
                home: Center( //Center es un widget
                    child: Text('Hola Mundo') //Text es un widget
                )
            )
        }
    }    
si son widget quiere decir que son clases.
El text no va a variar su valor, siempre sera Hola mundo asi que debemos declararlas como const. seria :

class MyApp extends StatelessWidget{
        @override
        Widget build(BuildContext context){
            return const MaterialApp(
                home: Center(
                    child: Text('Hola Mundo),
                )
            )
        }
    }
    El material app no varia y contiene a todos los demas asi que lo declaramos como constante. se declara contante hasta el maximo nivel en donde no varia. Tambien se usan final y var(var no se debe usar)

    La class MyApp debe de tener un constructor y debe de recibir un key y mandarlo a las key de StaelessWidget o StatefullWidget de la siguiente manera:

        para la clase MyApp:
        const MyApp({key?:key}):super(key:key);
    NOTA: recuerda que los : significan que le va a mandar esas props a la clase StatelessWidget andes de que el widget sea renderizado.

    Esto nos deja un warning en el runApp(MyApp());
    ya que hasta ahora MyApp mantiene los valores estaticos declaramos la clase como const.
    recuerda que en flutter las clases ya no se declaran con new pero MyApp en escencia es una clase.

    runApp(const MyApp(//Aqui podria ir la key que configuramos en el constructor pero como es opcional no hace falta, sin embargo es buena idea hacerlo));


    EXPERIENCIA:
     Con la version actual de flutter el constructor de la key se declara como :
      const MyApp({super.key});


podemos quitar el debug imagen que sale en la esquina, en el Widget buil y en return const MaterialApp

debugShowCheckedModeBanner => es un boolean y esta en true por lo tanto lo ponemos en false
------------------------------------------------------

MODULARIZANDO:

  - como con react es importante modularizar todo, de esta manera trabajamos mas organizado y limpio.

  como nombrar el widget home_screen.dart

  class HomeScreen extends StatelessWidget{

    const HomeScreen({super.key});

    @override
        Widget build(BuildContext context){
            return const Center(
                child: Text('Hola desde homeScreen)
            )
        }
  }


En la raiz del proyecto o donde lo vayamos a importar:

si lo usamos el lo importara solo pero entendamos la ruta:

import 'package:counter_app/screens/home_screen.dart'
counter: nombre del proyecto en este ejemplo
luego viene la ruta partiendo desde (Parece ser desde donde esta el archivo)

las importaciones de flutter primero, luego las de paquetes y por ultimo de nuestros widget.

ALGO CURIOSO: es que no necesitas exportar la clase, por defecto puedes acceder a ellas, a menos que coloques el guin bajo al inicio del nombre de la clase ya que esto las hace privadas.


------------------------------------------------------

BuildContext y Scaffold

Son widgets que son sumamente utiles.

ATAJO: cursor encima de lo que retorna el build, comand + . => Tiene opciones interesantes como Wrap with widget, esto va a agarrar nuestro widget y lo va a envolver en otro widget, es solo para optimizar tiempo.

Nota: CASI TODOS LOS WIDGETS RECIBEN CHILD O CHILDREN PERO EL SCAFFOLD RECIBE ES LA PROPIEDAD BODY

Scaffold: Prepara mi app  para empezar a trabajar, tiene ya el formato por defecto del dispositivo, fondo blanco, lo del body es el contenido y esta centrado en la app, recibe otras pros como backgroundColor ( si colocamos backgroundColor: Colors se van a desplegar varios colores predeterminados.) 
EL SCAFFOLD ES COMO UN LAYOUT


BuildContext => es todo el arbol de widgets.
como podemos verlo?? 
en la barra de navegacion que aparece cuando iniciamos un proyecto (aparece pausa, reload, hotreload) hay una lupa con una flecha azul.
Es como la representacion del DOM? 
Sirve para saber el contecto en el cual nuestro widget esta siendo construido.
podemos leer informacion de el, y tambien sirve para routing... obviamente lo usaremos y veremos mejor con la practica.

Vemos todo el arbol de widgets menos el componente qye estamos haciendo. mantiene referencias de toda la app


SCAFFOLD

Widget PreferredSizeWidget esto es una prop para un appbar.
la prop se llama appBar y recibe un widget de ese tipo.

AppBar widget constructor no constante

ERRORES CON LOS QUE ME ENCONTRE:
    no mediaquery ancestor found-> cuando use el Scaffold me salia y se soluciono envolviendo el Widget en un Material app en el main
    de esto: 
    void main() {
  runApp( const  MyApp());
}
    a esto:
    void main() {
  runApp( const MaterialApp(home:  MyApp()));
}

----------------------------------------------------

AppBar props:{
    elevation: esto recibe un entero y hace una sombra dependiendo del numero de elevacion.
}

si queremos colocar mas de un child debemos usar un widget que nos permita eso, Column, Row, etc... en la docu estan los Widgets basicos.

en el caso de Column => este recibe varias props, entre ellas la prop children que recibe un array de wodgets y los devolvera todos uno debajo de otro, esto es especialmente util, otra prop interesante es el mainAxisAligment que alinea el contenido segun el espacio que lo contiene.
EL COLUMN TIENE EL WIDTH DEFINIDO COMO SI HIJO MAS HANCHO, SI LO ENVOLVEMOS EN UN CENTER, TOMARA TODO EL WIDTH DE SU PADRE, ESTO ES INTERESANTE.

-------------------------------------------------------
ESTILOS DE TEXTO:

El campo Text no solo recibe el string que imprimira, tambien las propiedades de estilos que recibe, el primer argumento es posicional, el resto debe de tener su key y value.
Text('Texto que quiero imprimir',style://debemos crear una clase TextStyle)
Text('Texto',style: TextStyle(fontSize:30))// El constructor de Textstyle tiene muchas props y las puedes ver colocando el mouse encima.

Ahora, para que no repitamos codigo en Textos que lucen exactamente igual podemos crear una constante en el widget

const fontSize=Textstyle(fontSize:30);

y luego usarlo en los widgets.
Si alguno de los valores de esto puede cambiar la declaracion cambia ya que esta es si los valores no cambiaran.

-------------------------------------------------------

BOTON FLOTANTE Y FLOATINGACTIONBUTTON

El scaffold tiene una prop que se llema floatingActionButton, recibe Widgets cualquiera,
podemos usar FloatingActionButton que es un widget de flutter.

OBLIGATORIAMENTE debemos configarar la prop onPressed, la cual recibe una funcion como valor,

Los iconos de google ya vienen incluidos en flutter, igual se pueden usar iconos de otras fuentes.

recibe un hijo que en este caso queremos que sea un icono:
    child: const Icon(Icons.plus)
    Icon recibe varias props pero la mas importante es IconData y se soloca sin keys.
NOTA: PARA VER LOS ICONOS A MEDIDA QUE VOY BAJANDO PUEDO PRESIONAR CTRL + SPACE

-------------------------------------------------------

Crear el estado en un stateless widget:

En este caso declaramos int clicks=0;

en el Text
Text('$clicks',style:fontSize30)

y quitamos el const de childrens en column porque tenemos una variable dentro del text.

para que funcione ocupamos un gestor de estado (objeta que maneja el estado);

NO SE PUEDE Con lo que sabemos hasta ahora.

usaremos el StateFull por ahora:
    el statefull en primera instancia tiene la clase corriente pero el Override ya no cambia el metodo build si no que se forma algo como esto:
        State <nombredelWidget> createState()=>_NombreDelWidget();

Y luego debajo se define la clase _NombreDelWidget si usara el metodo build debajo del override.
los estados los colocaremos como base, fuera del build,
el build lo usaremos como siempre, para construir el widget, cuando queramos modificar el estado podemos hacerlo como se modifica una variable normal pero debemos hacerlo y luego invocar a la funcion setState con una funcion anonima o podemos hacerlo dentro de la misma
ej 
counter++;
setState((){});
 o
setState((){
    counter++;
})
 NOTA: POR LO GENERAL EVITAREMOS USAR STATEFULL WIDGETS.

 Podemos usar el widget SizedBox para crear espacios entre elementos en un Row (esto es algo raro);
