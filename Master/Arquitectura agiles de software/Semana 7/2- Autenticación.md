Tags #tacticas-arquitectura #seguridad #arquitectura-de-software #atributos-de-calidad 

Podemos definir nuestras tácticas en los siguientes grupos: 
- Detección de ataques
- Resistir ataques
- Reaccionar a los ataques
- Recuperation de los ataques

## Detección de ataques
- Detectar intrusiones
	- Identificación de patrones de eventos que coinciden con patrones conocidos de ataque
-  Verificar la integridad de mensajes
	- Uso de hashs para la verificar la integridad de los mensajes
- Detectar retardos en los mensajes
	- Los retardos pueden indiciar la posibilidad de un ataque de tipo "hombre en el medio"

## Resistir los ataques
> Superficie de ataque son todos los puntos de contacto entre el exterior y el sistema a crear

- Identificar los actores
	- Identificar las fuentes externas al sistema que pueden estar causando el ataque,
- Autenticar actores
	- Verificar que el actor es quien dice ser
	- Uso de biométricos, MFA
- Autorizar actores
	- Asegurarse de que los actores tengan los permisos y niveles de autorización.
- Limitar el acceso
	- Limitar a los procesadores, conexiones, memoria …
- Separación de entidades
	- Manejar fuentes de datos y procesamiento (microservicios) en diferentes espacios de ejecucción, diferentes contenedores, maquinas virtuales o servidores.


## Reaccionar a los ataques
- Revocar acceso
	- Si se sospecha que un actor es la fuente de un ataque se debe limitar el acceso a unidades de procesamiento
- Bloquear computadores
	- Si se detectan multiples intentos fallidos de ingresar a un computador, se procede a bloquear el acceso a dicha unidad de procesamiento (Puede afectar a la disponibilidad del sistema)
- Informar a los actores
	- Si se detectan posibles ataques de seguridad se debe notificar a las personas indicadas para tratar de responder lo antes posible 

## Recuperaciones de ataques
- Restauración de servicios
- Manejo de log de eventos