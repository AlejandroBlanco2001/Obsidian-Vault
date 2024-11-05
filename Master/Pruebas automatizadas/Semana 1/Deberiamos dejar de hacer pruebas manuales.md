Tags #QA 

Siempre necesitamos tener un balance entre las pruebas manuales y automaticas, ademas debemos tener en cuenta nuestros recursos como:

- Horas por persona disponibles para hacer QA
- Horas de infraestructura para la ejecuccion de pruebas
- Recursos monerios para adquirir servicios externos 

>[!NOTE]
>Antes de hacer pruebas automaticas, debemos saber hacer pruebas manuales

Recordemos que estos procesos manuales se hacen en un escenario de ***Ambiente de pruebas*** que deben ser muy parecidos al escenario de produccion

>[!IMPORTANT]
>Tambien existe el caso de que se pruebe en produccion, debido al coste que conllevaba hacer un escenario de prueba (esfuerzo/monetario), de igual manera existen casos donde es mas probable que pase en produccion que un ambiente, como el caso de ***Netflix con las pruebas de caos o ingenieria de caos***

## Aspectos que impactan la calidad del proceso de pruebas

1. Replicabilidad, deben estar bien indicados los pasos para reproducrilos, debemos tener un ***oraculo de una prueba***
2. Conocimiento que tenga el ejecutor de la prueba sobre el sistema
3. Velocidad de la ejecuccion
4. Falta de comunicacion
5. Fragilidad de los casos de prueba (Dependemos de las particularidades)

Un oraculo de prueba se refiere a:

> Criterios o resultados esperados que definen cuando una prueba se declara como exitosa o fallida

## Pruebas exploratorias 

Cuando se tiene una falta de conocimiento sobre el sistema, es necesario hacer ***pruebas exploratorias***

1. Crear o actualizar inventarios de pruebas
2. Detectar defectos de forma manual
3. Generar documentacion de diseno y usuarios