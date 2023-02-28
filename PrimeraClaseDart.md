void main() {
  //Hola mundo comentado
  /*
   * Comentario multilinea
   * aqui todo bien
   * bla bla bla
   * */
  
//   VARIABLES STRINGS Y NUMEROS
//   final String nombre='Gustavo';
//   final apellido='Riera';
//   int edad=26;
//   double numeroRandom=213123123.9231;
//   print('Hola mundo soy $nombre $apellido y tengo $edad años y numero random $numeroRandom');
  
  
//   VARIABLES BOOLEANOS Y CONDICIONES
//   bool isActive=true;
//   bool? isInactive=null;
//   //los condiciones solo aceptan valores de verdadero o falso
//   isInactive!=null?print('Esta activo'):print('Esta inactivo');
  
// LISTAS
//   List<double> numeros=[1,2,3,4,5];
//   numeros.add(88);
//   print(numeros);
//   final generado=List.generate(100,(int index)=>index);
//   print(generado);
  
//MAPAS (ES LO MISMO QUE OBJETOS)
  // los paramtros del map definen los tipos de las llaves y valores
  //  v v v v v v v
  //  llaves,valores
//   Map<String,String> persona={
//     'nombre':'Gustavo',
//     'apellido':'Riera',
//     'soltero':'falso'
//   };
//   final gente=Gente(name:'Gustavo',apellido:'Riera',soltero:false);
//   print(persona['nombre']);
//   print(gente.traerDatos);
  
  
//FUNCIONES EN DART
  void saludar(String name,[String message='Hi']){
    print('$message $name');
  }
  //Si queremos que los parametros no sean obligatorios si no opcionales:
  /*
   void saludar([String name = 'No name']){
      print('Hola $name');
   }
  */
//   saludar('Gustavo','Saludos');
  
  void saludar2({
    required String name,//con la palabra reservada required nos aseguramos
    required String message}){//de que jamas sera null porque sera obligatorio
    print('$message $name');//en los parametros de la funcion.
  }
  saludar2(message: 'Saludos',name: 'Gustavo');
}




// ASI SE DEFINEN CLASES EN DART FUERA DEL MAIN
//   class Gente{
//     final String name;
//     final String apellido;
//     final bool soltero;
//     get traerDatos{
//       return Gente;
//     }
//     Gente({this.name='indefinido',this.apellido='indefinido',this.soltero=true});
//   }