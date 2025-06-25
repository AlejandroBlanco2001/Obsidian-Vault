---
tags:
  - patrones-de-diseno
  - diseno-uml
  - arquitectura-de-software
  - master
  - Lectura
---
Recordemos que esto son formas probadas de resolver problemas conocidos en el mundo del software, especialmente para la:

- Creación
	Se concentra en patrones para facilitar la creación de objetos
- Comportamiento
	Se concentran en patrones para asignar responsabilidades entre objetos
- Estructuración
	Se concentra en patrones para ensamblar la creación de objetos complejos

## Patron Singleton 
Continuar lectura y posibles ejemplos prácticos en la nota [[Singleton Pattern]]

Tipo: Creacional

La intención de este patron es asegurar la creación de una instancia única de una clase, y ofrecer un acceso global para el mismo.

La motivación detrás de este es asegurar que solo se cree una instancia de una clase, porque es importante que no exista mas de una o simplemente necesitamos una, y no podemos permitir que otras existan.

Por ejemplo:
- No necesitamos muchos sistemas de archivos, ni manejador de ventanas
- Necesitamos solo un conversor de A/D en un sistema eléctrico
- Conectores a bases de datos 

 Por ende, hacer una variable global para eso es imprudente, porque igual deja el espacio para que tu crees una instancia de la misma. Por este motivo, ***hacemos a la clase responsable de manejar su propia creación***

Representación en UML

![[Pasted image 20240907185832.png]]

Implementación en Python

```
clas SingletonMeta(type):
    _instances = {}

    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            instance = super().__call__(*args, **kwargs)
            cls._instances[cls] = instance
        return cls._instances[cls]

class Singleton(metaclass=SingletonMeta):
    def some_business_logic(self):
      pass

if __name__ == "__main__":
    # The client code.

    s1 = Singleton()
    s2 = Singleton()

    if id(s1) == id(s2):
        print("Singleton works, both variables contain the same instance.")
    else:
        print("Singleton failed, variables contain different instances.")
```

## Patron Facade
Continuar lectura y posibles ejemplos prácticos en la nota [[Patron Facade]]

Tipo: Estructural

La intención detrás de este patron es brindar una interfaz unificada y manejable para un conjunto de otras interfaces dentro del sistema. La fachada cumple una funcion de hacer el sistema mas sencillo de usar 

La creacion de subsistemas dentro de nuestro sistema ayuda a manejar la complejidad, sin embargo, creamos dependencias y comunicaciones. Esa es la motivacion de la fachada, brindar un sitio unificado donde todo eso pase y exponer una sola cosa para su uso.

![[Pasted image 20240907191629.png]]

De esta manera evitamos que la persona que realize la codificacion tenga conocimiento de todas las clases que interactuan en el sistema, el solo necesita usar la fachada y acceder a sus metodos que se encargna de manejar su complejidad.

Representacion en UML

![[Pasted image 20240907192043.png]]

Implementacion en Python

```python
from __future__ import annotations

class Facade:
    def __init__(self, subsystem1: Subsystem1, subsystem2: Subsystem2) -> None:
        self._subsystem1 = subsystem1 or Subsystem1()
        self._subsystem2 = subsystem2 or Subsystem2()

    def operation(self) -> str:
        results = []
        results.append("Facade initializes subsystems:")
        results.append(self._subsystem1.operation1())
        results.append(self._subsystem2.operation1())
        results.append("Facade orders subsystems to perform the action:")
        results.append(self._subsystem1.operation_n())
        results.append(self._subsystem2.operation_z())
        return "\n".join(results)

class Subsystem1:
    def operation1(self) -> str:
        return "Subsystem1: Ready!"

    # ...

    def operation_n(self) -> str:
        return "Subsystem1: Go!"

class Subsystem2:
    def operation1(self) -> str:
        return "Subsystem2: Get ready!"

    # ...

    def operation_z(self) -> str:
        return "Subsystem2: Fire!"

def client_code(facade: Facade) -> None:
    print(facade.operation(), end="")

if __name__ == "__main__":
    # The client code may have some of the subsystem's objects already created.
    # In this case, it might be worthwhile to initialize the Facade with these
    # objects instead of letting the Facade create new instances.
    subsystem1 = Subsystem1()
    subsystem2 = Subsystem2()
    facade = Facade(subsystem1, subsystem2)
    client_code(facade)
```

