Existen dos grandes categorias que expresan los UML:

- Estructura
	- Clase
	- Paquetes
	- Componentes
	- Objetos
	- Despliegue
- Comportamiento
	- Secuencia
	- Actividades
	- Interaccion
	- Casos Uso
	- Comunicacion
	- Estado

En este curso usaremos los siguientes: ***Clase, Paquetes, Componentes, Despliegue y Comunicacion***

Habra ocasiones donde usaremos un sistema distinto sistema de notacion, por ejemplo, para el caso de los diagramas de contexto, busca identificar sistemas externos, actores relevanates y todo funciona como una caja negra

![[Pasted image 20240824152217.png]]

## Diagrama de componentes

![[Pasted image 20240824152501.png]]

Facilitan agrupar de forma logica que exponen una interfaz a otro componente, nos permite ver el tipo de mecanismo de comunicacion que usaran

![[Pasted image 20240824152627.png]]

RPC - Bloquea el recurso
![[Pasted image 20240824152723.png]]

No bloquea el recurso, sistema de cola

![[Pasted image 20240824152755.png]]

Ejemplo completo

![[Pasted image 20240824152838.png]]

## Modelo de despliegue

Ilustra como se comunican y donde estaran alojados nuestros componentes a nivel de unidad de trabajo

![[Pasted image 20240824153230.png]]
## Modelo de concurrencia 

Ilusra como se comunican a nivel de procesos de ejecuccion

![[Pasted image 20240824153410.png]]

## Modelo de paquetes

Se encarga de mostrar nuestra organizacion del codigo fuente para ilustrar su indepedencia y como se pueden dividir 

![[Pasted image 20240824153542.png]]