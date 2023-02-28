FUTURES esto es sumamente util y necesario.
que es? 
es lo que es una promesa en js, es una tarea asincrona.


lo mas comun de un future es una peticion http

se declara fuera de la funcion main;

Future httpGet(String url){
    return Future.delayed(Duration(seconds:3),(){
        return 'Hola Mundo -3 segundos'
    })
}


delayed es como un setTimeOut que tienen las promesas en dart
es una funcion intrinseca, Duration es una clase que supongo es referente a unidades de tiempo y que recibe como parametro al menos en este caso las unidades de tiempo desglosadas.


Se usan igual en en JS

httpGet('http://www.nasa.com/aliens')
.then((data)=>data)

Para definir que es lo que devuelve un future en su declaracion
Future <String> httpGet(){}...

ya que si no posee la propiedad dynamic (el any de dart)


-------------------------------- ASYNC AWAIT --------------------
El async await tiene la misma funcion que en JS, veamos como es su sintaxys e implementacion aca:

String getNombre(String id) async{//Mal
    ...
}
La funcion pasada esta mal ya que la funcion al volverse async ya no esta retornando un string, si no que esta retornando un Future, quedando asi

Future<String> getNombre(String id) async {
    return ...
}


UNA SYNTAXIS INTERESANTE

getNombre('10').then(print);//Funciona Bien