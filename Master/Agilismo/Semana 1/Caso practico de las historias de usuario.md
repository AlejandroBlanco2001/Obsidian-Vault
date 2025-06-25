---
tags:
  - Agilismo
  - historias-de-usuario
  - master
---
**Identificación de usuarios**
- Independientes
- Interesados

**Identificación de historias de usuario**
- "Al inscribir sus servicios deben dar la siguiente información"
- "Consultar el listado de independientes registrados"
- "El listado de independiente se debe poder filter por los diferentes servicios que se registran en el portal"
- "Consultar los detales del independiente haciendo click sobre su tarjeta"
- "Los independientes que se han inscrito pueden hacer login en el sistema"
- "Una vez identificados pueden consultar y modificar la informacion de su registro"
- "Los usuarios interesados en contratar independientes pueden dejar un comentario en la informacion del independiente"\

**Revision listado de historias**
- Forma
	- Como, Qusiera, Para
- Completo
	- Funcionalidades solicitadas estan presentes
- Consistentes
	- No hay contradicciones
- Independientes
	- No dependen una de la otra

Para una segunda revisión, **se verifica** 
- Completo
	- Cumple todas las funcionalidades
- Consistente
	- No presenta contradicciones
- Negociable
	- Se puede categorizar en prioridad o agregado
- Valiosa
	- Genera valor
- Estimable
	- Se puede hacer una estimacion
- Pequeña
	- No requiere mas de dos dias
- Comprobable
	- Los criterios y descripcion, permiten ser comprabadas


### Ejemplo

|                         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Identificador           | HU007                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Nombre                  | Comentar tarjeta                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Descripción             | Como interesado quiero ingresar un comentario sobre la tarjeta de servicio del independiente utilizando un correo electrónico propio válido, para dejar mis opiniones sobre dicho independiente visibles a los demás usuarios interesados.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Criterios de aceptación | - Cuando se guarda el comentario se debe validar que dicho comentario no se encuentre vacío o solamente con espacios. En caso de que no pase esta validación se muestra un mensaje indicando el error, no debe permitir el guardado del comentario, y el usuario queda en la misma vista.<br>    <br>- Cuando se abre la tarjeta del servicio, el espacio para ingresar los comentarios debe aparecer justo debajo de la información del servicio.<br>    <br>- Cuando ya se ha elegido adicionar un comentario en la página, no debe ser posible adicionar otro comentario.<br>    <br>- Cuando ya se ha adicionado un comentario en la página, no debe ser posible editarlo.<br>    <br>- El campo del correo electrónico no puede estar vacío y debe permitir un correo electrónico válido. En caso de que no pase esta validación se debe mostrar un mensaje indicando el error, no debe permitir el guardado del comentario y el usuario queda en la misma vista.<br>    <br>- Al guardar la información, el nuevo comentario aparecerá al final de la vista. |
| Mockup                  | (La imagen se copia debajo de la tabla para verla con mejor tamaño)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
![[Pasted image 20240811034513.png]]