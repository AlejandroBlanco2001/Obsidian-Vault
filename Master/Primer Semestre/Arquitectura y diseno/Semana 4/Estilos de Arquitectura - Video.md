---
tags:
  - estilo-arquitectonico
  - master
  - arquitectura-de-software
---
Existen 3 estilos 
- Modulo
- Componente C&C (Componentes y Conectores)
- Asignación

# Módulos
- ***Propósitos*** Hacer evidente unidades de implementación que proveen conjuntos de responsabilidades
- ***Elementos*** Clases, Conjunto de clases y Capas
- ***Relaciones*** Son de es-parte-de, depende-de y es-un
- ***Utilidad*** Construccion del producto, analisis del modulo o del sistema y comunicar el funcionamien del sistema usualmente una aproximacion de lo mas general a lo especificio

***Ejemplos***
- Descomposicion
- Uso
- Generalizacion
- Capas
- Aspectos
- Modelado de datos

## Descomposicion
- ***Propósito*** Ir de lo general a lo especifico, mostrando dentro de los módulos todos los submódulos existentes
- ***Elementos*** Módulos 

![[Pasted image 20240831011508.png]]

## Capas

> Ver mas en [[Layered Style]]

- ***Propósito*** Agrupas unidades de codigo en criterios semánticos, mostrando jerárquicas y se modela de manera vertical. Una capa solo tiene acceso a su inferior directo
- ***Elementos*** Capas

![[Pasted image 20240831011624.png]]

# Componente-Conector
- ***Propósito*** Expresar decisiones de comportamiento del sistema durante ejecución.
- ***Elementos*** Componentes y conectores
- ***Relaciones*** Exposición y uso de interfaces, y envió y recepción de mensajes
- ***Útil*** Mostrar como funciona el sistema en tiempo de ejecución, entender las principales decisiones sobre el flujo de control y entender decisiones de diseño para razonar sobre atributos de calidad.

***Ejemplos***
- Orientados a Flujos
	- Pipe y Filter
- Llamada-Retorno
	- [[Client-Server Style]]
	- [[Peer-to-Peer style]]
	- [[Service-Oriented Architecture Style]]
- Orientados a eventos
	- Publicador-Subscribtor
- Orientado a depositos
	- Datos compartidos

## N niveles (N-Tier)
- ***Propósito*** Los niveles expresan las decisiones de diseno en las que se agrupan de forma logica conjuntso de componentes que tiene una relacion entre si. La agrupacion por nievels se puede dar por varios criterios 
- La comunicación entre los diferentes niveles se puede reglamentar de format que algunos componentes, solo puede comunicarse con otros componentes.
- Las restricciones también pueden aplicar a rango del nivel
- ***Elementos*** Nivel, Componente y Conector

![[Pasted image 20240831012251.png]]

# Asignación

- ***Propósito*** Expresar decisiones de asignación de elementos de software con elementos del ambiente.
- ***Elementos*** Nodos de ejecución y unidades de software
- ***Relación*** Asignado A
- ***Útil*** Explicar decisiones de diseño relacionado con operaciones del sistema, especificar decisiones de operación en ambientes de desarrollo y producción, determinar responsabilidades a elementos de arquitectura y razonar sobre la disponibilidad y escalabilidad presente 

***Ejemplos***
- Despliegue
- Instalación
- Trabajo 

## Despliegue

- ***Propósito*** Configuración de hardware para crear los entornos de pruebas y producción. Asociando hardware y componentes
- ***Elementos*** Nodos de ejecución, unidad de software y el protocolo

![[Pasted image 20240831012639.png]]

