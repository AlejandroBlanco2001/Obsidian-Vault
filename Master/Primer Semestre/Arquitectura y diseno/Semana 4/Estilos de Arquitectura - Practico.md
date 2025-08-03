---
tags:
  - atributos-de-calidad
  - diseno-uml
  - arquitectura-de-software
  - master
---
Imagina que tiene dos componentes:
- Cliente: Encargado de la gestion de los clientes
	- Datos basicos del cliente
	- Logica de negocio asociada al cliente
- Envio: Encargado de la gestion de los envios
	- Datos de entrega del envio
	- Logica de negocio asociada al envio

Forma de solucionar el problema de conectarlas 

![[Pasted image 20240831013051.png]]

El Cliente conoce los servicios por medio de la interfaz expuesta de Envios, es una comunicacion sincronica y directa. Envio debe estar siempre presente, si algo pasa, hay una falla de disponibilidad.

En este caso favoremos la ***latencia***, pero perjudicamos la ***disponibilidad*** y ***facilidad de modificacion***

![[Pasted image 20240831013145.png]]

Menos acoplamiento, pero tenemos la necesidad de un medio de comunicacion intermediario ***broker***. El componente Cliente debe estar disponible para el componente Envió, de lo contrario, hay una falla de disponibilidad.

![[Pasted image 20240831013311.png]]

Ya no hay comunicación directa, por medio de un mensaje a través de una cola de mensajería. Si al momento de enviar el mensaje el servicio no esta disponible, no pasa nada, cuando lo este, recibirá el mensaje y lo hara. 

Tenemos ***mayor disponibilidad*** y ***facilidad de modificación*** pero ***menor tiempo de respuesta***

Un estilo de arquitectura establece normas, lineamientos e instrucciones sobre como debemos construir modelos de arquitectura.

Nos define la forma en como se definen los elementos dentro del modelo, es decir, su topologia.

![[Pasted image 20240831013741.png]]