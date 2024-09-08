Tags #ToDo 

El desempeño es hablar sobre tiempo de respuesta, es nuesta capacidad de responder ***requisitios de tiempo***. Como algo curioso, recordemos que toda operacion toma tiempo en un computador.

>[!NOTE]
>Los computadores miden en nanosegundos la respuesta, el acceso al disco toma tiempo en el orden de milisegundos y el acceso por red toke alrededor de 100 milisegundos para mensajeria intercontinental.

Para poder responder sobre los eventos que ocurren en nuestro sistema (iinterrupciones, mensajes, mensajes entre usuarios), debemos entender y caracterizar los eventos que puedan ocurrir en nuestro sistema (Cuando y como pasan) y los elementos asociados a nuestro sistema que responden.

Para una aplicacion basada en la web los eventos vienen en forma de peticiones por el usuario (se cuentan por decenas o decenas de millones) por medio de clientes como el navegador web. Los servicios obtienen eventos por medio de otros servicios. En un sistema de control para la combustion interna de un motor, los eventos vienen del operador que maneje el operador.

En un sistema basado en la web, una base de datos central, o en un sistema que se encarga de procesar entradas desde el entorno, la respuesta deseada puede ser expresada como la cantidad de respuestas procesadas en un tiempo particular. En el sistema de control, la respuesta podría ser la variación admisible del tiempo de combustion.

Recordemos que el desempeño es un atributo de calidad ***siempre deseado***, sin embargo, muchas veces choca con otros atributos de calidad.

>[!IMPORTANT]
>Recordemos que siempre tendremos el tema de que un computador puede resolver un problema, la cuestion es la rapidez del mismo para hacer util el proceso

Podemos afirmar que un gran amigo es la ***escalabilidad***

## Escenario general

Este comienza con un evento llegand a nuestro sistema. Contestar de manera correcta al evento requiere ***recursos*** (incluye el tiempo) que sean consumidos. Mientras esto sucede, el sistema puede ser estar contestando otros eventos

### Concurrencia

Es el concepto mas importante que un arquitecto debe entender (increiblemente es uno de los menos tratados tambien en los cursos de CS). Concurrencia es operaciones ocurriendo de forma paralela. Por ejemplo, imaginemos que un hilo ejecuta

```javascript
let x = 1;

x==;
```

Y otro hilo ejecuta los mismas sentencias. Cual deberia ser el valor de x despues de que ambos hilos ejecutaran ambos sentencias?

La concurrencia ocurre cuando en cualquier momento tu sistema crea un nuevo hilo, porque los hilos por definicion, son secuencias independientes de control. Cuando tienes multiples usuarios en tu sistema, los hilos hacen parte de ese trabajo.

La concurrencia ayuda mucho a resolver temas de desempeño, sin embargo, siempre hay que estar conscientes, de que pueden succeder ***race conditions***, basicamente donde dos o mas hilos tratan de acceder a un mismo recurso.

Dos posibles soluciones podrian ser:

- Bloquear un recurso una vez accedido
- Crear dos recursos, basicamente uno por hilo

Los errores asociados a estos temas pueden ser un dolor de cabeza, debido a que requieren una coordinacion milimetrica para ser repetidos. 

Por esto mismo, no debe darte miedo utilizar la concurrencia, simplemente usala bien y sabiendo que puede y que no puede pasar 

## Escenarios 


| Parte del escenario    | Descripcion                                                                   | Posibles valores                                                                                                                                                                                                                 |
| ---------------------- | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Fuente                 | El estimulo que hace que el evento suceda<br>en primera instancia             | Externos<br>- Peticion del usuario<br>- Peticion de otro sistema<br>- Datos entrando de un sensor u otro sistema<br><br>Internos<br>- Un componente hace una peiticion a otro componente<br>- Una generacion de una notificacion |
| Estimulo               | Es la llegda del evento                                                       | Puede ser de tipo periodica, esporadica o estocastica                                                                                                                                                                            |
| Artefacto              | Lo que sera estimulado, es decir, que sera afectado por el estimulo.          | - Todo el sistema<br>- Un componente del sistma                                                                                                                                                                                  |
| Entorno                | El estado en que el sistema recibe el estimulo                                | - Estado normal<br>- Estado de emergencia<br>- Estado de correcion de errores<br>- Estado de carga maxima<br>- Estado de sobrecarga<br>- Estado de degradacion<br>- Algun otro estado                                            |
| Respuesta              | La manera en que el evento responde al sistema                                | - Retorna una respuesta<br>- Retorna un error<br>- Sistema genera una respuesta<br>- SIstema ignora la peticion<br>- Sistema cambia el modo del servicio<br>- Sistema sirve un evento de mayor prioridad                         |
| Medida de la respuesta | Medida de tiempo para comparar el resultado y poder contabilizar el resultado | - El (maximo. minimo, promedio, mediana) tiempo de respuesta (latencia)<br>- Numero de respuestas satisfactorias/rechazdas en un intervalo de tiempo<br>- Porcentaje de uso de recursos.<br>                                     |
![[Pasted image 20240907181030.png]]