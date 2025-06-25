---
tags:
  - QA
  - master
---
# APIs de automatización
Usando un lenguaje de programación o la API, podemos generar una serie de instrucciones para ejecutar como lo son:

- JUnit
- WebDriver
- Espresso
- Robotium
- Appium
- Nightwatch
- Cypress

Beneficios :
- Fácil reproducción
- Sintaxis de alto nivel

Inconvenientes;
- Curva de aprendizaje
- Mantenimiento costoso

# Record & Replay
Usar alguna herramienta que permita grabar los escenarios y que la herramienta se encargue de traducir a codigo:

- Selenium
- Android Espresso Test Recorder
- XCode UI Test Recorder

Mismos beneficios que el caso anterior, además de que es No Code

Inconvenientes:
- Acoplados a pantallas (posición absoluta)
- Tiempo de espera preestablecidos

# Monkey Testing
Son pruebas aleatorias que generan eventos sin intervención humana, donde tenemos el Fuzz Testing (Datos aleatorios), y tenemos el Monkey Testing (Datos, eventos y transacciones aleatorias)

- UI/Application Exerciser Monkey
- OSS-Fuzz tool

Beneficios:
- Rápida ejecución
- Buenos para detectar casos raros

Inconvenientes:
- Alta tasa de eventos inválidos
- Bajo nivel de cobertura
- Falta de expresividad

# GUI Ripping
Herramientas que permiten hacer pruebas autónomos de reconocimiento en aplicaciones con GUI, básicamente son Monkeys inteligentes.

- Test*
- ripX

Beneficios:
- Cobertura de codigo
- Versátiles dependiendo de la heurística de exploración
- Se puede combinar con generación de datos de prueba

Desventajas:
- Mucho tiempo de ejecución

# Basadas en modelos
Haciendo uso de los modelos existentes en la aplicación, crear un multi-modelo que nos permita generar pruebas.

- Sapienz
- RIP

Beneficios:
- Diversidad de escenarios a generar

Desventajas
- Construcción y acoplamiento de la herramienta

# Basadas en IA
Haciendo uso de modelos, construimos con deep-learning y minado de datos, un modelo super inteligente basado en pruebas anteriores.