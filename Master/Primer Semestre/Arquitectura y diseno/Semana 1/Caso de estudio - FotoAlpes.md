---
tags:
  - restricciones-objetivos-negocio
  - master
---
***Que hacen?***
Es una empresa dedicada a las artes graficas, llevan 20 anos de fundada, tienen multiples sedes en 3 paises distintos, que cuenta con puntos físicos

***Motivo de contacto***
Innovación tecnológica

## Actividades
1. Toma de fotografías 
2. Revelado de rollos
3. Impresión digital

Sus estudios fotográficos, son orientados a familia

### Toma de fotografías
Operación con mas volumen, 50% de ventas y 20% utilidad

1. Seleccionas documento (Visa, pasaporte, ID)
2. Cancelas
3. Cabina
4. 20 minutos 
5. 6 copias para ti
### Revelado de rollos
Operación 10% de las ventas totales, costoso generados son mas grandes que las ventas

1. Entrega rollo
2. Cancela y recibe comprobante
3. 3 días después vuelve con su comprobante y ya

Estos deben ser llevados a un lugar por alguien
### Impresion digital
1. **Recogida de archivos:** Un empleado recoge cada mañana una memoria USB de los puntos de venta y la lleva al centro de producción.
2. **Impresión:** En el centro de producción, las fotos en formato digital se imprimen en papel o tela.
3. **Envío a proveedores:** Los productos impresos se envían a la marquetería o a un proveedor de estampación, según el servicio solicitado.
4. **Recepción de productos terminados:** El empleado recoge los productos terminados de los socios de negocio.
5. **Empaque y entrega:** Los productos terminados se empacan en el centro de producción y se envían a los puntos de venta para que el cliente los recoja.

- Los ingresos obtenidos por esta linea aporta 30% de las ventas totales
- Cuenta con proveedores de estampados y marquetería. Esto se realiza en el centro de producción
- Proceso dura 5 y 8 días

### Estudios fotograficos
- Mas nueva, rapido crecimiento
- Representa el 10% de las ventas totales

## Objetivos
### Transformación digital
- ***Desean crear*** una nueva linea de negocio llamado "Contenido Digital"
	- **Meta** Ingresos obtenidos pore este sean del 40% del total de ventas en los próximos 2 años
	- **Integra**
		- Fuentes de datos digitales
		- Camera propia 
		- Flexibilidad de adiccion de nuevos servicios
	- **Funcionalidades:**
		- Disenar camias, photobooks, enmarcaciones y otras opciones
		- Previsualizacion del producto
		- Generar una orden de producto, y pago electronico
	- **Logistica**
		- Cada socio del negocio hace su parte, y un servicio de mensajeria los recogera
	- **Ejemplo**
		- Una vez seleccionado la fuente, elegido la foto, previsualizado la foto, pagada y recibida el pago. FotoAlpes inicia el proceso de produccion, y una vez terminada se genera una orden de 
	- **Mercado**
		- Madre entre 26 y 40 anos de edad
		- Debe ser facil de utilizar
	- Integracion es clave, debe tener una gram gama de fuentes
- ***Desean crear una plataforma*** que funcione como un mercado electronico
	- **Meta**  Este debe representar ahora el 20% de las ventas en el próximo año
		- Recoger pequenos comercios y proveedores de artes graficas, y brindar desarrollo y operacion
	- **Funcionalidades**:
		- Muestra e interaccion de los productos
		- Registro de clientes
		- Registro de comercios
		- Manejo de pagos
		- Brindar analiticas sobre sus ventas
	- **Consideraciones:**
		- Cada tienda, ofrece su catalogo
		- Cada producto tendra su propia cadena de fabricacion en la que pueden participar proveedores
	- **Logistica**
		- Debe generar una comision a la venta
		- Cubrimos mantenimiento y operacion de la plataforma, gestion de pagos y de clientes, entrega de productos
	- **Presupuesto**
		- 25,000 USD
			- Infraestructura
			- Licencias
			- Recursos humanos e inftraestructura para ellos
	- **Duracion**
		- 8 meses
	- **Requisito**
		- **Rapidez** en operaciones como el calculo de tiempo, envio de productos, busqueda...
			- Tiempo de respuesta debe ser 2 segundos a lo mucho
		- Debe ser multiplataforma, por ende, es necesario la creacion de una API
		- Debe ser hecho en **Python**
	- **Carga**
		- 50 mil usuarios previstos
		- 10 mil usuarios concurrente
		- Integracion con plataformas y aplicaciones de aliados (Altamente integrable)
		- Nuevos servicios seran anadidos
## Como?
### Busqueda rapida de productos
- Debe poder buscar por:
	- Nombre
	- Codigo
	- Palabras claveas
- Debe responder con una lista de *productos y servicios* 
- Tiempo de respuesta < 2seg
- 100 consultas per segundos
### Manejo del pago
- Debe recibir un numero de confirmación
	- Seguimiento de su orden
- Tiempo de respuesta < 2seg
- Correo de confirmación < 5seg

### Manejo de usuarios
- Suministrar sus datos
- Validación de correo y clave
- Debe informarse todo en < 2seg

### Compra de productos
- Venta debe actualizar el inventario < 1 segundos
- Evitar que dos personas compre lo mismo

### Previsualización
- Selecciono mis fotos 
- Muestro preview y sus opciones
- Todo esto debe durar menos de 3 segundos

### Carga alta (Calidad)
- 100 consultas a 2000 consultas por segundo, debe conservar el tiempo de respuesta
- Intervalos de 8 horas 
- 20 ordenes a 1500 ordenes por hora, debe conservar el tiempo de respuesta
- Preview electronico -> 30 usuarios por hora
	- Este proceso demora 30 segundos
- En alta demanda, 200 usuarios por ahora
	- Conservamos el tiempo

### Multiplaforma
- Se espera dar el salto a movil

### Flexible
- Debe estar abierto a cualquier fuente de datos, relacional, no relacional, llave-valor...

### Flexibilidad
- El cambio en el FE debe ser lo mas rapido posible

### No funcional
- 15% crecimiento base de los usuarios por ano
	- 5000 clientes actuales

### Generador de álbumes
- Debe tener en cuenta numero de hojas y las fotográficas ubicadas (la mayor cantidad de fotos en el menor espacio posible)
- Su mejora debe ser sencilla
- No debe ser el mejor inicialmente
- Probablemente no una prioridad

### Algortimo de envio
- Debe optimizarse para enviar la mayor cantidad de producto a una misma ciudad o localidad (evitar multiples envios)
- Se debe mejorar siempre que se tenga una nueva variable
- Debe ser sencillo de modificar
