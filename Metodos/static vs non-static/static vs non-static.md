En la programación orientada a objetos (POO), los métodos estáticos son aquellos que pertenecen a la clase en sí y no a una instancia específica de la clase. Puedes llamar a un método estático directamente desde la clase sin necesidad de crear un objeto. Por otro lado, los métodos no estáticos, también conocidos como métodos de instancia, requieren que crees un objeto de la clase para poder utilizarlos.

**Métodos Estáticos:**

- No pueden acceder a propiedades no estáticas (de instancia) directamente.
- Son útiles para operaciones que no requieren datos de una instancia específica.

**Métodos No Estáticos:**

- Pueden acceder a todas las propiedades y métodos de la clase.
- Son utilizados para operaciones que dependen del estado específico de un objeto.

```ts
class Matematicas {
    static pi: number = 3.1416;
    //`pi` es una constante matemática que no cambia independientemente de la instancia de la clase. Por esta razón, tiene sentido declararla como estática, ya que su valor es universal y no pertenece a una instancia específica de la clase. Podría no ser estática.

    static sumar(a: number, b: number): number {
        return a + b;
    }

    radio: number;

    constructor(radio: number) {
        this.radio = radio;
    }

    calcularArea(): number {
        return Matematicas.pi * this.radio * this.radio;
    }
}

console.log(Matematicas.sumar(5, 3)); // Método estático
const circulo = new Matematicas(5);
console.log(circulo.calcularArea()); // Método no estático que usa la propiedad 'radio' de la instancia


```

```php
class Matematicas {
    public static $pi = 3.1416;
    //`pi` es una constante matemática que no cambia independientemente de la instancia de la clase. Por esta razón, tiene sentido declararla como estática, ya que su valor es universal y no pertenece a una instancia específica de la clase. Podría no ser estática.


    public static function sumar($a, $b) {
        return $a + $b;
    }

    private $radio;

    public function __construct($radio) {
        $this->radio = $radio;
    }

    public function calcularArea() {
        return self::$pi * $this->radio * $this->radio;
    }
}

echo Matematicas::sumar(5, 3); // Método estático
$circulo = new Matematicas(5);
echo $circulo->calcularArea(); // Método no estático que usa la propiedad 'radio' de la instancia


```
En ambos ejemplos, el método estático `sumar` no utiliza ninguna información de una instancia específica y puede ser llamado directamente desde la clase. El método no estático `calcularArea`, sin embargo, utiliza la propiedad `radio` que pertenece a la instancia específica de la clase para realizar su cálculo.