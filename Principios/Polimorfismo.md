El polimorfismo es un concepto que permite a los objetos tomar muchas formas. En POO, el polimorfismo permite que una interfaz o clase base se use para representar diferentes tipos en tiempo de ejecución.
```ts
interface Vehiculo {
    acelerar(): void;
}

class Automovil implements Vehiculo {
    acelerar(): void {
        console.log("El automóvil está acelerando");
    }
}

class Motocicleta implements Vehiculo {
    acelerar(): void {
        console.log("La motocicleta está acelerando");
    }
}

let vehiculo: Vehiculo = new Automovil();
vehiculo.acelerar();  // Imprime "El automóvil está acelerando"

vehiculo = new Motocicleta();
vehiculo.acelerar();  // Imprime "La motocicleta está acelerando"

```