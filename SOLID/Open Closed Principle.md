El **Principio Abierto/Cerrado (OCP)** es uno de los cinco principios SOLID y establece que las entidades de software (clases, módulos, funciones, etc.) deben estar abiertas para la extensión pero cerradas para la modificación. Esto significa que deberías poder agregar nuevas funcionalidades a una entidad de software sin cambiar su código existente

**Abierto para extensión**: Puedes agregar nuevas características o comportamientos a la entidad de software. Por ejemplo, si tienes una clase de ‘Vehículo’, podrías extenderla para crear subclases como ‘Automóvil’ o ‘Motocicleta’ sin modificar la clase ‘Vehículo’ original.

**Cerrado para modificación**: Una vez que la entidad de software está desarrollada y ha sido revisada y probada, su código no debe ser alterado para corregir el comportamiento del software. En lugar de modificar el código existente, utilizas la herencia o la composición para extender el comportamiento.

Aplicar el OCP ayuda a mantener el código más manejable, facilita las pruebas y reduce el riesgo de errores al introducir nuevas funcionalidades. 

Imagina que tienes una clase `Reporte` que puede generar reportes en un formato específico. Según el OCP, si deseas agregar la capacidad de generar reportes en un nuevo formato, no debes modificar la clase `Reporte` existente. En su lugar, puedes extenderla:
```JS
abstract class Reporte {
    abstract generar(contenido: string): void;
}

class ReportePDF extends Reporte {
    generar(contenido: string): void {
        // Extender la funcionalidad para generar un reporte en PDF
    }
}

class ReporteExcel extends Reporte {
    generar(contenido: string): void {
        // Extender la funcionalidad para generar un reporte en Excel
    }
}

```

`Reporte` es una clase abstracta que define un método abstracto `generar`. Las clases `ReportePDF` y `ReporteExcel` extienden la clase `Reporte` y proporcionan implementaciones concretas del método `generar`, permitiendo así la generación de reportes en diferentes formatos sin modificar la clase base. Esto cumple con el Principio Abierto/Cerrado (OCP), ya que las clases derivadas están abiertas para extensión pero la clase base está cerrada para modificación.
