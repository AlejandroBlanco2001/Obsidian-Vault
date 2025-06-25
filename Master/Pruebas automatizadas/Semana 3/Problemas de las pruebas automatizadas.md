---
tags:
  - QA
  - master
---
# Replicabilidad
La naturaleza del tipo de herramienta nos permite tener mucha replicabilidad (API, R&R), pero las menos determinísticas (Modelo y Monkeys)

# Flaky tests
Prueba que se comporta de forma no determinística, con cada ejecución esta varia.

>[!IMPORTANT]
>La intestibilidad pasa por suposiciones que se hacen duranta la prueba, los tiempos de espera son un ejemplo de que el test puede ser flaky

Siempre debe usarse alguna herramienta que ofrezca esperas nativas, y usar ID para evitar posiciones absolutas


