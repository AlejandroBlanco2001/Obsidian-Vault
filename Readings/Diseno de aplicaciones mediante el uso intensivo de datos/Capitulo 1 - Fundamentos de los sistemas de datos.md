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
- Por ende, nuestro enfoque debe ser siempre un análisis de la carga en un caso creciente:
	- Si aumentamos la carga, y mantenemos los recursos, *que pasa con el rendimiento?*
	- Si aumentamos la carga, *cuantos recursos necesitamos para mantener el rendimiento deseado?*
- El rendimiento de un sistema es distinto por sistema:
	- Hadoop entiende el rendimiento como
		- Registros procesados por segundo
		- Tiempo para procesar un lote de X volumen
	- Para un servidor web puede ser el tiempo de respuesta del servicio

> [!IMPORTANT]
> La latencia no es lo mismo que tiempo de respuesta, el segundo es el tiempo percibido por el cliente (además de incluir el tiempo de servicio y todos los retardos), mientras que la latencia es el tiempo de solicitud para ser tratada mientras esta latente.
> 

- Siempre debemos tener unas metricas para llevar estos numeros para poder comparar y analizar nuestros rendimientos
	- El promedio no es una buena idea puesto que oculta las anomalías, y no queremos eso.
	- Deberíamos usar percentiles como el 90,95 y 99.99 ($p90$, $p95$. $p99.9$) para medir nuestros tiempos
		- Estos últimos se conocen como ***latencia de cola***

> [!NOTE]
> Amazon mide sus servicios internos en base al $p99.9$, debido a que notaron que este es el grupo que mas productos comprados y/o para vender tienen, por ende, es muy importante siempre tenerlos felices y no perderlos.
> 
> De igual manera, notaron que ciertos retrasos en algunas peticiones ocasionaban problemas a nivel de ventas y satisfacción del usuario

- Recordemos que tendremos algunos problemas donde independientemente de nuestros recursos, podremos tener problemas al procesar las peticiones, esto se llama ***bloqueo de cabecera***
- Siempre recordemos que aunque nuestra arquitectura presente sea muy apropiada, a medida de que la carga aumente, siempre se degradara.

> [!NOTE]
Al dia de hoy, sigue siendo preferible llevar la base al limite de sus recursos en un nodo, debido a los problemas que traer la distribución de las mismas

## Mantenimiento
- El software cuesta no por el tema de obtener gente y sus operaciones, es mas bien prepáralos para sus tareas diarias y adopción del sistema.
- El software de legado es algo que nosotros mismo creamos, y de igual manera odiamos.
- Para evitar esto, tenemos las siguientes opciones:

### Operabilidad
Recordemos que la operabilidad es que nuestro sistema pueda ser operado con facilidad, en el sentido de tener cosas como:

- Monitoreo
- Observable
- Actualizable
- Manejo de dependencias
- ...

Por ende, tener una buena operación puede ayudar a salvar un mal sistema, pero no al revés. Alguna de las cosas que deberíamos tratar de tener son:

- Mantenimiento de seguridad
- Procesos predecibles y automáticos
- Actualización de los componentes de nuestro sistema
- Preservación del conocimiento
- Proporción de visibilidad
- Soporte
- ....
 
### Simplicidad
Nuestro sistema debe ser simple para que pueda ser razonado, en proyectos pequeños esto es fácil de obtener (seria preocupante que no), con el tiempo estos se harán inherentemente mas complejo por muchos posibles motivos, como:

- Hacks para temas de rendimiento o operación
- Alto acoplamiento
- Explosion de estados
- Buzzwords
- ...

Por ende, debemos recordar lo mencionado en [[Why Can't We Make Simple Software - Peter van Hardenberg]] sobre temas de ***complejidad accidental***, donde esta proviene de la implementación, no del problema que proponen el usuario.

Debemos recordar que mantener un sistema ***lo hace mas propenso a errores debido a que suponemos mas cosas debido a la no certeza con muchas cosas*** 
### Evolución
- Los requerimientos cambian, siempre, pueden ser debido a:
	- Cambios en dependencias ajenas a nosotros
	- Cambios legales 
	- Cambios en los deseos del cliente
	- Nuevas necesidades

- Agile ofrece una capa de herramientas como (TDD, refactoring..), sin embargo, ***su enfoque es muy local***

>[!IMPORTANT]
>Para una evolución orgánica y mas fácil de llevar, cuanto ***mas simple tu sistema mejor***

