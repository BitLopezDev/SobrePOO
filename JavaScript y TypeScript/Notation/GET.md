En JavaScript, `get` es una palabra clave que se utiliza para definir un método getter en un objeto. Un método getter se comporta como una propiedad, pero su valor se calcula dinámicamente cuando se accede a él.

```JS
get area() {
  return this.calcArea();
}

```

`area` es un método getter. Cuando accedes a la propiedad `area` de un objeto `Rectangle`, en realidad estás llamando al método `calcArea()` y devolviendo su resultado. Aquí está cómo se usaría:

```JS
class Rectangle {
  // El constructor es un método especial para crear e inicializar un objeto creado a partir de una clase.
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }

  // 'get' define un método getter que se comporta como una propiedad.
  get area() {
    return this.calcArea();
  }

  // Este es un método regular de la clase.
  calcArea() {
    return this.height * this.width;
  }

  // El asterisco (*) indica que este es un método generador.
  *getSides() {
    yield this.height;
    yield this.width;
    yield this.height;
    yield this.width;
  }
}
```
`area` es un método getter. Cuando accedes a la propiedad `area` de un objeto `Rectangle`, en realidad estás llamando al método `calcArea()` y devolviendo su resultado. Aquí está cómo se usaría:
```JS
let myRectangle = new Rectangle(5, 10);
console.log(myRectangle.area);  // Imprime 50, no necesitas llamar a myRectangle.area()

```

aunque `area` es un método, no necesitas llamarlo como tal (es decir, no necesitas los paréntesis `()`). Esto puede hacer que tu código sea más legible y fácil de usar, ya que puedes tratar los resultados de los métodos complejos como si fueran simplemente propiedades de un objeto. 