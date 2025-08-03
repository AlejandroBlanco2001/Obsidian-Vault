---
tags:
  - arquitectura-de-software
  - disponibilidad
  - microservicios
  - estilo-arquitectonico
  - master
---
> Los sistema distribuidos son una colección de **computadores independientes** que a la vista del usuario se ven como **un solo sistema** coherente

Teniendo esto en cuenta, debemos recordar un sistema distribuido  es un grupo de **componentes** conectados a una red que los comunica unos a otros.

 Esto trae la ventaja de que múltiples entidades **autónomas** que deben trabajar en conjunto como un solo sistema coherente (Componentes mas reducidos)

Sin embargo, alguno de los retos que traen estas **múltiples entidades**, es que deben representar **un solo sistema uniforme**, por ende, el monitoreo y coordinación es algo complejo.

Por ende, de esto nacen los **microservicios**, donde este estilo busca reducir la complejidad inherente al diseño y aplicación de los ***sistemas distribuidos***.

En este estilo, cada capacidad de negocio esta construido como un servicio.

> Servicios pequeños y autónomos que trabajan en conjuntos

Para este caso trabajaremos con una modificación de la arquitectura hexagonal (Ver mas en [[Hexagonal]]) (O patrón de puertos y adaptadores )

Los microservicios interactúan de varias como:
- Llamada retorno síncrono 
- Llamada retorno asíncrono
- Publicador - Subscriptor 

Debemos siempre tener en cuenta, que hacen dichos microservicios con respecto a otro (flujo de control):

- Si este manda un **comando**: Solicitud o intención que busca un cambio en el sistema
- Si esta manda una **consulta**: Esto solo busca resolver una duda pero no altera el sistema
- Si este manda eventos: Estos representan la ocurrencia de una acción, no son una intención ni tampoco provocan cambios en el sistema


![[Pasted image 20250128215609.png]]

Si manejamos una comunicación síncrona, esto se hace a través de APIs, pero para la comunicación asíncrona usamos consultas, comandos y eventos a través de colas de mensajería. Con respecto al almacenamiento de datos, estos deben ser independientes de los demás.

Lo bueno de este sistema es su **independencia**, donde cada servicio se encarga de sus propios problemas. De igual manera, su proceso de despliegue es **independiente**, y no debería provocar fallos en otros microservicios.

De igual, favorecen tener distintas tecnologías por servicio. El mayor reto que tenemos es el ***proceso de construcción, pruebas y puesta a producción*** es compleja (Orquestación y coreografía).

Por otro lado, a medida de que introducimos la distribución, manejar el estado de la información es algo complejo, donde tenemos consistencia eventual.

Últimamente, la complejidad operacional es bastante notoria, donde tener ***una proliferación de microservicios***, genera un caos. 