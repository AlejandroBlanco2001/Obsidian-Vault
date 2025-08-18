---
tags:
  - master
  - cloud
LInk: https://learning-oreilly-com.ezproxy.uniandes.edu.co/library/view/cloud-native-architecture/9781484272268/html/511610_1_En_3_Chapter.xhtml#:-:text=3.%20Cloud%20Native%20Architecture%20Principles
---
# Principios basados en la ejecución 
## Isolation Failure Principle

Recordemos que tener todo en la nube, no hace que nuestra aplicacion sea por defecto mas rápida o mas estable, debemos diseñar nuestras soluciones teniendo en mente como aislar los fallos.

Por ejemplo, debes preguntarte sobre la relacion de tus microservicios, los flujos que estan involucrados, que hacer ante un fallo, porque algo puede fallar.

Imagina que tienes 5 microservicios (A-E), donde es una cascada de fallos si E esta fallando

```
A -> B -> C -> D -X-> E
Por ende, nuestro microservicios esta en un fallo en cadena, generando un punto de fallo unico
```

## Deploy Independently Principle

Este principio estipula que todos nuestros microservicios (o servicios) deben poder ser desplegados de una manera individual sin necesidad de depender de otro servicio.

Recordemos que cuanto mas servicios estan en una maquina, mas problemas tienes para hacerles cambios de manera individual, esto aplica tanto para contenedores como maquinas.

- Haz un bundle del microservicio en una imagen de contenedor
- Despliega cada servicio como un contenedor
- Despliega estado e información fuera del contenedor

## Be Smart With State Principle

Este principio estipula como y cuando deberías guardar tu estado en el diseño, teniendo en cuenta que realizar esta acción no es la mas compleja, siempre deberías tratar de manejar carente de estado.

Recordemos que carente de estado, significa que este se encuentra fuera del contenedor, lo que nos permite deshacernos del contenedor sin ningún tipo de inconveniente.

Nuestros componentes que carecen de estado deben seguir:

- Facil de destruir y facil de crear
- Facil de reparar
- Capacidad de auto escalado horizontal/vertical
- Rollback

## Design for Failure Principle

Nosotros servicios deben estar hechos para tolerar el fallo, debido a que estos pueden fallar en cualquier momento. Por esto, debemos tener herramientas que nos permitan detectar estos fallos de una manera rápida, y en la medida de lo posible un arreglo automático.

- Desechable: Maximizar lo robusto para inicios rápidos y terminaciones sin problemas.
- Logs: Trata los logs como una corriente de eventos
- Dev/prod: Los entornos tanto de Dev como de Prod deben ser lo mas similar posible

# Principios basados en la seguridad

## Defense in Depth Principle

Este principio nos brinda de varias herramientas, mecanismo y controles para el manejo de las redes de computación para manejar confidencialidad, integridad y disponibilidad de nuestros servicios.

Debido a que estamos conectados a internet, debemos protegernos tanto a atacantes externos como internos, por ende el manejo de ***autenticación es necesario***, ademas de los siguientes mecanismos:

- Manejo fuerte de un gestor de credenciales
- Firewalls
- Prevención de intrusion o sistemas de detección
- Endpoint detection and response
- Segmentación de red
- Patch management
- Autenticación en la API
- Auditoria y consultoría

# Principios basados en la ingeniería de software

## Products Not Projects Principle

Es el hecho de mirar nuestro sistema mas que como un proyecto individual, como un conglomerado que actúa como producto y no tiene un fin sino que esta abierto a la constante mejora y debe ser construido con el fin de perdurar, alguno de los beneficios son:

-  Mejoramiento de la UX
- Arquitectura madura
- Cultura de la innovación y la automatización
- Aproximaciones por MVP
- Facilidad de extension, mantenimiento y prueba
- Mayor visibilidad en cuanto al funcionamiento real del sistema
- Retroalimentación constante

Es necesario comprender los siguientes temas también:

- Provisionamiento automático
- Self service y self healing
- DevSecOps principles

## Shift-Left Principle

Los  equipos se concentran en la calidad, trabajar en la anticipación de un problema en vez de detección y pruebas. 

Esto viene de la cultura DevOps

- Encontrar y prevenir problemas tempranos durante el ciclo de desarrollo
- Empezar con pruebas, seguridad y rendimiento primero que todo
- Calidad mas que todo

Mover todo primero a la izquierda (shift left) para trabajar lo mas pronto posible.

### Shift-Left Security

Integrar herramientas de DevSecOps en las pipelines ademas de los IDE de los desarrolladores para tener una mayor visibilidad.

- Involucrar expertos en la seguridad en los fases tempranas del ciclo
- Usar herramientas de seguridad
- Integrar herramientas de seguridad dentro del IDE del desarrollador

### Shift-Left Performance

Mover las pruebas de rendimiento, nos permite a los desarrolladores ejecutar dichas pruebas antes en nuestro ciclo de desarrollo, esto no solo se enfoca en latencias y así, también la calidad del codigo (el inicio de todo el problema)

- Implementación de pruebas de rendimiento con/paralelo al ciclo de desarrollo.
- Incluir las pruebas de rendimiento dentro de nuestro set de pruebas
- Crear atributos de rendimiento
- Integración de DevSecOps