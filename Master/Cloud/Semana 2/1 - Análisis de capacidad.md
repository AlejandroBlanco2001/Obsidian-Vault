---
tags:
  - pruebas-capacidad
  - master
  - cloud
---
Cuando hablamos de prueba de rendimiento, estas nos permiten estudiar el desempeño de un sistema o de una aplicación cuando ante un escenario en particular como:

- Pruebas de carga
- Pruebas de estrés
- Pruebas de pico
- Pruebas de resistencia
- Pruebas de escalabilidad

***Las pruebas de rendimiento*** evalúan la capacidad de un servicio para responder a las entradas de un usuario en un momento determinado del tiempo y bajo unas condiciones específicas. Una prueba de rendimiento, es un experimento que permite medir y analizar unos parámetros de interés de un servicio o aplicación.

Una prueba de rendimiento debe cumplir:
- Deben estar alineadas a los requerimientos de negocio, y en particular ca la experiencia de los usuarios un servicio o aplicación
- Deben ser reproducibles. En las diferentes iteraciones de las pruebas los resultados deben ser estadísticamente consistentes bajo los mismos criterios de interés.
- Deben aportar resultados comprensibles y comparables.
- Deben realizarse sobre un entorno representativo del servicio o la aplicación en producción.

***Las pruebas de carga*** se realizan para evaluar el comportamiento del sistema, bajo una cantidad esperada de usuarios concurrentes, que realizan un número específico de transacciones durante un tiempo predefinido

***Las pruebas de estrés*** se realizan para determinar el comportamiento del sistema cuando se enfrenta a cargas extremas. Se realizan aumentando el número de usuarios concurrentes y el número de transacciones que ejecutan, sobrepasando la carga esperada. Permiten conocer cómo es el rendimiento del sistema, en caso de que la carga real supere la carga esperada, determinando cuales son los componentes y/o recursos que fallan primero y limitan el desempeño del sistema.

# Métricas necesarias
- **Capacidad de procesamiento (Throughput)**: La cantidad de trabajo realizado en un periodo definido de tiempo (Ejemplo: transacciones por minuto)
- **Tiempo de Respuesta (Response Time)**: tiempo que transcurre desde que el usuario envía una transacción hasta que recibe la respuesta completa.
- **Utilización (Utilization)**: porcentaje que representa qué tan ocupado está un recurso (CPU, Mem, I/O, etc) en un momento específico

