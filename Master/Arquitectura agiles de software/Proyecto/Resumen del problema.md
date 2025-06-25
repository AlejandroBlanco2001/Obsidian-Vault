---
tags:
  - arquitectura-de-software
  - master
---
# Empresa

Empresa: **CCP**

Que hacen: Venta de productos masivos en diferentes paises
Procesos: Se encargan de 
- Compra de productos a los fabricantes y almacenamiento
- Venta de los productos a grandes superficies, supermercados, autoservicios y tiendas a nivel nacional
- Entrega de los productos vendidos a los establecimientos
Presencia en:
- 5 paises
	- 5 grandes bodegas por pais
Fuerte: Mayorista 
- La compra y venta es a fabricantes locales e internacionales
- Cada compra obedece al potencial de venta

La venta de los productos realiza una fuerza de ventas de cerca de 250 vendedores por pais
- El vendedor tiene una cuota de venta, donde el sugiere al cliente: cantidad y productos
- Diligencia una orden de producto, entrega una cotización y tiempo de entrega

Una vez tenemos la orden de pedido, el área de logística hace todo lo posible por cubrirla. 
- Validar con bodega la ubicación de los productos
	- Traer desde la mas lejana es una opción si no hay
- Se pueden programar uno o varios envíos
	- Siempre buscamos el menor numero de envíos
- Transporta el producto, descarga, recoge el dinero
	- Al final del dia transfiere.

Contexto añadido:
- Manejan 5000 referencias de productos
- Bodegas son propias
	- Mas 30 bodegas en diferentes paises
		- Por ende tenemos destinas monedas y aspectos legales distintos
- Realizan análisis de mercados para la venta y compra de materiales
- Las negociaciones las lidera CCP
- CCP realiza los tramites legales con los clientes internacionales
- CCP compra los productos requeridos y los almacena donde van estratégicamente
- Cada vendedor tiene su inventario y la lista de productos
	- Deben llenar un formulario donde describe la ubicación del producto y los de la competencia
	- Cada vendedor, debe llenar un informe en el que describe la ubicación del cliente, puntos y zonas de interés
	- Programación anual de los principales eventos en su zona de cubrimiento
- El producto debe ser entregado en 2 días
- El pagado puede ser por partes, por medio de facturas 
	- 60 días posterior a la descarga para las grandes
	- Contra entrega directamente para los pequeños
- El producto puede ser devuelto
	- Mala calidad
	- Productos equivocados
	- Arrepentimiento

# Problemas

- Situación: Actualmente tienen el 45% del mercado en los paises donde tienen presencia
	- Quieren incrementar un 3% de manera anual por los siguientes 4 años.

> El promedio en cada pais se atienden unos 50000 clientes

- Situación: Hay errores en las entregas provocados por alcance y factores varios
	- Desean reducir el costo de los errores de 800000 USD anuales en un 10% durante los próximos 2  años

- Situación: Las bodegas cuentan con productos perecederos, inventarios desactualizados entre otros
	- Desean reducir el costo de los errores en bodegas de 450000 USD anuales en un 60% en el siguiente año.

 > Actualmente no sabemos en realidad cual es la mejor combinación de productos y cantidades para realizar compras e importaciones
 
 - Hay gastos innecesarios en compras de grandes productos que no se usan, y productos que se necesitan que no se compran en la cantidad apropiada
	 - No hay claridad de los productos que tenemos
	 - Hay problemas en almacenamiento que genera perdidas
	 - No hay claridad con los fabricantes y sus productos.

> Nuestra fuerza de venta no cuenta con las herramientas para dar un buen servicio

- El inventario al no estar actualizado, ofrecemos cosas que no hay
- Hay retrasos en los tiempos de entrega, o productos en malas condiciones
- No usamos todo el contexto del los vendedores
- No hay fuerza para cubrir las necesidades de un evento especial.

> No hay información en tiempo real del inventario de bodega

- No hay control exacto durante la preparación del envio, lo que provoca entregas cosas que no son.
- No hay una buena planeación de las entregas, no tenemos rutas eficientes y a veces con rutas malas.
- No hay un correcto manejo de inventario, los productos desaparecen
- Vulnerabilidad de los conductores al manejar efectivo.


# Objetivos
> Diseñar un sistema de apoyo a las areas de compra, ventas y logística

## Compras
Se le quiere ofrecer un modulo que le permita tener un registro unificado de los fabricantes a los que se les compran productos en todas los paises.

Además de un portafolio internacional para análisis de mercado

El sistema de registro debe permitir registro individual y masivo de todos los productos de un fabricante, con todos sus detalles.

También debe contar toda la información legal pertinente a cada producto por pais.

Debe existir comunicación con sistemas de inventario y ventas.

