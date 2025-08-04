---
tags:
  - cloud
  - master
  - sistemas-distribuidos
  - microservicios
---
> [!INFO]
> Para mayor contexto, leer [[4 - Sistemas distribuidos]]

Se define como

 > Sistema en el cual diversas maquinas de computo conectadas a través de la red se presentan como una sola maquina 

Al distribuir el poder de computo en diversas maquinas se benefician *la escalabilidad*, *la disponibilidad*, *la tolerancia a fallos* y *los costos*.

Algunas de las falacias que consideramos que puede traer problemas son:
- La red es confiable
- La red es homogénea
- La red es segura
- La latencia entre componentes cero
	- Debe pensarse en la cercanía a la información
- Hay ancho de banda infinito
- La topología no cambia
	- IP's estáticas
- Hay un administrador
- Costo de transporte es cero
	- Costo económico
	- Costo en latencia; serializar, deserializar