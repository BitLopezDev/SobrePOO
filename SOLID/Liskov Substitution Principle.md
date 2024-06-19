El **Principio de Sustitución de Liskov (LSP)** es otro de los cinco principios de SOLID en la Programación Orientada a Objetos (POO). Este principio establece que si una clase `B` es una subclase de la clase `A`, entonces deberíamos poder reemplazar `A` con `B` sin interrumpir el comportamiento del programa.
Este principio es fundamental para garantizar que un cliente que usa un objeto de la clase base pueda funcionar correctamente cuando se le pase un objeto de una subclase.
```JS
// Clase base
class Pajaro {
    volar(): void {
        console.log("El pájaro está volando");
    }
}

// Clase derivada que sigue el LSP
class Aguila extends Pajaro {
    volar(): void {
        console.log("El águila está volando alto");
    }
}

// Clase derivada que no sigue el LSP
class Pinguino extends Pajaro {
    volar(): void {
        throw new Error("Los pingüinos no pueden volar");
    }
}

```

En este ejemplo, `Pinguino` es una subclase de `Pajaro`, pero no puede volar. Cuando intentamos hacer volar al pingüino, obtenemos un error. Esto viola el LSP porque no podemos usar `Pinguino` en lugar de `Pajaro` sin cambiar el comportamiento del programa.
```php

class Vehiculo {
    public function acelerar() {
        echo "El vehículo está acelerando";
    }
}

class Coche extends Vehiculo {
    public function acelerar() {
        echo "El coche está acelerando";
    }
}

class Bicicleta extends Vehiculo {
    public function acelerar() {
        throw new Exception("Las bicicletas no aceleran de la misma manera que los vehículos motorizados");
    }
}

function hacerAcelerar($vehiculo) {
    $vehiculo->acelerar();
}

$miCoche = new Coche();
hacerAcelerar($miCoche);  // Funciona correctamente

$miBicicleta = new Bicicleta();
hacerAcelerar($miBicicleta);  // Lanza un error

```
En este ejemplo, `Bicicleta` es una subclase de `Vehiculo`, pero no acelera de la misma manera que otros vehículos. Cuando intentamos hacer acelerar a la bicicleta, obtenemos un error. Esto viola el LSP porque no podemos usar `Bicicleta` en lugar de `Vehiculo` sin cambiar el comportamiento del programa.

Sea B extends A. Se analiza:
**1. Clase B tiene más métodos que la clase A:**
```TS
class A {
    metodoA(): void {
        console.log("Método A");
    }
}

class B extends A {
    metodoB(): void {
        console.log("Método B");
    }
}

let b = new B();
b.metodoA();  // Imprime "Método A"
b.metodoB();  // Imprime "Método B"

```

En este caso, la clase `B` tiene un método adicional `metodoB()`. Esto no viola el Principio de Sustitución de Liskov (LSP) siempre que `B` pueda hacer todo lo que `A` puede hacer.

**2. Clase B tiene menos métodos que la clase A:**
Aquí, aunque `B` no define `metodoA2()`, todavía hereda este método de `A`. Por lo tanto, `B` todavía tiene todos los métodos de `A`.
```JS
class A {
    metodoA1(): void {
        console.log("Método A1");
    }
    metodoA2(): void {
        console.log("Método A2");
    }
}

class B extends A {
    // No se define metodoA2
}

let b = new B();
b.metodoA1();  // Imprime "Método A1"
b.metodoA2();  // Imprime "Método A2"

```

**3. Clase B tiene métodos diferentes a la clase A:**

```TS
class A {
    metodoA(): void {
        console.log("Método A");
    }
}

class B extends A {
    metodoB(): void {
        console.log("Método B");
    }
    metodoA(): void {
        console.log("Método modificado de A en B");
    }
}

let b = new B();
b.metodoA();  // Imprime "Método modificado de A en B"
b.metodoB();  // Imprime "Método B"

```
En este caso, `B` redefine `metodoA()`. Esto es aceptable según el LSP siempre que `metodoA()` en `B` sea compatible con `metodoA()` en `A`. Es decir, debe aceptar los mismos argumentos y devolver un tipo de valor compatible. Además, no debe tener efectos secundarios inesperados que contradigan la documentación o las expectativas establecidas por `A`.