Además que debe contar con un algoritmo de optimización de compras, que recibe como entrada el inventario de un producto, las ventas proyectadas, los eventos que sucederán en cada zona, y su salida, es la cantidad optima a comprar para el fabricante.

### Requerimientos de calidad

La carga masiva de la información de los productos ***debe tomar menos de 3 segundos***

La ***disponibilidad de registro debe ser 7x24x365***

El modulo de compras debe poder integrar con el modulo de ventas e inventarios, esta información ***se debe poder importar en 2 segundos.***

El componente de calculo para la optimización de compras ***debe generar el resultado en menos de 4 segundos***

El componente de calculo para la optimización de compras ***puede procesar normalmente 40 peticiones por minuto***, pero debe poder procesar hasta ***300 peticiones hasta por periodos de 30 minutos***
## Ventas
Estos contaran con un dispositivo móvil que les permita realizar su trabajo (una aplicación móvil)

- Consulta en tiempo real del inventario y sus cantidades
	- Una vez ofrecidas se deben bloquear dichas cantidades
- Captura de video con el fin de usar un algoritmo de recomendación, que le indicara al vendedor cambios en la distribución para maximizar ventas.
- El algoritmo debe también dar, productos adicionales a ofrecer, teniendo en cuenta ubicación de la tienda, época del año y los eventos, ofreciendo una cantidad estimada  
- Creación de cuenta por parte del tendero para para realizar pedidos
	- Consultar el estado de su pedido
	- Seguimiento
	- Pago por medios móviles 

El modulo de ventas (web) debe permitir crear vendedores y asignarles grupos de clientes y definir sus planes.

## Requerimientos de calidad

También debe permitir generación de reportes e informes de ventas, por vendedor, producto, zonas y mas.
- El proceso de creación de un reporte debe ser ***menos de una hora/hombre***

 La aplicación ***debe calcular el tiempo de entrega y notificar en menos de 2 segundos*** al vendedor de la posible fecha de entrega.

La ***disponibilidad de la aplicación debe ser 7x24x365***

El modulo de ventas ***deberá procesar 100 pedidos por minuto***, pero podría subir a ***400 pedidos por minuto por pedidos de una hora*** 

Para el tendedero, este podría ***consultar los estados de los pedidos en menos de un segundo***

## Inventario
Un modulo de apoyo del control de inventario, que permita localizar rápidamente donde estan las cosas y registrar su salida del mismo para actualizarse.

El modulo debe recomendar a los bodegueros como deben seleccionar los elementos de la manera mas optima para despachar. Esto incluye productos de otras bodegas

También debe permitir a los encargos de logística programar las rutas de los camiones para el día siguiente y registrar su salidas.

### Requerimientos de calidad

El proceso de registro y actualización del inventario debe ***tomar menos de un segundo***

Un producto debe ser localizado en la bodega ***en menos de un segundo***

La generación de rutas optimas debe tomar ***menos de 5 segundos para ser calculada***.

El monitoreo en tiempo real de los camiones debe poder visualizarse en un mapa, el proceso de recargar ***esto debe tomar menos de 500ms***

El algoritmo de recomendación de orden de compra debe entregar el ***resultado en menos de 2 segundos***

## Aspectos generales y requerimientos extras
- Evitar cometer fraudes de productos (Sacar productos sin registrar)
- Solo personas que hacen compras y autorizan ventas pueden realizar dicha operación
- La detección de operaciones fraudulentas debe ***tomar menos de 2 segundos***.
- La consulta de los planes y metas de un vendedor, así como las tiendas atendidas, históricos, debe ***ser presentando en menos de 2 segundos***
- El algoritmo de calculo de rutas debe:
	- Generar rutas a 20 camiones en ***menos de 5 segundos***
	- Este calculo debe poder  realizar este calculo ***para 100 camiones en 10 segundos***.
	- Puede ser modificado en menos de ***20 horas / hombre***.
	- Errores en el calculo debe ser ***detectados y corregidos en menos de 2 segundos***.
-  El algoritmo de recomendación debe ***poder atender 20 solicitudes por minuto***, pero también debería **poder 100 solicitudes por minuto en periodos de una hora**


# Tiempos, costos y mas
- Tiempo: 8 semanas (Arquitectura) + 8 semanas (primer desarrollo) = 16 semanas 
	- Pruebas de concepto
	- Experimentación
	- Desarrollo de la versión inicial

- Costo humano: 4 arquitectos (15.000$ mensuales) para las 8 semanas, 4 desarrolladores por 8 semanas (no hay costo) = 120.000 dólares en los arquitectos + ? en el desarrollo 

- Fecha de entrega: Rígida, no aplazable

- El costo de operabilidad no debe pasar de 1000 USD mensuales

- Tecnologías
	- Flask - Python
	- Base de datos relacional - Libre
	- Microservicios es el estilo