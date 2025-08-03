---
tags:
  - Agilismo
  - master
---

>Todas las maneras de usar un sistema deben lograr un logro paritcular para un usuario particular

Un caso de uso es:

1.  **Secuencia de pasos finitos** que un sistema realiza para ver un valor observable en un usuario particular
2. **Ese comportamiento específico de un sistema** que participa en una colaboración con un usuario para entregar algo de valor para ese usuario.
3. **La unidad más pequeña de actividad** que proporciona un resultado significativo al usuario.
4. **El contexto para un conjunto de requisitos relacionados**.

![[Pasted image 20240811152406.png]]

## Introduccion

Los diagramas de casos de uso son mas viejos de lo que podemos imaginar, estos fueron los padres para la creacion de las ***historias de usuario***

Sin embargo, los diagramas de casos de uso ya estan un poco obseletos (en comparacion con las historias de usuario), por eso nace la iniciativa ***Use Case 2.0***

Este busca traer lo mejor de ambos mundos, donde tenemos la misma informacion importante de los diagramas antiguos junto con todos los atributos de las historias de usuario como:

- Arquitectura
- Diseño
- Test
- UX

## Porque sirven y son tan populares estos diagramas?

Estos fueron introducidos en [OOPSLA 87](https://dl.acm.org/doi/abs/10.1145/38807.38824) pero fueron adoptados alrededor del 92, gracias al libro "Object-Oriented Software Engineering - a Use-Case Driven Approach"

Estos diagramas con el tiempo han madurado y crecido en adopcion, sin embargo, deberian poder ***dirigir el desarrollo***

![[Pasted image 20240811153917.png]]
**Impacto en el ciclo de vida del desarrollo**: El enfoque de casos de uso no solo es útil para capturar requisitos y diseñar experiencias de usuario, sino que también influye en todo el ciclo de vida del desarrollo de software.
    
**Casos de uso clave y arquitectura**: Los "slices" de casos de uso son fundamentales para identificar la arquitectura de la aplicación y los componentes de diseño de software.
    
**Soporte al diseño dirigido por pruebas**: Los casos de uso son esenciales en el diseño dirigido por pruebas, ya que son los elementos que deben ser probados.
    
**Planificación y organización del trabajo**: Los casos de uso se utilizan para planificar sprints y organizar el trabajo con Kanban, colocándolos en el backlog o en el canvas.
    
**Modelado de negocios**: Los casos de uso reflejan los procesos de negocio, lo que facilita el modelado de negocios y ayuda a identificar los casos de uso del sistema a desarrollar.
    
**Facilitación de la reutilización de software**: Los casos de uso ayudan a encontrar elementos comunes, lo que dirige el trabajo de arquitectura hacia la reutilización de software.
    
**Intuitivos y ágiles**: Los casos de uso son intuitivos, ligeros, ágiles, escalables, versátiles y fáciles de usar, lo que los hace atractivos para quienes los conocen por primera vez.