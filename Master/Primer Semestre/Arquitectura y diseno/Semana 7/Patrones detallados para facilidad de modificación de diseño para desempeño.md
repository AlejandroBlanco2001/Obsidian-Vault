---
tags:
  - master
  - arquitectura-de-software
  - modificacion
  - performance
---

El atributo de calidad de facilidad de modificación se refiere a disminuir:
- Menor tiempo posible
- Menor esfuerzo posible
- Menor impacto posible

Uno de los principales problemas de los objetos, es el proceso de ***creación***, y luego la asignación de su responsabilidad como lo es discutido en los patrones [[GRASP - Lectura]],de igual manera, esto es tratado por los patrones [[Principios SRP y DIP]].

Algunos de los patrones que podemos usar:
- Creación (GoF)
- Creador (GRASP)
- Inversion de dependencias (SOLID)

![[Pasted image 20240921004259.png]]

Aproximación 1

![[Pasted image 20240921004318.png]]

En este caso, si el software escala, el *Envió* debería cambiar porque el *Envió* y la *Notificación* pueden cambiar o incluir nuevas cosas.

Aproximación usando la inversion de control
	![[Pasted image 20240921004532.png]]
