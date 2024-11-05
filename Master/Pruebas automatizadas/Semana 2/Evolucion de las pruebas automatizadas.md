Tags #QA 

# APIs de automatizacion
Usando un lenguaje de programacion o la API, podemos generar una serie de instrucciones para ejecutar como lo son:

- JUnit
- WebDriver
- Espresso
- Robotium
- Appium
- Nightwatch
- Cypress

Beneficios :
- Facil reproduccion
- Sintaxis de alto nivel

Inconvenientes;
- Curva de aprendizaje
- Mantenimiento costoso

# Record & Replay
Usar alguna herramienta que permita grabar los escenarios y que la herramienta se encargue de traducir a codigo:

- Selenium
- Android Espresso Test Recorder
- XCode UI Test Recorder

Mismos beneficios que el caso anterior, ademas de que es No Code

Inconvenientes:
- Acoplados a pantallas (posicion absoluta)
- Tiempo de espera preestablecidos

# Monkey Testing
Son pruebas aleatorias que generan eventos sin intervencion humana, donde tenemos el Fuzz Testing (Datos aleatorios), y tenemos el Monkey Testing (Datos, eventos y transacciones aleatorias)

- UI/Application Exerciser Monkey
- OSS-Fuzz tool

Beneficios:
- Rapida ejecuccion
- Buenos para detectar casos raros

Inconvenientes:
- Alta tasa de eventos invalidos
- Bajo nivel de cobertura
- Falta de expresividad

# GUI Ripping
Herramientas que permiten hacer pruebas autonomas de reconocimiento en aplicaciones con GUI, basicamente son Monkeys inteligentes.

- Test*
- ripX

Beneficios:
- Cobertura de codigo
- Versatiles dependiendo de la heuristica de exploracion
- Se puede combinar con genracion de datos de prueba

Desventajas:
- Mucho tiempo de ejecuccion

# Basadas en modelos
Haciendo uso de los modelos existentes en la aplicacion, crear un multimodelo que nos permita generar pruebas.

- Sapienz
- RIP

Beneficios:
- Diversidad de escenarios a generar

Desventajas
- Construccion y acoplamiento de la herramienta

# Basadas en IA
Haciendo uso de modelos, construimos con deep-learning y minado de datos, un modelo super inteligente basado en pruebas anteriores.