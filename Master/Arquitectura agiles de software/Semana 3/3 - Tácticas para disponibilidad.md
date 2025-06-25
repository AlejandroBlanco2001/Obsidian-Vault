---
tags:
  - tacticas-arquitectura
  - disponibilidad
  - microservicios
  - master
---
Estos patrones que vamos a comentar solo aplica para microservicios que se van a comunicar de manera síncrona, muy probablemente esto no aplique para los que se comuniquen de otra manera.

## Monitor
Dentro de las tácticas de detección de fallas, se encuentra esta táctica.

Hay un componente que se encarga de verificar el estado de salud de estos componentes.

Este monitor inicia el chequeo (ping/echo) o el componente monitoreado puede informar periódicamente que esta bien (heart-beat)

![[Pasted image 20250203214518.png]]

## Votación
Dentro de las tácticas de detección de fallas, se encuentra esta táctica.

Contaremos con una cantidad impar de servicios, donde ejecutan lo mismo en paralelo, cuando comando es ejecutado, se valida con este componente Validador, las discrepancias (Idealmente, deben ser las respuestas siempre igual, en caso de no serlo, hay un problema)

![[Pasted image 20250203214911.png]]

## Retiro del servicio
Dentro de las tácticas de detección de fallas, se encuentra esta táctica.

Si un servicio es una fuente de fallas, procederá a ser removido del flujo normal. esta puede ser combinada con cualquiera de las otras tácticas expuestas.

- Si el monitor detecta una falla, podemos bajar el servicio e intentar repararlo.
- Si el votante detecta una discrepancia, podemos bajar el servicio e intentar repararlo.
