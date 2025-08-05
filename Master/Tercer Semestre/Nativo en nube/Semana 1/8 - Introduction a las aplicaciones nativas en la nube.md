---
tags:
  - master
  - cloud
  - arquitectura-de-software
---
Cuando buscamos desplegar nuestra sistema, tenemos las siguientes alternativas
![[Pasted image 20250804233402.png]]

Donde a medida de que subamos en la capa, tendremos menor control, pero mayor facilidades. Para poder ser mas rápidos que la competencia siempre debemos agilizar nuestro ciclo de desarrollo de software.

Las aplicaciones nativas en la nube logran esto, donde su definición es la siguiente según  la Cloud Native Computing Foundation ([[9 - CNFC]])

> Las aplicaciones nativas en la nube son aplicaciones construidas como un conjunto de servicios independientes, bajamente acoplados, y orientados al negocio, que pueden ser ejecutados en ambientes dinámicos caracterizados por ser ***escalables***, ***resilientes***, ***gestionables*** y ***observables***.

## Características
- Escalabilidad: Tiene la capacidad de responder a cambios en la carga que este reciba sin degradarse 
- Resiliente: Pueden detectar y responder a una falla en el sistema sin afectar a todo el sistema.
- Observabilidad: Tienen la capacidad de comunicar y comprender su propio estado sin necesidad de desplegar codigo
- Orientado a microservicios = independientes y bajamente acoplados

## Buenas practicas
- Este se orienta en Domain Driven Design (DDD), el cual nos permite abstraer la complejidad de las necesidades de negocio a servicios bajamente acoplados.
- Usamos los principios Twelve Factor Application
	- Gestion del codigo base
	- Aislamiento de las dependencias
	- Configuración separada del codigo
	- Uso de servicios de respaldo
	- Fase de construcción, empaquetamiento y ejecución separadas
	- Ejecución de procesos sin estado
	- Asignacion de puertos para cada aplicacion que se ejecuta
	- Manejar concurrencia escalando en copias de la apliacacion
	- Facilidad de deshechar y recuperar recursos
	- Paridad en desarrollo y produccion
	- Manejar los logs como un flujo de eventos constante,
- Containerization
- Automatización
- Orquestación
- Gestion dinámica de recursos
- Microservicios