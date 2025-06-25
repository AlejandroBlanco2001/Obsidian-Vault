---
tags:
  - restricciones-objetivos-negocio
  - arquitectura-de-software
  - master
---
Para lograr una arquitectura debemos iterar sobre estas 3 fases:
1. Entendimiento del problema
2. Diseño
3. Experimentación

## Requerimiento
Reconocer los requisitos, entradas y salidas de las necesidades de nuestro cliente

>[!IMPORTANT]
> Constantemente estaremos en proceso de entender el problema, sin embargo, es necesario tener un ***conocimiento minimo*** para empezar.

Las entradas que **debemos identificar**:
- Objetivos del negocio
	- *Que es lo que motiva al cliente*
	- Por ejemplo: Incrementar ventas, cumplir una ley...
- Restricciones
	- *Que no debemos negociar*
		- **Tecnologico**  Seleccion de una tecnologia
		- **Negocio:** Fechas limites, presupuestos
- Requerimientos funcionales
	- *Que hace nuestro sistema*
	- Puede no estar claros desde un inicio, pero debemos identificar los necesarios 
- Requerimientos de calidad (o no funcionales)
	- *Asociados a los atributos de calidad*
		- Disponibilidad
		- Flexibilidad
		- Escalabilidad
		- Seguridad
	- Deben ser claros, sin ambiguidades y cuantificables
	- No se pueden tener todos los atributos de calidad, estos generan contienda

## Hipotesis
Una vez tengamos claras las entradas, podemos comencar el ciclo de diseno:
- Requisitios de calidad mas importantes
- Establecer estilos de arquitectura, en pro de los requisitos
- Tácticas de arquitectura

>[!IMPORTANT]
>Este proceso debe verse como una prueba y error, debemos ensayar varias alternativas para nuestra posible solucion

## Experimentar
Una vez tengamos un diseño aceptable, podemos comenzar a experimentar con el, con el fin de validar y rectificar.

>[!IMPORTANT]
>Este es un proceso continuo, vuelve y comienza una vez terminas

