La herencia es un mecanismo que permite a una clase obtener (heredar) las propiedades y métodos de otra clase. Con la herencia, se pueden crear nuevas clases a partir de clases existentes, lo que permite la reutilización de código y la representación de relaciones de tipo “es un”.

```TS
class Vehiculo {
    velocidad: number;

    acelerar(): void {
        this.velocidad++;
    }
}

class Automovil extends Vehiculo {
    // Automovil hereda velocidad y acelerar() de Vehiculo
}

```