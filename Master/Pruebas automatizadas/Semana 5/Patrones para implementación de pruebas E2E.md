---
tags:
  - QA
  - e2e
  - PruebasAutomaticas
  - Automatizacion
  - master
---
## Patron Given-When-Then
Este patron lo que busca es un paradigma para orientar nuestras pruebas, es decir, como deriamos orientras nuestros escenarios de prueba.

## PageObject
Este nace detras de la problematica donde dependiamos antes de:
- El HTML directo de la pagina web
- Posiciones absolutas de la pagina web

Esto limitaba mucho la creacion, porque: 
- Que tal si la UI cambia
- Que tal si cambia la posicion
- Que pasa si el mismo selector se usa en varias pruebas

Basicamente lo que buscamos encapsular la manipulacion y localizacion de los componentes de la interfaz.
