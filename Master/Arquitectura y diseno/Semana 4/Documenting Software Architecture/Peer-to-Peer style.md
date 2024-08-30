Tags #arquitectura-de-software #design #estilo-arquitectonico #componentesyconectores

El estilo de peer-to-peer (red entre pares), los componentes son directamente pares que se intercambian servicios. La comunicacion que se presentan en este parecida a la de request/reply, sin embargo, ***no es asimetrica***.

Esto permite que cada par pueda interactuar (en teoria) con cualquier otro componente, solo solicitando sus servicios. 

Cada componente par provee y consumo servicios similar, y a veces, todos los pares son instancias del mismo tipo de componente. 

Los conectores en este estilo, involucran protocolos bidireccionales complejos de interaccion, reflejando el doble sentido de cada comunicacion enrre componentes.

Ejemplos como:
- Redes de intercambio de archivos
	- BitTorrent
	- eDonkey
- Mensajeria instantanea
- VoIP
	- Skype

## Elementos, relaciones y propiedades

En este estilo, los componentes son ***pares***, que usualmente son programas independientes que corren en nodos de red. El principal conector siguen siendo el call-return.

A diferencia del estilo [[Client-Server Style]], la interaccion puede ser causada por cualquiera de los dos componentes. Los pares tienes interfaces que describen los servicios que solicitan de los otros pares y los servicios que provee. 

El flujo de este estilo, es simetrico. El par se conecta primero a la red peer-to-peer and luego inicias las acciones para conseguir la computacion por medio de la cooperacion con otro par pidiendo los servicios del otro

## Casos de uso

Al cada par actuar como un cliente y un servidor, provoca que este sea un sistema altamente distribuido. Esto permmite que quitar una par, no afecte al sistema en si, siendo esto un sistema altamente ***escalable***.

Muchas veces los pares tienen sobreposicion de capacidades, como prover acesso al mismo set de datos. Por ende, un par actuando como cliente puede colaborar con multiples acciones de pares (que actuan como servidores) para completar una tarea.

>[!NOTE]
>Si alguno de estos falle, siempre habra otro para responder su necesidad.

Esta capacidad mejora su ***disponibilidad***. Esto puede afectar a guardas las cosas de manera local, mas que tener un sistema central

Usualmente esto es usado en sistemas como:
- Redes de compartir archivos
- Mensajeria instantana

Hacer un despliegue eficiente, haria que la aplicacion haga uso eficiente de la CPU y el manejo de espacio de disco por medio de la red de pares que se ayudan mutuamente, y haciendo uso del sistema local. 

![[Pasted image 20240830000940.png]]