## Patron Mediador
Continuar lectura y posibles ejemplos prácticos en la nota [[Patron Mediador]]

Tipo: Comportamiento

La intención detrás de este patron la creación de un objeto que encapsule como un conjunto en particular de objetos interactua. El patron Mediador promueve un bajo acoplamiento manteniendo a cada objeto sin referirse entro si (de manera explicitia), por esto, podemos usarlos de manera independiente

En la POO se prueba la distribución de comportamiento entre objetos. Dicha distribución puede resultar en objetos relacionados con otros objetos. En el peor caso, todos saben de la existencia de otro objeto.

Aunque esta creación ayuda a la reusabilidad, las conexión pueden hacer que esa ayuda se pierda. De igual manera, generamos que los objetos entre si tengan una ***dependencia***, 

Imagina una ventana, siempre hay una dependencia entre dichos objetos, el botón se deshabilita cuando un campo esta habilitado, y este nace de un **list box**. Los diálogos pueden tener distintos comportamientos entre los widgets que usan, entonces aunque el dialogo muestre widgets (hasta del mismo tipo), ellos no pueden re-utilizar los widgets, y hacer muchas subclases seria tedioso.

Imagínate si tuvieras una … para eso existe el objeto ***mediador***, que se encarga de encapsular comportamiento colectivos. Este es responsable de ***controlar*** y ***coordinar*** la interacción entre un grupo de objetos. Los objetos solo conocen al mediador, no al resto de clases.

Siguiendo el caso de la ventana, imagínate un mediador llamado ***FontDialogDirector*** puede ser el mediador entre los widgets y su dialog.

![[Pasted image 20240907193423.png]]

En un diagrama de interacción se vería así

![[Pasted image 20240907193448.png]]

Asi podriamos observarlo en forma de clases
![[Pasted image 20240907193536.png]]

Representación general en UML

![[Pasted image 20240907193639.png]]

Implementación en Python

```python
from __future__ import annotations
from abc import ABC

class Mediator(ABC):
    def notify(self, sender: object, event: str) -> None:
        pass

class ConcreteMediator(Mediator):
    def __init__(self, component1: Component1, component2: Component2) -> None:
        self._component1 = component1
        self._component1.mediator = self
        self._component2 = component2
        self._component2.mediator = self

    def notify(self, sender: object, event: str) -> None:
        if event == "A":
            print("Mediator reacts on A and triggers following operations:")
            self._component2.do_c()
        elif event == "D":
            print("Mediator reacts on D and triggers following operations:")
            self._component1.do_b()
            self._component2.do_c()

class BaseComponent:
    def __init__(self, mediator: Mediator = None) -> None:
        self._mediator = mediator

    @property
    def mediator(self) -> Mediator:
        return self._mediator

    @mediator.setter
    def mediator(self, mediator: Mediator) -> None:
        self._mediator = mediator

class Component1(BaseComponent):
    def do_a(self) -> None:
        print("Component 1 does A.")
        self.mediator.notify(self, "A")

    def do_b(self) -> None:
        print("Component 1 does B.")
        self.mediator.notify(self, "B")

class Component2(BaseComponent):
    def do_c(self) -> None:
        print("Component 2 does C.")
        self.mediator.notify(self, "C")

    def do_d(self) -> None:
        print("Component 2 does D.")
        self.mediator.notify(self, "D")

if __name__ == "__main__":
    # The client code.
    c1 = Component1()
    c2 = Component2()
    mediator = ConcreteMediator(c1, c2)

    print("Client triggers operation A.")
    c1.do_a()

    print("\n", end="")

    print("Client triggers operation D.")
    c2.do_d()
```