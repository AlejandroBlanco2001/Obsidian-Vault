---
tags:
  - master
  - cloud
LInk: https://learning-oreilly-com.ezproxy.uniandes.edu.co/library/view/cloud-native/9781492053811/ch03.html#scalability_and_cost
---
Una de las principales diferencias entre las arquitecturas tradicionales y las basadas en las nube es

> Como se maneja el estado (Session state, application and configuration data, y así)

Naturalmente, las arquitecturas tradicionales eran ***statefull***, donde todo era contenido en la maquina host

>[!INFO]
>Por esta razón, los balanceadores de carga contaban con una sticky session

Por ende, ante un fallo en alguna de nuestras maquinas era necesario mover dicho estado a otra (o volverlo a crear en la nueva)

![[Pasted image 20250811171950.png]]

Implementación con algo cloud native

![[Pasted image 20250811172005.png]]

Sin embargo, en las aplicaciones enfocadas en la nube, el estado es externalizado y nuestros servicios hechos de una manera que no depende de el, con el fin de no afectar a nuestros usuarios y su experiencia.

De igual manera, las aplicaciones monolíticas contaban con una comunicación sincrónica donde un servicio en particular era el encargado de redirigir al servicio en cuestión

![[Pasted image 20250811172339.png]]

Por otro lado, en los cloud native se busca una coreografía basada en eventos

![[Pasted image 20250811172408.png]]