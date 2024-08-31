
Existen 3 estilos 

- Modulo
- Componente C&C (Componentes y Conectores)
- Asignacion

# Modulos

***Propositos*** Hacer evidente unidades de implementacion que proveen conjuntos de responsabilidades


***Elementos*** Clases, Conjunto de clases y Capas

***Relaciones*** Son de es-parte-de, depende-de y es-un

***Utilidad*** Construccion del producto, analisis del modulo o del sistema y comunicar el funcionamien del sistema usualmente una aproximacion de lo mas general a lo especificio

***Ejemplos***

- Descomposicion
- Uso
- Generalizacion
- Capas
- Aspectos
- Modelado de datos

## Descomposicion

***Proposito*** Ir de lo general a lo especifico, mostrando dentro de los modulos todos los submodulos existentes

***Elementos*** Modulos 

![[Pasted image 20240831011508.png]]

## Capas

Ver mas en [[Layered Style]]

***Proposito*** Agrupas unidades de codigo en criterios semanticos, mostrando jerarquicas y se modela de manera vertical. Una capa solo tiene acceso a su inferior directo

***Elementos*** Capas

![[Pasted image 20240831011624.png]]

# Componente-Conector

***Proposito*** Expresar decisiones de comportamiento del sistema durante ejecuccion.

***Elementos*** Compoentes y conectores

***Relaciones*** Exposicion y uso de interfaces, y envio y recepcion de mensajes

***Utili*** Mostrar como funciona el sistema en tiempo de ejeccucion, entender las principales decisiones sobre el flujo de control y entender decisiones de diseno para razonar sobre atributos de calidad.

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

***Proposito*** Los niveles expresan las decisiones de diseno en las que se agrupan de forma logica conjuntso de componentes que tinen una relacion entre si. La agrupacion por nievels se puede dar por varios criterios 

La comunicacion entre los diferentes niveles se puede reglamentar de fofrma que algunos componentes, solo puede comunicarse con otros componentes.

Las restricciones tambien pueden aplicar a rango del nivel

***Elementos*** Nivel, Componente y Conector

![[Pasted image 20240831012251.png]]

# Asignacion

***Proposito*** Expresar decisiones de asignacion de elemetnos de software con elementos del ambiente.

***Elementos*** Nodos de ejecuccion y unidade de software

***Relacion*** Asignado A

***Util*** Explicar decisiones de diseno relacionado con operaciones del sistema, especificar decisiones de operacion en ambientes de desarrolo y produccion, determinar responsabilidades a elementos de arquitectura y razonar sobre la disponibilidad y escalabilida presente 

***Ejemplos***
- Despliegue
- Instalacion
- Trabajo 

## Despliegue

***Proposito*** Configuracion de hardware para crear los entornos de pruebas y produccion. Asociando hardware y componentes

***Elementos*** Nodos de ejecuccion, unidad de software y el protoclo

![[Pasted image 20240831012639.png]]

