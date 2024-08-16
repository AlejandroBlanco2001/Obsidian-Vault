Un mecanismo para la especificacion de requisitios de calidad son los ***escenarios de calidad***  que propone Bass

- Identificar momentos claves\
- Como deseamos verlos 

Debemos ver nuestro sistema como una caja negra, donde tenemos una ***fuente*** qe genera un ***estimulo***, y esta al interactuar con nuestro sistema genera una ***respuesta***

Por ejemplo, un usuario seleciona una opcion para ver los productos comprados

***Fuente*** Un usuario
***Estimulo*** Solicitud de envio de los produtos
***Respuesta*** La generacion de orden de envio

Entre la recepcion del estimulo y su respuesta, se necesita que sea en menos de 3 segundos, esto se denomina ***medida de la respuesta***

Para definir esto como un ***escenario de calidad***, debemos: 

1. Describirlo con un nombre adecuado que denote su intencion
	"Manejo de solicitud de productos"
	
2. Definimos su fuente la que genera el escenario (No necesariamente una persona)
	Comprador

3. Definimos el estimulo que genera la respuesta deseada de nuestro sistema
	"Creacion de orden de envio"

4. Definir la respuesta esperada de nuestro sistema
	"La orden de envio ha sido creada"

5. Definir la medida de la respuesta
	"En menos de 2 segundos"

![[Pasted image 20240816105058.png]]

En este caso, el ***Desempeno*** es el atributo de calidad

Si en otro caso, cambiaramos la condicion, a que el sistema siempre este disponible, es decir, la ***medida de la respuesta*** seria que debe ser la misma respuesta el 99,99% de las veces. Por ende, el atributo de calidad seria ***Disponibilidad***

El esccnario de calidad, ***solo debe tener UN*** atributo de calidad. De igual manera, la medida que utilicemos, debe ser medible (obviamente)

De igual manera, en un escenario de calidad, hablamos del ***ambiente***, que es las condiciones en que se ejecuta (el contexto), ejemplos del ambiente son:

- Operacion normal del sistema
- Bajo un ataque de DDOS
- En recuperacion de una caida del sistema

![[Pasted image 20240816105836.png]]

En nuestros escenarios, tambien contamos con un componente que recibe el estimulo, en este ejemplo, seria un componente de manejo de soliciutedes de texto. Inicialmente, el artefacto es el sistema completo.

