Tags #arquitectura-de-software #diseno-uml #estilo-arquitectonico #modificacion 

La facilidad de modificacion es el atributo que indica que tan facil es modificar nuestro software, hardware o infraestructura.

Los remplazos pueden ser parciales o totales, y puede nacer de:
- Errores que nacen
- Actualizacion de librerias
- Optimizacion

Una de las preguntas que nos debemos hacer es:

- Que puedo cambiar 
- Probabilidad del cambio
- Cuando ocurrira el cambio (Fase inicial, Desplegue, Produccion)
- Quien hace el cambio
- Costo del cambio (Esfuerzo requerido)

Haciendo uso de los escenarios de calidad podemos definir nuestros requisitios.

![[Pasted image 20240912183132.png]]

# Estilos de arquitectura

Algunos de los requisitios es:

- Manejar la mayor cantidad de independencia de cada componente (bajo acoplamiento)

Estilos que favorecen:
- Familia Modulos: Estilo poro Capap
- Familia C&C: Estilo Publicador-Subscritpor

## Por capas 

- Desacoplar las unidades lo mayor posible 
- El uso es descendente, es decir la capa n, solo puede usar n+1.
- El modelo MVC es un ejemplo de esto
	Vista -> Controlador -> Modelo -> BD

## Publicador subscriptor

- Se realiza la comunicacion por el medio de mensajes asincronos 
- Contamos con:
	- Productores
	- Subscriptores
	- Sistema de Mensajeria
- Ningun Productor conoce a su Subscriptor