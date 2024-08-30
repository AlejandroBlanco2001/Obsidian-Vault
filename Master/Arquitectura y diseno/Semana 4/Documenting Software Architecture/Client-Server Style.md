Tags #arquitectura-de-software #diseno-uml #estilo-arquitectonico #componentesyconectores 

Es un estilo donde los servicios exponen un set de servicios que pueden ser invocados por otro componentes. Esta invocacion ***bloquea*** el llamado hasta que este queda realizado por completo.

>[!NOTE]
> Podemos decir que basicamente su analogo a nivel de codificacion es el una funcion

Ejemplos de este estilo incluye:
- REST
- Cliente-Servidor
- Peer-to-peer

## Vista general

En este estilo, se pueden denominar a los que piden como ***clients*** y los proveedores del servicio se denominan ***servers***, que proveen un set de servicios a traves de uno o mas puertos. 

Algunos componentes pueden actuar como (clientes y servicios), tambien pueden existir casos donde hay un servidor central o muchos distribuidos. 

Ejemplos de estos sistemas:

- Sistemas de informacion corriendo en servidores locales, donde los clientes son aplicaciones visuales y las bases de datos son los clientes

- Aplicaciones web, donde el cliente corre en un navegador web, y el servidor son los componentes ejucutandose en un servidor web (Apache, por ejemplo)


![[Pasted image 20240829224210.png]]
## Elementos 

En este los componentes son de tipo ***cliente y servidor***. Donde los principales conectores son el ***request/reply*** usado para invocar servicios. Donde mas de un servicio puede ser solicitado por el mismo conector, se necesita especificar un protocolo para especificar la comunicacion.

Los servidores cuentan con puerto que describen los servicios que proveen. Los clientes cuentan con puertos que describien que requieren.

El flujo de cliente-servidor es ***asimetrico***, es decir, el cliente inicia la peticion y sabe con antelacion que necesita y de quien, pero, el servidor no sabe de antemano dicha informacion.

La invocacion del servicio es sincrona: El solicidator del servicio ***espera***, o se bloquea, hasta que la peticion es recibida,

## Para que sirve

Esta vista sirva para presentar un sistema que separa al cliente de los servicios que usa. Este estilo soporta el entendimiento del sistema y reusa factorizando servicios comunes. 

Estos servicios permiten multiples clientes, y estos mismos pueden ser replicados con fines de ***escalabidad*** y ***disponibilidad***.

