---
tags:
  - restricciones-objetivos-negocio
  - arquitectura-de-software
  - master
---
**Principios de diseno**
- Disenar para las personas
- Preservar la ambiguedad
- Disenar es redisenar
- Hacer tangible lo intangible
## Disenar para las personas
Recuerda que tu diseño es para que los DEMAS lo vean, opinen y ejecuten. De igual manera, tu diseñas con personas. Tu intención debe ser comunicar.

## Preservar la ambiguedad
No todo debe quedar plasmados en la primera etapa (o en las fases tempranas), recuerda el ***diseño es de alto nivel***. Si algo no es claro, deja esa ambigüedad, posiblemente cuando este mas claro se refina y se hace.

## Disenar es redisenar
Todo diseno es una **evolucion**, hay **iterarlo** y poco a poco crece hasta que la incertidumbre es manejable

## Tangible lo intangible
Todas nuestras ideas deben poder ser expresadas en nuestros diagramas

## Aplicación de esto

### Definición de entradas
- **Objetivos de negocio**
	- **Deseos del cliente**
	- Deben ser claros
	- Debemos saber el tiempo, su viabilidad y su expectativa
- **Restricciones**
	- **Son decisiones que se imponen para acotar el problema y la solucion**
	- Las pudimos tomar nosotros
	- No podemos cambiarlas
	- Nos ayudan a acotar las cosas
	- Nos eliminan opciones
	- Hay de tecnologia y negocio
- **Requisitios funcionales**
	- **Cosas que hace**
	- Casos de uso o historias de usuario
	- Manejamos generalidad, simplemente que hace, no como se hace
- **Requisitios de calidad**
	- **Son requerimientos no funcionales**
	- Estos pueden ser ambiguos
		- El sistema debe ser rapido
		- El sistema debe ser lo mas rapido posible
	- Siempre debemos reducir esta ambigüedad


## Caso FotoAlpes

| *Objetivos del negocio*                                                     |                                                                                                                   |
| --------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| *Descripcion del objetivo*                                                  | Se desea crear una nueva linea de negocio que se llamara "Contenido Digital"                                      |
| *Tiempo de cumplimiento*                                                    | 2 anos                                                                                                            |
| *Mejora esperada al negocio*                                                | Se esper que sus ingresos obtenidos por esta nueva linea de negocio sean del 40% del total de las ventas          |
| *Como considera que puede afectar la arquitectura del sistema este objtivo* | - Mejor tiempo de respuesta<br>- Mas usuarios operando simultaneamente<br>- Mayor disponibilidad de la plataforma |

| *Restricciones del negocio*                                                     |                                                                                                                                                                                                                             |
| ------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| *Descripción de la restricción*                                                 | El presupesto total para el desarrollo y puestaen produccion del marketplace es de 25,000 USD                                                                                                                               |
| *Usuario que expresa esta restriccion*                                          | Gerente General                                                                                                                                                                                                             |
| *Justificacion*                                                                 | La empresa obtuvo un solo credito para este proyecto                                                                                                                                                                        |
| *Como considera que puede afectar la arquitectura del sistema este restricción* | - Evitar licencias de ciertos productos<br>- Favorecer el diseno y desarrollo de funcionalidades que aporten ingresos pronto<br>- El producto a desarrollar debe poder ser puesto en producto de forma gradual y por modulo |

| *Restricciones del tecnologia*                                                  |                                                                                     |
| ------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| *Descripción de la restricción*                                                 | El director de tecnolgoia indico que el software se debe desarrollar en Python      |
| *Usuario que expresa esta restriccion*                                          | Director de tecnologia                                                              |
| *Justificación*                                                                 | Se ha hecho una inversion en capacitaciones en esta tecnologia y se debe aprovechar |
| *Como considera que puede afectar la arquitectura del sistema este restricción* | - Entender las capacidades de la tecnologia a utilizar y su desempeno en produccion |





