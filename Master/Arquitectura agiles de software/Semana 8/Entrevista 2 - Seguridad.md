Tags #seguridad #arquitectura-de-software 

- Al momento de trabajar microservicios, estos se ven directamente afectados por la ***ley de Conway***, que establece que un sistema es un fiel reflejo de las estructuras sociales de las personas que lo crean.
	- Por ejemplo, imagina que tienes un microservicio A desarrollado por el equipo A, y tienes otro microservicio B desarrollado por el equipo B, puede darse el caso donde uno de los dos microservicios no tenga las mejores practicas de seguridad posible.

- Existe un planteamiento teórico que enuncia que la seguridad y el desempeño son atributos inversamente proporcionales
	- En la practica, esto también es una realidad, sin embargo, no es tan pronunciado.
	- El tema de seguridad afecta pronunciadamente el tema de la velocidad de desarrollo.
	
- Algunas de las fuentes de seguridad mas recientes son:
	- OWASP
	- Herramientas de análisis estático (SonarQube)
	- NIST
	- IEEE

- El mayor error siempre sera dejar la seguridad como lo ultimo

- Para mezclar agilismo, arquitectura y seguridad, debemos tomar iniciativas para ***propagar una cultura***
	- Recordemos que tener una ruta de producto y fechas de entrega siempre sera un limitante
	- Una política de constitución microservicios, es una receta para estipular que debe tener si o si un microservicio

- El mayor problema entre que el plantea una arquitectura y el que la desarrolla, es que el ***contexto que tienes influye mucho***

