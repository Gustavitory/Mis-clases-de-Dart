-------------------------------MIXINS----------------------------
es propio de Dart

ejemplo

abstract class Animal{}

abstract class Mamifero extends Animal{}

abstract class Aves extends Animal{}

abstract class Peces extends Animal{}


abstract class Volador{
    void volar ()=>print('Estoy volando')
}
abstract class Caminante{
    void volar ()=>print('Estoy caminando')
}
abstract class Nadador{
    void volar ()=>print('Estoy nadando')
}

class Delfin extends Mamifero with Nadador{};
class Murcielago extends Mamifero with Volador,Caminante{};


tengo que investigar la diferencia bien entre extend, implement y with.

Un mixin no es mas que tengamos una calse y le implementamos funcionalidades (no se si propiedades) de otra clase.