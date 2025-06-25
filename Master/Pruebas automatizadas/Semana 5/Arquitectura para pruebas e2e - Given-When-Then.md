---
tags:
  - QA
  - e2e
  - Automatizacion
  - master
---
Esta metodología de pruebas nace bajo el umbral de *BDD* (Behavioral Driven Development), donde planteamos nuestros escenarios de prueba de manera:

- ***Dada*** una situacion previa a nuestra prueba, es decir, el estado del mundo previo a la prueba (***Given***)
- *Cuando* suceda lo que queremos probar (***When***)
- Finalmente *entonces*, describiremos los cambios que esparabamos (***Then***)

Esto es un ejemplo realizado con el framework Cucumber

```
Feature: User trades stocks
  Scenario: User requests a sell before close of trading
    Given I have 100 shares of MSFT stock
       And I have 150 shares of APPL stock
       And the time is before close of trading

    When I ask to sell 20 shares of MSFT stock
     
     Then I should have 80 shares of MSFT stock
      And I should have 150 shares of APPL stock
      And a sell order for 20 shares of MSFT stock should have been executed
```

