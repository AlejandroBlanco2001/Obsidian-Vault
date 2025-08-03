---
tags:
  - QA
  - master
---
# Niveles
Granularidad del sistema a probar, es decir, que se esta probando

- Unitarios - De forma aislada (funciones del codigo)
	- CodeShip
	- Jenkins
	- GitHub Actions
- Integracion -  Busca validar varios componentes integrados (Componentes del codigo)
- Sistema - Busca validar el sistema como un todo, debemos tener todo listo
- Aceptacion - Busca validar sobre el sistema en escenarios mas realisticos, es decir, desde el punto de vista del cliente

# Tipos
Cual es el proposito de la prueba

- Segun el requerimiento
	- Funcionales
	- No Funcionales

- Salidas del sistema
	- Caja negra: Sin sabern nada de como esta implementando
	- Caja blanca: Sabiendo como esta implementado

- Segun los escenarios
	- Positivas: Escenarios esperados
	- Negativas: Escenarios no esperados

# Tecnicas
Como se ejecuta la prueba y como se generan los venetos en la prueba