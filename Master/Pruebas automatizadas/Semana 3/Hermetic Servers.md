Tags #QA #Lectura

Link: https://testing.googleblog.com/2012/10/hermetic-servers.htmlv

Imagina que tienes una aplicacion web demandante, que cuenta con multiples funcionalidades, muchas animaciones, varias peticiones a tu API, y todos estan viajan a traves de multiples nodos. Como hacemos nuestras pruebas e2e?

# Que es un e2e para Google?

Recordemos que un e2e es algo que basicamente cubre todo el flujo de un software, desde el cliente hasta la respuesta del servidor. El siguiente diagrama cubre este ejemplo

![[Pasted image 20241024210738.png]]

Por ende, alguno de los muchos problemas es que el cliente siempre sera rapido, ya que tiene todos los recursos a las manos, sin embargo, como hacemos que nuestro servidor que sea **rapido** y **confiable**.  Esto siempre causa ***flaky test***

# Servidor Hermetico

Un **servidor hermético** es esencialmente un servidor autónomo que puede funcionar por completo en una sola máquina sin necesidad de conexión a la red. Esto lo hace ideal para realizar pruebas, ya que puede simular y probar un sistema completo de forma aislada. Los servidores herméticos son útiles porque permiten ejecutar pruebas sin necesidad de recursos de red externos, lo que simplifica la configuración y hace que las pruebas sean más fiables. Estos servidores pueden funcionar en máquinas físicas o virtuales.


## Diseno

Esto siempre estar contemplado al momento de realizar un servidor nuevo:

1. Todas las conexiones a otros servidores deben ser realizadas por medio de la inyeccion de dependencia como lo pueden flags por comandos o herramientas como [Guice](http://code.google.com/p/google-guice/).
2. Todos los archivos estaticos deben estar en el binario del servidor
3. Debemos tener datos de pruebas cargados que mocken las llamadas

Tener esto ya asegura el funcionamiento de un servidor hermetico:

1. Asegurarse que los mocks sean lo mas parecido a la realidad
2. Proveer modulos que sean faciles de popular
3. Usar loggers

# Servidores hermeticos en los e2e

![[Pasted image 20241024214133.png]]![[Pasted image 20241024214133.png]]

La prueba de extremo a extremo sigue estos pasos:

1. Inicia todo el sistema bajo prueba (SUT) en una sola máquina.
2. Envía solicitudes al servidor mediante un cliente de prueba.
3. Valida las respuestas del servidor.

En esta prueba, no es necesaria una conexión simulada para el backend; si una solicitud requiere conexión con el backend, sería necesario un servidor hermético en ese punto. Esta prueba es más confiable y rápida al no requerir conexión de red, ya que todo se encuentra en memoria o en el disco local. Estas pruebas se ejecutan continuamente con cada cambio que afecta al SUT, y en caso de fallos, el módulo de registro ayuda a identificar el punto exacto de fallo en el sistema.

Usos comunes de los servidores herméticos en pruebas incluyen:

- Pruebas de inicio de servidores con Guice para verificar errores.
- Pruebas de API para servidores backend.
- Micro-benchmarks de rendimiento.
- Pruebas de UI y API en servidores frontend.