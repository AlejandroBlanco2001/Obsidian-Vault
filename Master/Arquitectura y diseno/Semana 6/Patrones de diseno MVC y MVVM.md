---
tags:
  - patrones-de-diseno
  - master
  - arquitectura-de-software
---
El software siempre cambia durante su ciclo de vida;
- Nuevas tecnologias
	- Mejoras en la infraestructura
	- CAmbios en los lenguajes de programcaion
	- Cambios en los sistemas de almacenamiento
- Mejora en los algoritmos
	- Pago de deuda técnica
	- Nuevas tecnologías que permiten implementar nuevos algoritmos
	- Entendimiento del problema
- Defectos en el codigo
	- Defectos que se incluyen en el cilo de desarrollo
	- Pruebas no ejecutadas
- Cambios en el dominio de problema
	- Nuevos reglamentos o regulaciones
	- Modificacion interna
	- Cmabios en el objetivos del negocio

Siempre tenemos que recordar algo al momento de hacer cambios:
- Que puede cambiar?
	- Visualización
	- Lógica del negocio
	- Interacción con el usuario
- Que tan probable es?
	- Muy probable
	- Poco probable
	- Nada probable
- Quien hara el cambio?
	- Desarrolladores
	- Diseñadores
	- Usuarios finales
- Costo del cambio
	- Horas 
	- Dias
	- Dinero
# MVC

![[Pasted image 20240915153050.png]]

- Reducir el tamaño de los módulos (Si)
- Incrementar la cohesion (Si)
- Reducir el acoplamiento (No)
- Diferir la selección tecnológica (No es clara) 

![[Pasted image 20240915153156.png]]

![[Pasted image 20240915153222.png]]

Algunas tecnologías son:
- ASP.NET
- Rails
- Django

# MVVM

![[Pasted image 20240915153334.png]]

- Reducir el tamaño de los módulos (Si)
- Incrementar la cohesion (Si)
- Reducir el acoplamiento (Si, mas que el MVC)
- Diferir la selección tecnológica (No es clara)

![[Pasted image 20240915153358.png]]

Algunas tecnologías son:
- Angular
- ASP.NET Core
- Knockout
- Silverlight
