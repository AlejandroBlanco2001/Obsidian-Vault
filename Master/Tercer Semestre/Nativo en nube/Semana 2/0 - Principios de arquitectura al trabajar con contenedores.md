---
tags:
  - microservicios
  - docker
  - k8s
  - master
  - cloud
---
Podemos plantear que estos hacen uso de los principios SOLID, por ejemplo,
cada contenedor debo hacer una cosa exclusivamente, no puede hacer nada mas (Principio de responsabilidad única)

> [!INFO
 > Siempre debemos procurar tener uno sola razón para hacer el cambio en un contenedor
 
Otro principio es de la ***observabilidad***, recordemos que estos son cajas negra pero debemos tener una capacidad de tener mejor trazabilidad, consumir sus estados para tomar mejores decisiones y mejor monitor.

Por otro lado, queremos tener el *principio de conformidad de ciclo de vida*, donde queremos tener un control de un contenedor con comandos fuera del mismo. Por ejemplo, al recibir un *SIGTERM*, el debe poder hacer algo con respecto a este mensaje

> [!INFO]
> Es opcional aplicarlo, pero debemos siempre preguntarnos sobre su ciclo de vida y como manejarlos
> 

El ***principio de inmutabilidad***, nos implica a manejar nuestras imágenes como versiones para poder retroceder o avanzar sin miedo.

El ***principio de desechabilidad*** indica que todo contenedor puede ser detenido y remplazado sin afectar nuestra operación.

> [!INFO]
> Si nuestros contenedores manejan estado, es un problema para el principio anterior