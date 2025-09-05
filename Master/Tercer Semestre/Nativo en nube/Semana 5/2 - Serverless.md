---
tags:
  - master
  - cloud
---
> Un modelo de computación en el que los consumidores del servicio no quieren invertir su tiempo en aprovisionar, mantener, actualizar, escalar y planear la capacidad de sus servidores 

 Esto tiene las siguientes características:

- No *requiere gestionar* un servidor o instancia
- Responde a la *demanda requerida*
- No esta pensando para que *tenga capacidad planeada*
- No requiere que se configure *reglas de auto scaling* 
- Es *altamente disponible*
- No hay *costoso por el tiempo ocioso*, y algunos servicios tienen *costos precisos por uso*

Algunos de sus casos de uso son:

- Las tareas son *asíncronas, concurrente, fáciles de pararelizar* 
- La demanda es *infrecuente o esporádica*, con una variación grande e impredecible en términos de escalabilidad
- Las tareas no tienen *estado, son efímeras y no requieren un arranque* (cold start)
- Altamente dinámico en términos de requerimiento

Ejemplos textuales
- Procesamiento de elementos multimedia
	- Atomicos
	- Paralelizables
	- Infrecuentes
- Reaccionar a los cambios en una fuente de información
	- Logs, notificaciones o actualizar otra base de data
		- Atomico
		- Infrecuente
- Mensajes de sensores IoT / Streams de datos
	- Elasticidad
	- Atomicos
	- Paralelizable
- Chatbots
	- Elasticidad
	- Atomicos
	- Paralelizable
	- Costo eficiente
- Tareas en batch
	- Elasticidad
	- Atomicos
	- Paralelizabble
	- Costo eficiente
- Backend para aplicaciones moviles y aplicaciones moviles
	- BaaS
	- Mejores tiempos y costos
- Pipelines
	- Elasticidad
	- Atomicidad
	- Infrecuentes