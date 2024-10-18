Los vistas de C&C (Components & Connector) nos muestan las cosas que cuentan con metodo de ejecuccion como procesos, objectos, clientes, servidores y fuentes de datos, lo que llamamos ***componentes***. De igual manera estos tambien cuentan con nuestras conexiones, puentes, flujos de informacion, lo que llamamos ***conectores***

![[Pasted image 20240827075759.png]]

 Muestra una imagen del sistema tal y como aparece en tiempo de ejecución. El sistema contiene un repositorio compartido de cuentas de clientes (Base de Datos de Cuentas) al que acceden dos servidores y un componente administrativo. Un conjunto de clientes cajeros puede interactuar con los servidores del repositorio de cuentas, encarnando un estilo cliente-servidor. Estos componentes cliente se comunican entre sí publicando y suscribiéndose a eventos. La finalidad de los dos servidores es mejorar la disponibilidad: Si el servidor principal deja de funcionar, el de reserva puede tomar el relevo. Por último, un componente administrativo permite a un administrador acceder al almacén de datos compartidos y mantenerlo.

En el ejemplo anterior, los tres tipos de conectores muestran un tipo de interaccion distinta:

- Conectores de tipo Client-Server: Permite a un set de clientes concurrentes traer datos de manera sincronica por medio de peticiones de servicio.

- Conectores de tipo database access: Permite transacciones, accesos autenticados para escritura, escritura y monitoreo.

- Conectores de tipo publish-subscribe: Permite anuncion y notificacion de eventos asincronicos


![[Pasted image 20240827081427.png]]
## Elementos 

Dentro de la vista de C&C todos deben ser tener su representacion al momento de ejecutarse (manifestacion como elemento en tiempo de ejecuccion).

### Componentes
Representan los principales elementos que se visualizan durante ejecuccion, cada uno debe tener un nombre, y este debe mostrar su utilidad.

Estos tiene interfaces denominadas ***puertos**** estos pueden ser enumerados, indicando el numero de instancias del mismo (puerto). Por ejemplo, `[3]` significa que 3 ocurrencias de este puerto, `[0..10]` significa que hay de 0 a 10 instancias del mismo.

>[!NOTE]
>Es una interfaz de un componente. Este define un punto de interaccion de un componente con su entorno

Este debe ser documentado de manera explicita.

Este componente, puede representar ***todo un subsistema complejo***, que puedo ser descrito como una sub-arquitectura de C&C. Esta puede ser decompuesta en otro documento o de manera interna.

### Conectores
Ejemplos de estos pueden ser invocacion de servicios, colas asincronicas de mensajes, multicast de eventos y pipes de streams. Estas puede en si representan relaciones complejas del flujo de datos 

Estos cuentan con ***roles***, que son interfaces que indican en que manera el conecto manejara esa interaccion, por ejemplo:

- client-server connector: invokes-services and provides-service 
- pipe: writer and reader

Estos tambien pueden contacr con enumeracion para recalcar la cantidad de conectores en una interracion.

## Relaciones

La principal relacion de esta es ***attachment***, esto indica que conectores estan adjuntos a que componente. Esto es denotado, usando una asosiacion (attaching) el puerto de un componente con el rol de un conector.

Esto esta bien hecho en el contexto semantico de ambos, es decir que el rol tenga sentido en funcion del puerto:

> Imagina una arquitectura de tipo call-return, deberias confiar que todas los puertos de "llamadas" estan asociados algun conector de tipo call-return

Otro segundo tipo de relacion es la de ****delagacion de interfaces***. Donde un componente o conector cuenta con una subarquitectura, es importante documentar las relaciones internas dentro de la estructura y como estan se relacion hacia el exterior.

Estas deben ser documentadas relacionando puertos internos con con puertos exteriores.

![[Pasted image 20240828232309.png]]

**Figure 3.2** A UML component diagram showing the subarchitecture of a component called `Catalog`. UML delegation connectors associate the ports of `Catalog` with the ports of internal components.

## Propiedades

1. **Confiabilidad**: Probabilidad de fallo de un componente o conector.
2. **Rendimiento**: Tiempos de respuesta, latencias y capacidad de procesamiento bajo diferentes cargas.
3. **Requisitos de recursos**: Necesidades de procesamiento y almacenamiento.
4. **Funcionalidad**: Funciones que desempeña un elemento.
5. **Seguridad**: Capacidades de seguridad, como encriptación o autenticación.
6. **Concurrencia**: Si el componente se ejecuta en un proceso o hilo separado.
7. **Nivel (Tier)**: Nivel en una topología jerárquica.


![[Pasted image 20240828232712.png]]

***Figura 3.3*** Un diagrama de vista de C&C mal documentado. No tiene una leyenda; representa una interfaz (asumiendo que "API" tiene el significado común de una interfaz) como un componente; utiliza diferentes formas para el mismo tipo de componente; usa la misma forma para diferentes tipos de componentes y conectores; confunde el contexto con el sistema que se va a construir; el uso de las flechas no está explicado; y sus componentes no tienen puertos

Un buen ejemplo podria ser en la notacion ADSL

![[Pasted image 20240828232908.png]]

Equivalente en UML

![[Pasted image 20240828233142.png]]
## Contraste entre modulos y componentes

![[Pasted image 20240829214358.png]]


## Implementaciones 

[[Client-Server Style]]
[[Peer-to-Peer style]]
[[Service-Oriented Architecture Style]]
