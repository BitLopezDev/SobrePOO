La composición es una técnica que nos permite crear objetos complejos combinando otros objetos más pequeños. 

1. **Composición**:
    - Implica que un objeto más complejo está compuesto por otros objetos más pequeños.
    - La clase contenedora **depende** de las clases componentes.
    - Si el contenedor se destruye, los objetos componentes también se destruyen
    - Ejemplo: Imagina una **laptop** que **tiene un teclado**. El teclado es parte integral de la laptop y no puede existir independientemente de ella.
```ts
class KeyBoard {
    // Propiedades y métodos del teclado
    constructor() {
        // Inicialización del teclado
    }
}

class Laptop {
    private manufacturer: string;
    private model: string;
    private serviceTag: string;
    private keyBoard: KeyBoard; // Composición: la laptop tiene un teclado

    constructor(manufacturer: string, model: string, serviceTag: string) {
        this.manufacturer = manufacturer;
        this.model = model;
        this.serviceTag = serviceTag;
        this.keyBoard = new KeyBoard(); // Creación del teclado junto con la laptop
    }

    // Otros métodos y atributos de la laptop
}

// Ejemplo de uso
const miLaptop = new Laptop("Dell", "XPS 13", "ABC123");
// La laptop ahora tiene un teclado asociado

console.log(miLaptop);

```