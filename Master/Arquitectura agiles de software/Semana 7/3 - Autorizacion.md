Tags #seguridad #tacticas-arquitectura #microservicios #arquitectura-de-software 

Si pensamos en la superficie de ataque de una aplicación monolítica en teoría solo hay un punto de entrada (en lo personal, diría que hay dos), pero esto es mas controlable, ya que solo la capa de presentación es lo que afecta al usuario.

Sin embargo, en un microservicios hay multiples entradas por cada microservicio, donde cada microservicio puede ser una superficie de ataque.

# Concentrar la superficie de ataque en un solo lugar
Para reducir el area de impacto de la misma, podríamos usar un ***API Gateway*** que se encarga de controlar la autenticación. Para complementarla, podemos usar:

- Basados en certificados
	- Los certificados favorecen la confidencialidad y la integridad de la información durante la transmisión de la información.
	- El certificado representa la llave publica del servicio
	- Necesitamos un tercero que nos valide ambas partes
		- Se llama una entidad certificadora, y no debe ser propia del desarrollo
- Basados en control de acceso
	- En este caso necesitamos un servicio autenticador basados en quien hace la petición
		- Este se encarga de brindarnos un token de acceso con las operaciones que tiene permitidas hacer.
	- Encabezado + Contenido + Firma = JWT