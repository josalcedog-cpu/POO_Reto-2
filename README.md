# Programación Orientada a Objetos: Reto 2

En este repositorio están las soluciones al reto de la clase 5 del planteado en [la clase n°5](https://github.com/fegonzalez7/poo_unal_clase5).

Descripción del reto: 

Elija un problema de la vida real (sistema de gestión de biblioteca, negocio de compra-venta, automóvil, etc) que se pueda modelar a través de objetos y clases. Plantee las relaciones de clases, composiciones, propiedades y comportamientos del sistema en uno mas diagramas tipo UML.

## :paw_prints: VetUN: Sistema de gestión de la Clinica para Animales pequeños de la Universidad Nacional.

Elegí modelar el sistema de atención para citas de la clinica para animales pequeños de la universidad en Mermaid: 

```mermaid
---
config:
  layout: elk
title: VetUN
---
classDiagram
    direction TB

    class Animal {
        +int Edad
        +String Code
        +String Nombre
        +String Estado
    }

    class Perro {
        +Camina()
        +Ladra()
    }

    class Gato {
        +Maulla()
        +Ronrronea()
    }

    class Buho {
        +Vuela()
    }

    class Persona {
        +String Nombre
        +String id
    }

    class Owner {
    }

    class DocVet {
        +int Licencia
        +Examina()
        +Prescribe()
    }

    class Consulta {
        +String Fecha
        +String Hora
        +int Costo
    }

    class Historia_Clinica {
        +bool esVacunado
        +bool esCastrado
    }

    class Clinica {
        +String Direccion
        +String Telefono
        +Registrar()
        +Facturar()
    }

    Animal <|-- Gato
    Animal <|-- Perro
    Animal <|-- Buho
    Persona <|-- DocVet
    Persona <|-- Owner
    DocVet "1..*" *-- "1" Clinica
    DocVet "1" --> "0..*" Animal
    Clinica "1" --> "1..*" Animal
    Consulta "1..*" --* "1" Clinica
    Animal "1" -- "1" Consulta
    Historia_Clinica --> Clinica
    Consulta "1" -- "1..*" DocVet
    Owner "1" -- "0..*" Animal : Tiene
```
