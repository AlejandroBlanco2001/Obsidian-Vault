---
tags:
  - QA
  - PruebasAutomaticas
  - Automatizacion
  - master
---
Estas herramientas se encarga de ***destripar*** (Ripping) la interfaz grafica del usuario, en nuestro idioma, podemos llamarlo como ***exploracion sistemas de la GUI***

La diferencia entre un Ripper y un Monkey, es que el segundo al desconocer el estado de la pagina web y lanzar eventos de manera completamente. Mientras que el Ripper si conoce el estado de la pagina y tienen ***memoria***.

>[!NOTE]
>Basicamente el Ripper cuenta con memoria y puede usar una heuristica, como BFS o DFS

>[!NOTE]
>Fireabase Test Lab es una herramienta de Google para este caso
>

Estos pueden usar oraculos ***derivados*** o ***implicitos***.

Cuenta con los siguientes beneficios:

- Cobertura de codigo
- Versatiles dependiendo de la heuristica de exploracion
- Se puede combinar con generacion de datos de prueba.

Tiene con las siguientes desventajas como:

- Ejecuccion mas lenta comparada con los Monkeys

Otra diferencias pueden ser:

-  El modelo generado nos sirve para aplicarlos con pruebas manuales (Caminos del grafo)
- Ninguno de las herramientas tiene un modelo de uso y sus dependencias.


