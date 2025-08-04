---
tags:
  - cloud
  - master
  - DevOps
---
> [!INFO]
> Para mayor contexto, leer de nuevo [[Lectura - Maquina Virtuales]]

Partamos de una ***infraestructura como servicio*** (IaaS), donde tomamos las ventajas de la ***virtualización***, esto nos permite tener sobre UNA infraestructura correr MULTIPLES maquinas virtuales

> En este caso, recordemos que las capas se denominan de la siguiente manera:
> 1. Aplicaciones
> 2. Datos
> 3. E ntornos de ejecución
> 4. Middleware
> 5. S.O
> 6. Virtualización
> 7. Servidores
> 8. Almacenamiento
> 9. Red
> Donde el proveedor se encarga del 9 al 6, y nosotros del 5 al 1

Recordemos que nuestras maquinas virtuales son finitas y limitadas, por ende, podemos realizar:
- Escalamiento horizontal: Mas maquinas, usualmente mas barato
- Escalamiento vertical: Agregar mas recursos, usualmente mas caro

Tambien hay que tener en cuenta que los contenedores tienen también problemas como cualquier modelo de despliegue, pero que es un contenedor:

> [!INFO]
> Paquete de software **ejecutable, ligero y portable** que contiene todas las dependencias, archivos y elementos necesarios para la ejecución de una aplicacion.

Muy importante es recordar que contenedores y maquinas virtuales no son lo mismo, son conceptos relacionados pero no iguales
- Contenedores
	- Uso del kernel del sistema operativo anfitrión para todos los contenedores y sus aplicaciones
- Maquinas virtuales
	- Sistema operativos autónomos que gestionan su propio kernel

![[Pasted image 20250803175158.png]]

Recordemos que los contenedores al ser aislados, tenemos capacidad de modificarlos de manera autónoma.