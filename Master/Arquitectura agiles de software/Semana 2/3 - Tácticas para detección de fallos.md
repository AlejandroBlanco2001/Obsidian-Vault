---
tags:
  - arquitectura-de-software
  - disponibilidad
  - atributos-de-calidad
  - master
---
Primero debemos detectar eventos que ocasionen fallos:

- **Omisión**: El sistema no responde ante un estimulo
- **Caída**: El sistema repentinamente presenta fallas de omisión
- **Tiempo**: El sistema responde a un estimulo a destiempo
- **Respuesta**: El sistema responde al estimulo pero de manera incorrecta.

Algunas de las tácticas que tenemos para **detección de fallas** son:

- Monitor: Un componente donde podemos hacer de ping-pong o heart-beat para detectar la disponibilidad del sistema
- Votación: Tres componentes (o un numero impar), donde mandan sus resultados a un componente central, donde se comparan los resultados, el resultado diferente es notificado de error

Otras tácticas para la **preparación y reparación**:

- Redundancia activa:  Se tiene un componente principal y redundante, donde todos hacen la operación para estar sincronizados y se pueden sustituir.
- Redundancia pasiva: Se tiene un componente principal y redundante, pero *periódicamente* todos hacen la operación para estar sincronizados y se pueden sustituir
- Degradación: Los recursos deben ir a los componentes de mayor prioridad que estén siendo degradados.
- Reconfiguración: En caso de falla, se registra el componente ente defectuoso y se retira este, su responsabilidad es distribuida.

Otras tácticas para la **reintroducción**:
- Shadow: Una vez se repara la falla, se coloca en un ambiente controlado para su monitoreo, una vez todo este bien, se puede subir de nuevo a producción.
- Resincronización de estado: Contamos con un **componente sincronizador** que se encarga de entregar el estado a este componente que ha sido colocado como redundante o principal.

Por ultimo para la **prevención de fallas**:

- Retiro de servicio: Ante la sospecha de falla, retiramos el componente
- Modelo predictivo: Teniendo en cuenta el histórico, un modelo predictivo puede darse cuenta de que este posiblemente falle. 

Recordemos, todo nuestro sistema debe tener en cuenta dos principios: ***Fallar con gracia*** y ***recordar el fallo***, esto quiere decir que:

- El sistema debe siempre pensar que va a fallar, así que manejemos el error de la mejor manera posible
- El sistema debe siempre guardar los logs de lo que paso, tener toda la información posible para ser estudiado.

Es importante siempre tener en cuenta que los procesos y componentes deben ser replicables en otros nodos de ejecucción.