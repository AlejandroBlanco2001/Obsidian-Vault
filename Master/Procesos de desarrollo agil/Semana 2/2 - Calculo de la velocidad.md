Tags #Agilismo  

Recordemos lo mencionado en [[1 - Fase de planeación de la fase de inicio]] sobre la velocidad

> Es la cantidad de puntos de usuarios que se pueden resolver por sprint 

Para realizar el calculo inicial debemos tener en cuenta dos cosas:
- Actividades para completar las historias de usuario
	- A partir de la arquitectura (Detalle de la historia base es lo primero)
	- Calcular el numero de horas en las historias de usuario base
		- Con esto podemos determinar cuantas horas equivalente a un cierto puntos de usuario (PPH)
- Capacidad de trabajo del equipo
	- Dedicación 
	- Efectividad (Horas efectivas)
	- Horas efectivas por sprint (3 semanas, 40h x semana, 120h x sprint)

![[Pasted image 20250201123822.png]]

Donde la suma de dichas horas, en este caso 309 horas, son las horas efectivas del equipo por sprint (HRP)

$$velocidad = \frac{HRP}{PPH}$$

Por ejemplo en este caso,

$$V= \frac{309}{13} = 24 $$
Por ende, podemos hacer 24 historias de usuario por sprint.

