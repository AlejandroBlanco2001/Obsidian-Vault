Tags #arquitectura-de-software #conversatorio

## Que caracteriza a un buen arquitecto?

- Un arquitecto debe ver un conjunto, del conjunto a las partes. Siempre debemos buscar armonia, ayuda a una comunidad y resuelve un problema al negocio
- Debe poder ser explicado de manera sencilla
- No es solo saber conceptualizar (teoria), tambien debes ser practico, debes asegurarte que en todas las fases se cumplan de manera correcta, es decir, debe abarcar todas las dimensiones en algun nivel
- El titulo no debe ser un necesario, recuerda que siempre ***debemos entregar con el minimo esfuerzo, el mayor valor***
- No es solo dar un buen plan, sino ver como avanza, asegurar que la idea permanezca

>[!IMPORTANT]
>Siempre es preferible un codigo sencillo que avance bien, que un codigo largo y complejo que evolucione mal

- Un disenador de software o un arquitecto son indistintos.

## Tiempo de respuesta y escalabidad, como lo debemos trabajar?

- Las mejoras tempranas y la optmizacion prematura, es el origen de todos los males.
- Iterar es la clave, haz algo simple que vaya evolucionando
- Entender algo es complejo, si algo es complejo toma tiempo entender, y cuanto mas complejo mas tiempo nos toma y eso es lo que notamos
- Debemos priorizar ciertos ***procesos claves***, no todos
- Como se siente el usuario con respecto a los procesos (UI/UX)

>[!IMPORTANT]
>Un sistema confiable, no es aquel que no falle, es aquel que yo se que pasa cuando algo falla 

- No todo el proceso debe ser rapido y escalable, solo lo importante. Identificar el punto de fallo critico
- El arquitecto usualmente, no sabe como solucionar los problemas del dia a dia (no debe saber en realidad)

## Como disenar un software modificable y mantenible

- En la industria, esto debe ser una meta, mas bien deberia ser una filosofia
- Software que no se puede modificar, es un software de legado, es un codigo muerto
- Hace mucho tiempo, las abstracciones era el puente para poder modificar un software sin tocar el software.
	- Una buena abstraccion es lo mas dificil de crear, y solo se puede adquirir esto a traves de la practica
	- Una forma de asegurar esto es las pruebas automaticas
	- Simplicidad y abstracciones deben estar balanceadas
- Aplicar todo lo que sabes del libro, no siempre es lo mejor
- Unas buenas abstracciones, no siempre es algo bueno en la practica, recuierda que el diseno no lo haras tu, hacerlo complejo es algo inncesario

>[!IMPORTANT]
>Menos abstracciones, es menos complejidad, menos ruido y mas mantenible, siempre y cuando tengas pruebas 

## Hay patrones para todo, cuando usarlos?

- Si vemos como ejemplo de Gaudi con la Sagrada Familia, este hizo uso de un patron de arquitectura sobre su estilo, pero antes de escogerlo, realizo muchas preguntas
	- Tengo los materiales
	- Tengo la gente
	- Cuento con la informacion necesaria para medir esto

>[!IMPORTANT]
>El patron siempre depende de un contexto, a quienes tengo, cuanta plata tengo, maneras en que puedo medir.

- Un buen arquitecto ve que abstracciones puedo usar y cuales puedo tener en este momento, recordemos que esto es un juicio subjetivo
- SIempre debemos identificar los patrones claves para las operaciones claves, y ver como evolucionan, debemos poder medirlo
- Los patrones son sabores, y son subjetivos a las experiencias.
- Analogia de la cocina, tu puedes modificar la receta segun tu contexto
- Un patron no debe ser limpio siempre.
- Recuerda, los patrones son un principio de Paretto, un 80% de los resultados se consigue con un 20% de los patrones. No debes usarlos todos y probablemente jamas los uses
- 