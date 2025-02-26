Tags: #microservicios #arquitectura-de-software #disponibilidad #atributos-de-calidad #tacticas-arquitectura 

El problema de la comunicación sincrónica es que al presentar una falla en la comunicación entre dos microservicios, presentábamos indisponibilidad.

Sin embargo, existe una alternativa, que es la *comunicación asíncrona*, por medio de mensajes, por ejemplo.

Por ejemplo, si mandamos un mensaje y el servicio que lo va a recibir se encuentra indisponible, este mensaje puede persistir y puede ser recuperado posteriormente cuando este otra vez disponible.

> Las colas de mensajería se encargan de este trabajo

Gracias a esto uno debe tener en cuenta de mezclar correctamente la comunicación asincrónica y síncrona.
