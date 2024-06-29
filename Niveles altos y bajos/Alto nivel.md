Las **clases de alto nivel** en la Programación Orientada a Objetos (OOP) son aquellas que se utilizan para definir conceptos o entidades más generales en tu aplicación. Estas clases suelen ser las que controlan el flujo de la aplicación y dependen de las clases de bajo nivel para realizar tareas específicas. No suelen tener mucha funcionalidad por sí mismas y su principal propósito es proporcionar una estructura a la aplicación.

```TS
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
En este ejemplo, `Pedido` es una clase de alto nivel que representa el concepto abstracto de un pedido. Esta clase depende de las clases de bajo nivel `Producto`, `Cliente` y `Pago` para realizar su tarea. La clase `Pedido` no se preocupa por cómo se implementan estas clases de bajo nivel, solo sabe que necesita un producto, un cliente y un pago para realizar un pedido.

```PHP
interface BaseDeDatos {
    public function guardar($dato);
}

class BaseDeDatosMySQL implements BaseDeDatos {
    public function guardar($dato) {
        echo "Guardando $dato en la base de datos MySQL";
    }
}

class Aplicacion {
    private $baseDeDatos;

    public function __construct(BaseDeDatos $baseDeDatos) {
        $this->baseDeDatos = $baseDeDatos;
    }

    public function ejecutar($dato) {
        $this->baseDeDatos->guardar($dato);
    }
}

$baseDeDatos = new BaseDeDatosMySQL();
$aplicacion = new Aplicacion($baseDeDatos);
$aplicacion->ejecutar("dato");


```

En este ejemplo, `BaseDeDatos` es una interfaz que representa la abstracción de una base de datos. `BaseDeDatosMySQL` es una clase de bajo nivel que implementa esta interfaz. `Aplicacion` es una clase de alto nivel que depende de la interfaz `BaseDeDatos`, no de la implementación concreta `BaseDeDatosMySQL`

Ccuando veas una clase en un código, puedes identificarla como una clase de alto nivel si cumple con las siguientes características:

1. La clase representa un concepto o entidad general en tu aplicación.
2. La clase depende de otras clases para realizar tareas específicas.
3. La clase no se preocupa por los detalles de implementación de las clases de las que depende.

**PREGUNTA**: 
Si las clases de alto nivel dependen de las clases de bajo nivel 'para realizar tareas específicas', ¿esto no viola el [[Dependency Inversion Principle]]?

**RESPUESTA**:
El **Principio de Inversión de Dependencias** (también conocido como Dependency Inversion Principle o DIP) establece que los módulos de alto nivel no deberían depender directamente de los módulos de bajo nivel. En cambio, ambos niveles deberían depender de abstracciones. Conforme se indica en la definición.
Las clases de alto nivel no pueden conocer detalles de las clases de bajo nivel.

**Ejemplo** de código con inconsistencia de nivel:

```ts
// Clase de bajo nivel (detalles)
class BajoNivel {
    obtenerDetalles(): string {
        return "Estos son los detalles desde la clase de bajo nivel.";
    }
}

// Clase de alto nivel que depende de la clase de bajo nivel
class AltoNivel {
    private bajoNivel: BajoNivel;

    constructor() {
        this.bajoNivel = new BajoNivel();
    }

    mostrarDetalles(): void {
        const detalles = this.bajoNivel.obtenerDetalles();
        console.log(`Detalles desde la clase de alto nivel: ${detalles}`);
    }
}

// Uso de la clase de alto nivel
const instanciaAltoNivel = new AltoNivel();
instanciaAltoNivel.mostrarDetalles();

```

**Ejemplo** de codigo sin inconsistencia de nivel:

```ts
// Clase de bajo nivel (detalles operativos)

class BajoNivel implements IDetallesOperativos {
    obtenerDetallesOperativos(): string {
        return "Estos son los detalles operativos desde la clase de bajo nivel.";
    }
}

// Interfaz para abstracción de detalles operativos
interface IDetallesOperativos {
    obtenerDetallesOperativos(): string;
}

// Clase de alto nivel que depende de la interfaz IDetallesOperativos
class AltoNivel {
    private detallesOperativos: IDetallesOperativos;

    constructor(detallesOperativos: IDetallesOperativos) {
        this.detallesOperativos = detallesOperativos;
    }

    mostrarDetallesOperativos(): void {
        const detalles = this.detallesOperativos.obtenerDetallesOperativos();
        console.log(`Detalles operativos desde la clase de alto nivel: ${detalles}`);
    }
}

// Uso de las clases
const instanciaBajoNivel = new BajoNivel();
const instanciaAltoNivel = new AltoNivel(instanciaBajoNivel);
instanciaAltoNivel.mostrarDetallesOperativos();


```

1. **Clase de Bajo Nivel (BajoNivel):**
    
    - La clase `BajoNivel` representa los detalles operativos o funcionales de nivel inferior. En este caso, tiene un método llamado `obtenerDetallesOperativos()` que devuelve una cadena con los detalles.
    - Esta clase es la implementación concreta de los detalles operativos.
2. **Interfaz para Abstracción (IDetallesOperativos):**
    - - La interfaz `IDetallesOperativos` define el contrato para cualquier clase que proporcione detalles operativos.
    - Contiene solo el método `obtenerDetallesOperativos()`, que debe ser implementado por cualquier clase que cumpla con la interfaz.
1. **Clase de Alto Nivel (AltoNivel):**
    
    - La clase `AltoNivel` representa la lógica de alto nivel que necesita acceder a los detalles operativos.
    - En su constructor, acepta una instancia de `IDetallesOperativos` (que puede ser una instancia de `BajoNivel` o cualquier otra clase que cumpla con la interfaz).
    - El método `mostrarDetallesOperativos()` utiliza la instancia de `IDetallesOperativos` para obtener los detalles y los muestra en la consola.
4. **Cumplimiento del DIP:**
    
    - El DIP establece que los módulos de alto nivel no deben depender directamente de los módulos de bajo nivel. En cambio, deben depender de abstracciones o interfaces.
    - En nuestro ejemplo, `AltoNivel` depende de la interfaz `IDetallesOperativos`, no de la implementación concreta (`BajoNivel`). Esto cumple con el DIP.
    - Si en el futuro necesitamos cambiar la implementación de los detalles operativos (por ejemplo, usar una clase diferente), no afectará a `AltoNivel` siempre que la nueva clase implemente `IDetallesOperativos`.

En resumen, el código sigue el DIP al depender de abstracciones (la interfaz) en lugar de detalles concretos (la clase `BajoNivel`). Esto facilita la flexibilidad y el mantenimiento del código.