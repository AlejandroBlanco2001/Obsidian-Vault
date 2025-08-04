---
tags:
  - master
  - cloud
  - patrones-de-diseno
---
> [!INFO]
> Para mayor contexto, leer [[GRASP - Lectura]]

Podemos usar un objeto como una navaja suiza para entender este concepto, donde esta *tiene muchas funciones* (responsabilidades), y esta sirve para muchas cosas.

Pero, si lo pensamos, esta no es *cohesiva*, debido a que cuenta con *demasiadas funciones* y que *no estan relacionadas* entre si, es decir, no podemos contestar la pregunta: Que hace la navaja?

>[!IMPORTANT]
> La pregunta de, ***Que hace?*** es el principal medidor de la cohesion

Podemos definir la cohesion como una medida que indica *cuan relacionadas estan las responsabilidades* de un elemento de software.

- Alta cohesion: Mas relacionadas estan las responsabilidades -> Mas facil de entender