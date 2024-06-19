La **abstracción** es un concepto fundamental en la Programación Orientada a Objetos (POO). Se refiere a la capacidad de representar entidades del mundo real en forma de objetos con características en común.

En la POO, los conceptos del mundo real se modelan como objetos, y la abstracción consiste en definir interfaces y comportamientos comunes para estos objetos. Una abstracción puede definirse como las características específicas de un objeto, aquellas que lo distinguen de los demás tipos de objetos y que logran definir límites conceptuales respecto a quien está haciendo dicha abstracción del objeto

Por ejemplo, si estás creando un programa para manejar una biblioteca, podrías tener una clase abstracta `Libro` que tiene propiedades como `titulo`, `autor`, `editorial`, etc., y métodos como `prestar()`, `devolver()`, etc. Cada instancia de la clase `Libro` sería un objeto que representa un libro específico en la biblioteca.

```TS
abstract class Libro {
    titulo: string;
    autor: string;

    constructor(titulo: string, autor: string) {
        this.titulo = titulo;
        this.autor = autor;
    }

    abstract prestar(): void;
    abstract devolver(): void;
}

class LibroConcreto extends Libro {
    prestar(): void {
        console.log(`El libro ${this.titulo} ha sido prestado.`);
    }

    devolver(): void {
        console.log(`El libro ${this.titulo} ha sido devuelto.`);
    }
}

let libro = new LibroConcreto("1984", "George Orwell");
libro.prestar();
libro.devolver();


```
En este ejemplo, `Libro` es una clase abstracta que define una interfaz para todas las clases de libros. `LibroConcreto` es una clase concreta que implementa esta interfaz. Cada instancia de `LibroConcreto` es un objeto que representa un libro específico en la biblioteca.