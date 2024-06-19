El **Principio de Inversión de Dependencias (DIP)** es uno de los cinco principios de SOLID en la Programación Orientada a Objetos (POO). Este principio establece que:

1. Los módulos de [[Alto nivel]] no deben depender de los módulos de [[Bajo nivel]]. Ambos deben depender de abstracciones.
2. Las abstracciones no deben depender de los detalles. Los detalles deben depender de las abstracciones.

En otras palabras, en lugar de que tus clases y módulos dependan de implementaciones concretas, deberían depender de interfaces o clases abstractas. Esto hace que tu código sea más flexible y menos acoplado.

```JS
// Interfaz de alto nivel
interface IBaseDeDatos {
    guardar(dato: string): void;
}

// Clase de bajo nivel
class BaseDeDatosMySQL implements IBaseDeDatos {
    guardar(dato: string): void {
        console.log(`Guardando ${dato} en la base de datos MySQL`);
    }
}

// Clase de alto nivel
class Aplicacion {
    private baseDeDatos: IBaseDeDatos;

    constructor(baseDeDatos: IBaseDeDatos) {
        this.baseDeDatos = baseDeDatos;
    }

    ejecutar(dato: string): void {
        this.baseDeDatos.guardar(dato);
    }
}

let baseDeDatos = new BaseDeDatosMySQL();
let aplicacion = new Aplicacion(baseDeDatos);
aplicacion.ejecutar("dato");

```
En este ejemplo, `Aplicacion` es una clase de alto nivel y `BaseDeDatosMySQL` es una clase de bajo nivel. En lugar de que `Aplicacion` dependa directamente de `BaseDeDatosMySQL`, ambas clases dependen de la interfaz `IBaseDeDatos`. Esto significa que puedes cambiar la base de datos que usa la aplicación simplemente pasando una instancia diferente de `IBaseDeDatos` al constructor de `Aplicacion`.

```PHP
// Interfaz de alto nivel
interface BaseDeDatos {
    public function guardar($dato);
}

// Clase de bajo nivel
class BaseDeDatosMySQL implements BaseDeDatos {
    public function guardar($dato) {
        echo "Guardando $dato en la base de datos MySQL";
    }
}

// Clase de alto nivel
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
Este ejemplo en PHP es similar al ejemplo de TypeScript. `Aplicacion` es una clase de alto nivel y `BaseDeDatosMySQL` es una clase de bajo nivel. Ambas clases dependen de la interfaz `BaseDeDatos`, lo que hace que el código sea más flexible y menos acoplado.