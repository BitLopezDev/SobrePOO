En JavaScript, cuando defines métodos dentro de una clase, **no necesitas** usar la palabra clave `function`. 
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
