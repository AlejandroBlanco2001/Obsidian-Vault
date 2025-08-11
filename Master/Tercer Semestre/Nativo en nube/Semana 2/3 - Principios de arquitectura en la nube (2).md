---
tags:
  - master
  - cloud
---
> [!INFO]
> Es una extension de [[2 - Principios de arquitectura en la nube]]

# MBDP
Tenemos conceptos de negocio, y haciendo uso de DDD para convertirlo en servicios de nuestro sistema.

# API First & Consumer First Principles
Todos nuestros microservicios se comunicaran por medio de sus API, por ende, también debemos tener en cuenta sus consumidores 

# Polyglot Persistence Principle
Debemos usar la herramienta indicada de almacenamiento de datos para nuestros tipos de datos, hay que *pensar en nuestros datos, no en nuestro facilidad de desarrollo*

# Single Source of Truth Principle
Debemos contar una única fuente de verdad de los datos agregados de todas nuestras otras bases de datos

![[Pasted image 20250811164626.png]]

# Decentralize Everything Principle
Queremos que nuestros equipos sean *autónomos, autosuficientes e independientes*, donde podemos usar las siguientes herramientas

- DDD
- Contenedores y orquestadores
- Sin burocracia
- Sin centralizar DevOps
- Poliglota
- Auditoria constante

# Culture of Automation Principle
Cuando empecemos a desarrollar, desde el día 0 debemos construir las herramientas que nos automaticen todo el trabajo