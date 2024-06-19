El encapsulamiento es el proceso de ocultar los datos internos y los métodos de una clase para proteger su estado. En POO, esto se logra utilizando modificadores de acceso (`private`, `protected`, etc.) para restringir el acceso a los miembros de la clase (variables, métodos, etc.).
```TS
class Automovil {
    private velocidad: number;

    acelerar(): void {
        this.velocidad++;
    }

    getVelocidad(): number {
        return this.velocidad;
    }
}

```