Tags: #microservicios #entrevistas #arquitectura-de-software #disponibilidad 

- La disponibilidad es uno de los atributos de calidad del software que mas se notan cuando falla (el sitio esta arriba o abajo)
	- Métricas asociadas a este: Cuanto dinero nos cuesta una falla de disponibilidad?
- Tener los micro-servicios nos permite mantener un mejor manejo de la carga, y si una parte del sistema falla, no afecta a todo el producto, solo a un camino del producto.
- Los microservicios fortalece:
	- Escalabilidad
	- Disponibilidad
- Los microservicios degrada:
	- Integración con los demás servicios 
	-  Problemas de comunicación y asociación del equipo.
	- Complejidad del sistema
		- Mantenibilidad
	- Facilidad de pruebas
- Se esta abandonando la estructura de Request-Reply a ***orientado a eventos*** haciendo uso de Kafka, por ejemplo.

>[!NOTE]
> Terminos que debo leer o buscar [[#BFF]], [[#SAGA]] y [[#pipelines and streaming]]
