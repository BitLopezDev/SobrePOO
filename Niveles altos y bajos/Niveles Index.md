En POO, las clases de [[Alto nivel]] y de bajo nivel se refieren a la abstracción de esas clases.
**Clases de Alto Nivel:** Las clases de alto nivel son aquellas que se utilizan para crear abstracciones más generales. Estas clases suelen ser las que controlan el flujo de la aplicación y dependen de las clases de bajo nivel para realizar tareas específicas. No suelen tener mucha funcionalidad por sí mismas y su principal propósito es proporcionar una estructura a la aplicación.

Por ejemplo, en una aplicación de comercio electrónico, podrías tener una clase de alto nivel `Pedido` que maneja el proceso de realizar un pedido. Esta clase podría depender de clases de bajo nivel como `Producto`, `Cliente` y `Pago`.
```JS
class Pedido {
    producto: Producto;
    cliente: Cliente;
    pago: Pago;

    constructor(producto: Producto, cliente: Cliente, pago: Pago) {
        this.producto = producto;
        this.cliente = cliente;
        this.pago = pago;
    }

    realizarPedido(): void {
        // Lógica para realizar el pedido
    }
}

```

**Clases de [[Bajo nivel]] Las clases de bajo nivel son las que realizan tareas específicas y proporcionan funcionalidad a las clases de alto nivel. Estas clases suelen estar más cerca de los detalles de implementación y pueden interactuar con el sistema de archivos, la base de datos, la red, etc.

Siguiendo con el ejemplo anterior, las clases `Producto`, `Cliente` y `Pago` serían clases de bajo nivel:

```JS
class Producto {
    nombre: string;
    precio: number;

    constructor(nombre: string, precio: number) {
        this.nombre = nombre;
        this.precio = precio;
    }
}

class Cliente {
    nombre: string;
    direccion: string;

    constructor(nombre: string, direccion: string) {
        this.nombre = nombre;
        this.direccion = direccion;
    }
}

class Pago {
    monto: number;
    metodo: string;

    constructor(monto: number, metodo: string) {
        this.monto = monto;
        this.metodo = metodo;
    }

    procesarPago(): void {
        // Lógica para procesar el pago
    }
}

```