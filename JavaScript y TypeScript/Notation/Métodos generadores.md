Lo elemental:

```JS
const foo = function* () {
  yield 'a';
  yield 'b';
  yield 'c';
};

let str = '';
for (const val of foo()) {
  str = str + val;
}

console.log(str);
// Expected output: "abc"

```

```JS
function* generator(i) {
  yield i;
  yield i + 10;
}

const gen = generator(10);

console.log(gen.next().value);
// Expected output: 10

console.log(gen.next().value);
// Expected output: 20
```

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
Este método en JavaScript es un **generador**. Los generadores son funciones especiales que pueden pausar su ejecución y luego reanudarla más tarde. Esto se hace mediante la palabra clave `yield`.

Cuando llamas a un generador, no se ejecuta de inmediato. En su lugar, devuelve un objeto especial llamado **iterador**, que controla la ejecución del generador.

Cada vez que llamas al método `next()` en el iterador, el generador se ejecuta hasta que encuentra la siguiente declaración `yield`, luego se pausa y devuelve el valor `yielded`.

```JS
let myRectangle = new Rectangle(5, 10);
let sides = myRectangle.getSides();

console.log(sides.next().value);  // Imprime 5
console.log(sides.next().value);  // Imprime 10
console.log(sides.next().value);  // Imprime 5
console.log(sides.next().value);  // Imprime 10

```

¿Qué tal si el método fuese el siguiente?
```JS
*getSides() { yield this.height; yield this.width;}
```
El método generador `getSides()` funcionaría de manera similar, pero solo produciría dos valores en lugar de cuatro. Aquí está cómo se usaría:
```JS
let myRectangle = new Rectangle(5, 10);
let sides = myRectangle.getSides();

console.log(sides.next().value);  // Imprime 5
console.log(sides.next().value);  // Imprime 10

```

¿Qué pasa si llamo side.next() una tercera vez?

Si llamas a `sides.next()` una tercera vez, obtendrás un objeto con dos propiedades: `value` y `done`. La propiedad `value` será `undefined`, ya que no hay más valores para producir, y la propiedad `done` será `true`, indicando que el generador ha terminado de producir valores
```JS
console.log(sides.next());  // Imprime { value: undefined, done: true }

```
Esto es útil porque te permite saber cuándo el generador ha terminado de producir valores, por lo que puedes dejar de llamar a `next()`.

¿Hay alguna forma de que siempre devuelva el alto o el ancho del rectángulo de manera intercalada pero sin hacer infinitas sentencias yield?

Sí, puedes hacerlo utilizando un bucle infinito en tu método generador. 
```JS
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }

  *getSides() {
    while (true) {
      yield this.height;
      yield this.width;
    }
  }
}

```
En este código, el método generador `getSides()` tiene un bucle `while (true)` que nunca termina. Cada vez que llamas a `next()`, obtienes el siguiente lado del rectángulo. Cuando llega al final del bucle, simplemente vuelve al principio y comienza de nuevo.

```JS
let myRectangle = new Rectangle(5, 10);
let sides = myRectangle.getSides();

console.log(sides.next().value);  // Imprime 5
console.log(sides.next().value);  // Imprime 10
console.log(sides.next().value);  // Imprime 5
console.log(sides.next().value);  // Imprime 10
// Y así sucesivamente...

```