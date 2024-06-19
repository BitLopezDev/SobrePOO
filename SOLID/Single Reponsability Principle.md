El **Principio de Responsabilidad Única (SRP)** es uno de los cinco principios de la Programación Orientada a Objetos (POO) del SOLID. Este principio establece que una clase debe tener una sola razón para cambiar. En otras palabras, una clase debe tener solo una tarea o responsabilidad.

```TS
// Clase que viola el SRP
class Employee {
    name: string;

    constructor(name: string) {
        this.name = name;
    }

    // Responsabilidad 1: Gestionar la información del empleado
    getName(): string {
        return this.name;
    }

    // Responsabilidad 2: Imprimir el informe del empleado
    printReport(): void {
        console.log(`Imprimiendo informe para el empleado: ${this.name}`);
    }
}

// Clase que sigue el SRP
class EmployeeSRP {
    name: string;

    constructor(name: string) {
        this.name = name;
    }

    // Solo una responsabilidad: Gestionar la información del empleado
    getName(): string {
        return this.name;
    }
}

class EmployeeReport {
    employee: EmployeeSRP;

    constructor(employee: EmployeeSRP) {
        this.employee = employee;
    }

    // Solo una responsabilidad: Imprimir el informe del empleado
    printReport(): void {
        console.log(`Imprimiendo informe para el empleado: ${this.employee.getName()}`);
    }
}

```
En el primer ejemplo, la clase `Employee` tiene dos responsabilidades: gestionar la información del empleado y imprimir el informe del empleado. Esto viola el SRP.

En el segundo ejemplo, separamos las responsabilidades en dos clases: `EmployeeSRP` y `EmployeeReport`. `EmployeeSRP` solo gestiona la información del empleado y `EmployeeReport` solo imprime el informe del empleado. De esta manera, cada clase tiene solo una responsabilidad, cumpliendo así con el SRP.

EJEMPLO:
'Si yo tengo una aplicación médica en POO, ¿no puedo crear una clase 'paciente' que retorne su historial médico cuando se precise, su número de documento de identidad cuando se precise, su cuota mensual, y demás? tendría que hacer una clase independiente para cada una de esas cosas?

RESPUESTA:
El Principio de Responsabilidad Única no significa que cada clase solo pueda tener un método o propiedad. Significa que cada clase debe tener una sola **responsabilidad** o **razón para cambiar**.

En este ejemplo, una clase `Paciente` podría tener métodos para obtener el historial médico, el número de documento de identidad, la cuota mensual, etc. Estos son detalles relacionados con el paciente, por lo que tiene sentido que estén en la misma clase. La “responsabilidad” de la clase `Paciente` es gestionar la información del paciente.
```JS
class Paciente {
    nombre: string;
    documento: string;
    historialMedico: string[];
    cuotaMensual: number;

    constructor(nombre: string, documento: string, historialMedico: string[], cuotaMensual: number) {
        this.nombre = nombre;
        this.documento = documento;
        this.historialMedico = historialMedico;
        this.cuotaMensual = cuotaMensual;
    }

    getNombre(): string {
        return this.nombre;
    }

    getDocumento(): string {
        return this.documento;
    }

    getHistorialMedico(): string[] {
        return this.historialMedico;
    }

    getCuotaMensual(): number {
        return this.cuotaMensual;
    }
}

```
Sin embargo, si empiezas a agregar métodos a la clase `Paciente` que manejan otras responsabilidades (como imprimir informes de pacientes, calcular seguros, etc.), entonces estarías violando el SRP. En ese caso, sería mejor crear clases separadas para manejar esas responsabilidades adicionales. Por ejemplo, podrías tener una clase `ReportePaciente` para manejar la impresión de informes de pacientes, y una clase `CalculadoraSeguro` para calcular los seguros.


```PHP
// Clase que viola el SRP
class Libro {
    private $titulo;
    private $autor;

    public function __construct($titulo, $autor) {
        $this->titulo = $titulo;
        $this->autor = $autor;
    }

    public function getTitulo() {
        return $this->titulo;
    }

    public function getAutor() {
        return $this->autor;
    }

    // Responsabilidad adicional: imprimir detalles del libro
    public function imprimirDetalles() {
        echo "Título: " . $this->titulo . ", Autor: " . $this->autor;
    }
}

// Clase que sigue el SRP
class LibroSRP {
    private $titulo;
    private $autor;

    public function __construct($titulo, $autor) {
        $this->titulo = $titulo;
        $this->autor = $autor;
    }

    public function getTitulo() {
        return $this->titulo;
    }

    public function getAutor() {
        return $this->autor;
    }
}

class ImpresoraLibro {
    private $libro;

    public function __construct($libro) {
        $this->libro = $libro;
    }

    // Solo una responsabilidad: imprimir detalles del libro
    public function imprimirDetalles() {
        echo "Título: " . $this->libro->getTitulo() . ", Autor: " . $this->libro->getAutor();
    }
}

```