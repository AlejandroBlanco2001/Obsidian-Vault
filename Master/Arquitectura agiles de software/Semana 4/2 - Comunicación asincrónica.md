Tags #microservicios #colas-mensajes #comunicacion-asincronica

Un microservicio puede interactuar puede recibir:
- eventos
- consultas 
- comandos

Estos a su vez, pueden generar eventos que otros microservicios escuchan y procesan, este esquema es llamado ***coreografía basada en mensajes***

![[Pasted image 20250215190715.png]]

Al no conocerse entre ellos, hay un ***acoplamiento débil***

![[Pasted image 20250215190935.png]]

## Eventos como mecanismo de notificación
En lugar de realizar consultas a otro servicio, se replican los datos y se realizara la consulta localmente.

- Aislamiento y autonomía
	- Mantener copias locales de los datos el servicio es autonomo.
- Acceso a datos rápido
	- Consultar información local es mas rápido que a través de consultas por la red
- Trabajo offline
	- Si se presentan fallas en la red , el servicio puede continuar operando fuera de linea y luego sincronizarse al estar en linea nuevamente
- Control centralizado
	- El servicio es autónomo y tiene control total de los datos, aunque se trata de una copia 