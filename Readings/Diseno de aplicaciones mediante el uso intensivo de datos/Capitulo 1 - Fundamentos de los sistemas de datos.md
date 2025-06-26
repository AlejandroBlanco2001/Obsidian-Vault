---
tags:
  - databases
  - Lectura
  - sistemas-distribuidos
---
- CPU no es el problema actual, el ***volumen de datos y su manejo es el nuevo gran problema***.
- La mayoría de apps modernas necesitan de:
	- Bases de datos
	- Indices
	- Procesamiento en lotes
	- Procesamiento de flujos
- Las colas de mensajería, bases de datos y cache son todos ***sistemas de datos***
	- Limites difusos entre ellas
	- Por ejemplo, tenemos caches como Redis que actúan como colas de mensajería, y tenemos colas de mensajería como Kafka que hacen en cierta capa de retención
- Una sola herramienta, no basta para hacer todo lo que necesitamos
	- Combinar herramientas y manejar su comunicación via de software
	- Crearemos un ***sistema especial de datos*** a base de ***sistemas de datos generales***
	- Desarrolladores deben también ser diseñadores de sistemas de datos

Podemos decir que nuestro sistema debe ser:
- Confiable: Funciona aunque haya adversidades
- Escalable: El sistema funciona bien en términos de rendimiento, a pesar de un aumento de carga 
- Mantenibilidad: Debe ser razonable en el tiempo
# Confiabilidad
- Se puede entender como:
	- Hace lo esperado
	- Tolera un error del usuario o su mal uso por parte del mismo
	- Buen rendimiento ante una carga esperada
	- Impide el abuso y el acceso no autorizado

- Puede haber mucho tipos de fallas, pero debemos clasificarlas para saber cuales podemos prevenir y cuales deben ser necesarios cubrir
- Debemos recordar que ***una falla no es lo mismo que una avería***

> [!NOTE]
> Una avería puede ser mas comprendida como un error de operación de nuestros dispositivos, por ejemplo, que se vaya la luz en un lugar, o que un cable se corte y se rompa

- Por ende, nosotros queremos tener ***tolerancia a los fallos***

>[!IMPORTANT]
>A veces queremos deliberadamente introducir errores en nuestro software (hasta en producción) para probar la reacción en tiempo real del mismo, como lo hace Netflix con los [[Chaos Testing]] , a veces es mejor prevenir solo.

## Fallas de Hardware
-  Estos pueden ser como
	- Apagones
	- Fallas de discos duros
	- Memoria RAM defectuosas
- Introducción de redundancia puede ser una forma de mitigarlo
	- Ciertas aplicaciones mas pequeñas pueden tener una redundancia controlada 
	- Hay apps que requieren muchas maquinas lo que puede generar problemas

>[!NOTE]
>Empresas que proveen acceso a la nube como AWS, con el fin de tener mayor elasticidad y flexibilidad, pueden llegar a tener insuficiencia de maquinas, así que puede pasar que en algún momento no tengas una maquina.

## Fallas de Software
>[!NOTE]
>Aunque el error físico es muy probable, el de software es muy común y mas difícil de encontrar

- Para prevenir hay que hacer cosas como:
	- Test exhaustivos
	- Verificar dependencias
	- ...
## Fallas humanas
- El sistema lo operan y lo crean personas
- Hay mas fallos humanos que de software y de hardware
- Recuerda, ***una persona no es fiable***
- Para prevenir podemos:
	- Crear APIs administrativas
	- Tener lugares de sandboxing o pruebas
	- Uso de pruebas automatizadas y manuales
	- Configuraciones reversibles
	- Telemetría
	- Gestion y formación cultural

## Por que?
- No debe ser algo que importar solo en sistemas críticos, ya que, puede ocasionar perdidas económicas, danos personales o incluso muertes.

# Escalabilidad
- Necesitamos entender que es una ***parámetro de carga***
	- Depende de la arquitectura
		- Peticiones por segundos en un servidor web
		- Lectura/Escritura en una base de datos
		- etc
- Tomando el ejemplo de Twitter, 
	- Tenemos las siguientes operaciones:
		- Publicación de un twit
			- 4.6k peticiones por segundo en media y 12k en pico
		- Feed por persona
			- 300k peticiones por segundo
	- Partiendo de eso tenemos el siguiente problema, como hacemos para sincronizar los feed por cada twit publicado?
		- Método 1: Una consulta SQL para obtener basados en el tiempo de publicación por usuario
		- Método 2: Contamos con una memoria cache para cada usuario en la plataforma, de esta manera, cuando ingresamos un twit, escribimos en la cache de cada usuario
	- Inicialmente Twitter, opto por la primera, pero luego toco usar la segunda por motivos de tiempos de respuesta, sin embargo, los temas de escrituras era un problema que llevo a plantear la distribucion de usuarios como un tema imporante.
		- Debido a este problema, la distribución de seguidores por usuario es un ***parámetro de carga***