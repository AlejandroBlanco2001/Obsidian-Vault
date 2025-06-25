---
tags:
  - diseno-uml
  - estilo-arquitectonico
  - arquitectura-de-software
  - componentesyconectores
  - master
---
Consiste en una coleccion de componentes distrubuidos que proveen y/o consumen servicios. Estos consumidorses y provedores pueden estar implementados en distintos lenguajes y plataformas. 

Los servicios deben ser completamente standalone (independiente): consumidores y proveedores son usualmente desplgados independiente, y muchas veces pertenecen a diferentes sistemas o hastas organizaciones

![[Pasted image 20240830073314.png]]
## Elementos, relaciones y propiedades

Los componentes basicos son los servicios proveedores y los servicios consumidores, que en practica pueden tomar distintas formas, es decir, desde un script corriendo en el navegador con JavaScript hasta un sistema transaccional con CICS corriendo en un mainframe.

Tambien puedes contar con componentes especializados que actuan como un intermediario:

- Invocacion de servicios pueden ser mediados por un ***ESB*** (Enterprise service bus). Un ESB se encarga de enrutar los mensajes entre el proveedor y su consumidor. 

> [!NOTE]
De igual manear, un ESB puede convertir mensajes de un protocolo o tecnologia a otro, transformacon de datos, chequeos de seguridad y transacciones. Este actua como un hub-and-spoke e incrementa ***interoperabilidad***, ***seguridad*** y ***facilidad de modificacion*** se mejoran

- Para que la ubicacion de los servicios sea transparente, tenemos al ***service registry*** . Este registro es un componente que permite a los servicios a ser registrados y consultados en tiempo de ejecuccion. Este incrementa la facilidad de ***modifiacion***, porque permite localizar el proveedor del servicio al proovedor de consumo permitiendo multiples versiones en vivo del mismo servicio.

- Un ***servidor de orquestracion*** (o motor de orquestracion) es un componente especial que ejecuta scripts al momento de pasar cierto evento (por ejemplo, una vez se compre algo en una tienda). Se encargar de orquestrar la interaccion entre consumidores y servicios. 

>[!NOTE]
>Empresas que manejan un flujo definido y organizado, se ven beneficiados de este componente, en temas de ***facilidad de modificacion***, ***interoperabilidad*** y ***fiabilidad***

Los conectores basicos en esta arquitectura son:

- Call-return:
	- SOAP: Se hacen las peticiones request/reply por XML, tipicamente se hacen por encima de HTTP
	- REST: Se hacen las peticiones sincronicamente a traves de peticiones HTTP. Se basa en los cuatro verbos basicos (GET, POST, PUT y DELETE) sobre recursos. Usualmente se usa notaciones JSON.
-  Mensajeria asincronica: Los componentes se comunican por medio de una cola de mensajes (Apache ActiveMQ, RabbitMQ...). Los conectores pueden ser point-to-point o de tipo publish-susbscribe. Estos ofrecen ***confiabilidad*** y ***escalabilidad***

Usualmente, en la practica toda arquitectura SOA usa todos estos al mismo tiempo

## Casos de uso

Su principal fuerte es la ***interoperabilidad***, debido a que todos estos elementos estaran corriendo en distintos entornos o lenguajes, estos tiene una mayor facilidad de ser integrados. Esto permite integrar nuevos servicios o servicios de internet de manera sencilla gracias al ESB. 

![[Pasted image 20240830081138.png]]