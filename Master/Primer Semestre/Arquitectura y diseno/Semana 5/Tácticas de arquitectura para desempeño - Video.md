---
tags:
  - arquitectura-de-software
  - master
  - tacticas-arquitectura
---
Las tácticas son decisiones ***particulares*** y ***especificas*** para favorecer un atributo de calidad, modificando el estilo de arquitectura.

En este curso buscaremos estudiar las tacticas que favorecen la esacalibidad y la latencia de la manera:
- Control de acceso a recursos
	- Priorizacion de eventos
	- Incrementar la latencia de los recursos
	- Limitar la respuesta de los eventos
- Manejo de recursos disponibles
	- Introduccir concurrencia
	- Multiples nodos de procesamiento
	- Multiples copias de datos

Escenarios que debemos considerar

- Respuesta inmediata (Reserva de boleta de cine)
- Recibir un evento, responder una confirmacion inmediata y continuar procesando (Proceso de pago)
- Requiere recibir una respuesta inmediata y responder lo mas rapido posible a un alto volumen de datos. (Procesamiento de un volumen alto de datos)
- Recibir un evento, notificaf la confirmacion y la respuesta puede ser consultada despues, basicamente no requiere una respuesta inmediata (Examenes medicos)