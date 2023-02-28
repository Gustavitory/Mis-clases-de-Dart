void main() {
  //Clases en DART
  
  //hagamos un simulacro de respuesta api
  final Map<String,String> rawJson={
    'name':'Tony',
//     'Poder':'Intelecto'
  };
  
  final wolverine=new Heroes(nombre:'Wolverine',poder:'Garras');
  final ironMan=new Heroes.fromJson(rawJson);
  print(wolverine);
  print(ironMan);
}

class Heroes{
  //datos que tendra un obj de esta clase
  String nombre;
  String poder;
  
  //Geter y Setter
  
  
  
  @override //el override es solo para que se sepa que estoy reescribiendo algo
  //pero no es obligatorio.
  
  //el metodo toString ya existe, solo lo estamos sobreescribiendo para que 
  //no devuelva instance of Heroes.
  String toString(){
    return 'nombre:$nombre, poder:$poder';
  }
  
  //---------------------- ojo aqui-----------------------------
  
  //Constructor
  //Debe tener el mismo nombre de la Clase
  //Esta es la forma mas facil de hacerlo.
//   Heroes(this.nombre,this.poder);
  
  // A continuacion otra forma:
  //esta forma para mandar los parametros identificados
  Heroes({
    required this.nombre,
    required this.poder
  });
  
  //CONSTRUCTORES CON NOMBRE:
  Heroes.fromJson(Map<String , String> json ):
  // LOS DOS PUNTOS SON PARA EJECUTAR ESTO EN EL MOMENTO EN QUE SE CREA
  //LA INSTANCIA DE LA CLAVE
  //ASI ES QUE LOGRAMOS QUE LAS VARIABLES SIEMPRE TENGAN VALOR DESDE EL INICIO
    this.nombre=json['name'] ?? 'No tiene nombre',
    this.poder=json['Poder'] ?? 'No tiene poder';
}


-----------------------------------CLASES ABSTRACTAS--------------------------------------
Es una clase que no se puede instanciar o inicializadas.
Sirven (Por ahora) solo para ser extendidas por otras clases que no son abstractas.
se declaran:
  abstract class Animal{
    int? pata;
    Animal();
    void emitirSonido();
  }

A partir de esta clase abstracta podemos crear otra clase que va a requerir inicializar o definir las propiedades de la abstracta

por ejemplo:

  class Perro implements Animal{
    int? patas;
    void emitirSonido(){
      print('Guauuuuuu');
    }
  }

Entonces si creamos una funcion que reciba un parametro que sea extendido de tipo animal podemos decir que ejecute su funcion personalizada
ejemplo:

void sonidoAnimal(Animal animal){
  animal.emitirSonido();
}
En el caso del perro saldra en consola Guauuuu pero a medida que declaremos mas saldran muchas mas cosas.
Entonces esto es como las interfaces en typescript?


---------------------------------------------Extends------------------------------------------------------
Extendemos una clase de funcionalidades de otra, tambien se puede usar con clases abstractas.
  abstract class Personaje{
    String? poder;
    String? nombre;
    Personaje(this.nombre);//por que constructor si es abstracta?
    @override
    String toString(){
      return '$nombre - $poder'
    }
  }
  esta clase abstracta solo sera para extender como todas las abstractas

  class Heroe extends Personaje{
    Heroe(String nombre): super(nombre);
  }
  EL SUPER SE REFIERE AL CONTRUCTOR DE DONDE ME ESTOY EXTENDIENDO, EN ESTE CASO SERIA EL SUPER DE PERSONAJE OJO.
  class Villano extends Personaje{
    int maldad=50;
    Villano(String nombre):super(nombre)
  }