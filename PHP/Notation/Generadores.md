Leer [[Métodos generadores]] de JS

PHP también soporta generadores, que son una característica poderosa que permite escribir código que usa la iteración de una manera más eficiente en términos de memoria. Al igual que en JavaScript, puedes usar la palabra clave `yield` en PHP para producir una secuencia de valores.
```PHP
class Rectangle {
  private $height;
  private $width;

  public function __construct($height, $width) {
    $this->height = $height;
    $this->width = $width;
  }

  public function getSides() {
    while (true) {
      yield $this->height;
      yield $this->width;
    }
  }
}

$myRectangle = new Rectangle(5, 10);
$sides = $myRectangle->getSides();

foreach ($sides as $side) {
  echo $side . "\n";
}

```

En este código, el método `getSides()` es un generador que produce el alto y el ancho del rectángulo de manera intercalada. Puedes usar un bucle `foreach` para iterar sobre los valores producidos por el generador.