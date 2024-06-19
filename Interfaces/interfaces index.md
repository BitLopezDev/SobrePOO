Las **interfaces** en **Programación Orientada a Objetos (POO)** son una herramienta poderosa para definir contratos y estructuras en el código.

- En TypeScript, las interfaces describen la **forma** que deben tener los objetos. Son como **contratos** que especifican qué propiedades y métodos debe tener un objeto.
- Las interfaces permiten definir **requisitos mínimos** para las clases que las implementan.

```ts
interface Animal {
    makeSound(): void;
}

class Cat implements Animal {
    makeSound() {
        console.log("Meow");
    }
}

const myCat = new Cat();
myCat.makeSound(); // Imprime "Meow"

```

- En PHP, las **interfaces de objetos** también definen qué métodos una clase debe implementar, sin especificar cómo se implementarán esos métodos.
```php
interface Animal {
    public function makeSound();
}

class Cat implements Animal {
    public function makeSound() {
        echo "Meow";
    }
}

$myCat = new Cat();
$myCat->makeSound(); // Imprime "Meow"

```