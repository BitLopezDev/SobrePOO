En TypeScript, la palabra clave `abstract` antes de una clase indica que la clase es abstracta, lo que significa que no se puede instanciar directamente. Las clases abstractas están destinadas a ser clases base de otras clases. Permiten definir métodos abstractos, que son métodos declarados pero no implementados en la clase abstracta, obligando a las clases derivadas a proporcionar una implementación específica para esos métodos.

```ts
abstract class Animal {
    abstract hacerSonido(): void;

    mover(): void {
        console.log("El animal se mueve");
    }
}

class Perro extends Animal {
    hacerSonido(): void {
        console.log("Guau");
    }
}

// const animal = new Animal(); // Error: no se puede crear una instancia de una clase abstracta
const miPerro = new Perro(); // Correcto
miPerro.hacerSonido(); // Salida: Guau
miPerro.mover(); // Salida: El animal se mueve

```
En este ejemplo, no puedes crear una instancia de `Animal` porque es una clase abstracta, pero puedes extenderla y crear instancias de las clases derivadas como `Perro`, que implementan los métodos abstractos.