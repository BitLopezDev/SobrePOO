El **Principio de Segregación de Interfaces (ISP)** es uno de los cinco principios SOLID de la programación orientada a objetos. Este principio establece que una clase no debería ser forzada a implementar interfaces que no utiliza. En otras palabras, es mejor tener muchas interfaces específicas en lugar de una única interfaz general.

```ts
interface Printable {
    print(): void;
}

interface Scannable {
    scan(): void;
}

class AllInOnePrinter implements Printable, Scannable {
    print(): void {
        // Implementación de la impresión
    }

    scan(): void {
        // Implementación del escaneo
    }
}

class SimplePrinter implements Printable {
    print(): void {
        // Implementación de la impresión
    }
}

```
En este ejemplo, `AllInOnePrinter` implementa dos interfaces porque puede imprimir y escanear, mientras que `SimplePrinter` solo implementa `Printable` porque solo necesita imprimir.
```php
interface Printable {
    public function print();
}

interface Scannable {
    public function scan();
}

class AllInOnePrinter implements Printable, Scannable {
    public function print() {
        // Implementación de la impresión
    }

    public function scan() {
        // Implementación del escaneo
    }
}

class SimplePrinter implements Printable {
    public function print() {
        // Implementación de la impresión
    }
}

```
En PHP, el concepto es el mismo. `AllInOnePrinter` implementa ambas interfaces, mientras que `SimplePrinter` solo implementa `Printable`. Esto sigue el ISP al asegurar que las clases no tengan que implementar métodos que no van a utilizar.