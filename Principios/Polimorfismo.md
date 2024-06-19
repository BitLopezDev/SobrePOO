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
El polimorfismo permite definir **métodos comunes** en una **clase base** y luego **implementarlos de manera específica** en cada una de las **clases derivadas**.


- Imagina que tenemos una clase base llamada `CheckingAccount` (Cuenta de Cheques) con un método `open(initialAmount: number)` para abrir una cuenta.
- Ahora, creamos dos clases derivadas: `BusinessCheckingAccount` (Cuenta de Cheques Empresarial) y `PersonalCheckingAccount` (Cuenta de Cheques Personal).
- Ambas clases heredan de `CheckingAccount` y **sobrescriben** el método `open`, pero con **reglas de negocio diferentes**:

```ts
class CheckingAccount {
    open(initialAmount: number) {
        // Código para abrir la cuenta y guardarlo en la base de datos
    }
}

class BusinessCheckingAccount extends CheckingAccount {
    open(initialAmount: number) {
        if (initialAmount < 1000) {
            throw new Error("Las cuentas empresariales deben tener un depósito inicial de 1.000 euros");
        }
        super.open(initialAmount);
    }
}

class PersonalCheckingAccount extends CheckingAccount {
    open(initialAmount: number) {
        if (initialAmount <= 0) {
            throw new Error("Las cuentas personales deben tener un depósito inicial superior a cero euros");
        }
        super.open(initialAmount);
    }
}

```

