---
tags:
  - arquitectura-de-software
  - master
  - atributos-de-calidad
---
Para tener las especificaciones correctas, debemos tener claros y bien definidos nuestros requisitos funcionales.

Estos requisitos expresan el comportamiento esperado por el usuario con el sistema.

Por ejemplo

> El comprador debe recibir un numero de seguimiento para su envió

Otra persona nos dice luego

> En menos de un minuto a partir de que el numero sea asignado - ***Desempeño***

Otra persona añade 

> El 100% de las veces debe salir bien - ***Disponibilidad***

Otra persona dice

> Se deben poder enviar 500 números de seguimiento por minuto - ***Escalabilidad***

Otra persona finalmente añade

> Se deben poder agregar un nuevo mecanismo de comunicación en menos de 10 horas/hombre *- **Facilidad de modificación***

Podemos definir el atributo de calidad como:

> Propiedad ***cuantificable*** de un sistema, utilizada para indicar que tan bien ***satisface*** un sistema las necesidades de los usuarios interesados.

## Definiciones

| ***Atributo de calidad***   | ***Definicion***                                                                                                                                                                                                                                                                        |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Disponibilidad              | Propiedad del software que indica que esta listo para realizar sus tareas cuando es necesitado.<br><br>Podemos hablar de hardware y software.                                                                                                                                           |
| Interoperabilidad           | Grado en el que dos o mas sistemas pueden intercambiar informacion importante  mediante interfaces y en un contexto particular                                                                                                                                                          |
| Facilidad de ser modificado | Grado de riesgo y costo asociado a la adiccion de nuevas caracterisiticas, cambio o dad de baja de funcionalidades de un sistema, arreglo de defectos, mejora de la seguridad, o mejoramiento del desempeno                                                                             |
| Desempeno                   | Habilidad para cumplir los requerimientos a tiempo<br><br>- Latencia: TIempo transcurrido entre ocurrencia y respueta<br>- Escalabilidad: Capacidad de un istema de incrementar su capacidad de trabajo mientras continua desempenandose bien<br>                                       |
| Seguridad                   | Medida de la habilidad de un sistema para proteger datos e informacion de uso no-autorizado, entanto que sigue permitiendo su uso y accesos a las personas y sistemas autorizados.<br><br>- Integridad de los datos <br>- Confidencialidad de los datos<br>- Disponibilidad del sistema |
| Facilidad de ser probado    | Facilidad con la que el software puede ser construido para demostrar sus fallas mediante pruebas                                                                                                                                                                                        |
| Facilidad de uso            | Propiedad que determina que tan facil es para el usuario completer una tarea determinada y el tipo de sporte a usuario provisto por el sistema                                                                                                                                          |

## Atributos de calidad 

### Fuente
Persona (interna o externa), o componente que ejecuta la acción.

### Eventos
- Esporádico: No sabemos si pasara, pero puede pasar.
- Periódico: Que ocurre cada cierto tiempo.
- Estocástico: Que ocurre en cualquier momento, pero sabemos que puede pasar.

### Artefacto
Donde se aplica el estimulo. inicialmente, es el sistema completo

### Respuesta
Comportamiento esperado

### Medida de la respuesta
Condicion de calidad que se desea ver cumplida en la respuesta 

### Ambiente
Contexto del escenario, por ejemplo:
- Normal
- Caída
- DDOS

![[Pasted image 20240816114139.png]]

