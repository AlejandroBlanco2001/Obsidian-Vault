Tags #arquitectura-de-software #diseno-uml 

Para diseñar arquitecturas hay muchas maneras, como por ejemplo:

- ad-hoc (Informales, bajo esfuerzo, no recomendable)
- tradicional
	- Enfoca la fase de arquitectura como una parte inicial del software
	- El diseño de arquitectura es fundamental para iniciar el software
	- Se caracteriza por tener muchas cosas en cuenta, gracias a su larga duración
	- No abierto al cambio debido a su larga duración 
- adaptativos
	- Se inspira en los procesos agiles
	- Se encarga de hacerse por Sprint
	- Se divide en
		- Especificación de requisitos de calidad
		- Diseño mínimo que satisfaga un conjunto de requisitos de alto valor  
		- Validación de la idea
	- Al finalizar, se evalúa los resultados y se comienza de nuevo
	- La etapa de requisitos, van de dos tipos:
		- Funcionales
		- Calidad
	- Las etapa de diseño encierra decisiones criticas para el éxito de la arquitectura
		- Se documenta en **modelos de arquitectura** dentro de **vistas**
	- La etapa de validación busca tener certeza de nuestras decisiones
		- Cambiar decisiones de diseño
		- Re-plantear los requisitos de calidad
		- Cambiar los modelos

Para esta primera fase (Requisitos) hablamos de la creación de escenarios de calidad (descritos en [[Introduccion a las especificaciones de requisitios de calidad]]), sin embargo, podemos construir unas ***historias de arquitectura***, donde podemos representar dichos escenarios como historias de usuario.

> Como *fuente* cuando *estimulo* dado que *ambiente* quiero *funcionalidad* para *respuesta*. Este debe suceder *medida de la respuesta* 

Como con las historias de usuario, tenemos los mismos problemas, por lo cual podemos usar las siguientes reglas:

- Solo se tiene una fuente
- Solo se tiene un estimulo
- Solo se tiene un ambiente
- Solo se tiene una unidad para la medida de respuesta

También tendremos todas nuestras historias de arquitectura en nuestro **Backlog de Arquitectura**