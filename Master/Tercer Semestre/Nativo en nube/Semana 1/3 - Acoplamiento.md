---
tags:
  - cloud
  - master
  - patrones-de-diseno
---
>[!INFO]
> Para mayor contexto, leer [[GRASP - Lectura]]

La medida de *cuanto un componente de software esta conectado* (tiene conocimiento) de otros componentes. Cuanto mas sea el conocimiento de un sobre otro, esto se llama *alto acoplamiento*, lo que puede generar algo muy perjudicial para nuestro sistema.
- Dificultad al entender el sistema
- Cambiar el sistema es mas complejo
- El impacto del cambio es algo mas difícil de estimar

> [!INFO]
> Otra forma de ver el acoplamiento es, se encarga de determinar el efecto que tendrá un cambio de un elemento de software sobre otro elemento.

Debemos considerar que a veces el acoplamiento *debe existir*, pero siempre debemos tratarlo de tenerlo *en la menor medida posible*

> [!IMPORTANT]
> Siempre queremos un bajo acoplamiento y una alta cohesion
