---
tags:
  - arquitectura-de-software
  - modulos
  - master
---
Necesitamos describir como funciona en la unidad mas pequeña nuestro sistema, esta descripción es la **vista de módulos**

>[!NOTE]
>El hecho de poder repartir nuestro sistema en unidades manejables es una gran pieza en nuestro planteamiento

Como minimo nos muestra las relaciones de nuestro codigo fuente, que cosas se ven afectadas entre si y nos refleja atributos como ***modificabilidad***, ***portabilidad*** y ***reuso***

>[!IMPORTANT]
>Un arquitecto es aquel que puede ser profeta, si no es capaz de verlo, no es arquitecto

![[Pasted image 20240826224846.png]]

## Elementos

El elemento a manejar se llama ***modulo***, este refiere a muchas posibles estructuras de software como lo pueden ser unidades de programacion (Programas en C, Clases en Java o C#, Unidades Delphi, procesos almacenados de PL/SQL, paquetes de Java o C# namespaces)

>[!NOTE]
>Un moduloe es una implementacion que sigue una(s) ***responsabilidad***

## Relaciones
### Es parte de 
En este tipo de relacion, contamos con submodulos dentro de nuestros modulos, podemos verlo como una agreacion

### Depende de
En este caso marcamos una dependencia de un modulo con otro.

### Es un
Se refiere al contexto de generalizar/especializar entre un modulo hijo y un modulo padre.

## Propiedades
- Nombre: El nombre del modulo y su función, aunque también puede decirnos su composición "A.B.C", se refiere al módulo C que es un submódulo de B, donde este ultimo es un submódulo de A
- Responsabilidad: Es una afirmación sobre que debe hacer
- Visibilidad de interfaces: Deben exponer como acceder a ellas

 ![[Pasted image 20240826225643.png]]

- Informacion de implementacion
- Relacion con unidad de codigo fuente: Archivos que constituyen el modulo.
- Informacion sobre pruebas: Debe contener su plan de pruebas, casos de pruebas y datos de prueba
- Manejo de informacion: Fechas y costo
- Restricciones: Informacion privada del modulo

## Casos de uso
- Construccion: Tener una idea de como lucira el codigo fuente
- Analisis: El análisis incluye dos técnicas clave: *la trazabilidad de requisitos* y el *análisis de impacto*. La trazabilidad asegura que los módulos del sistema cumplan con los requisitos funcionales, mientras que el análisis de impacto predice el efecto de modificar el sistema. Documentar secuencias entre módulos muestra cómo se cumplen los requisitos, y las dependencias entre módulos son esenciales para un análisis de impacto efectivo. Para ello, el diseño debe ser completo y la información de dependencias precisa.
 - Comunicación: Una vista de módulos nos permite explicar el sistema a alguien no tan familiarizado con el sistema.

## DSM (Dependency Structure Matrix)
Es una tabla que nos permite ver los módulos como las columnas y las cabeceras y dependencias como celdas. Es una matriz cuadrada ($n\times n$)
donde el elemento $M_{ij}$ no es cero si hay dependencia entre el modulo I y el modulo J.

## ERD (Entity Relationship Diagram)
Este es mas para las bases de datos, y es mas para modelado de datos.

## Implementaciones

[[Layered Style]]
