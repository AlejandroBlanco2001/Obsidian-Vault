Podemos definir a GRASP Como ***General Responsibility Assignment Software Patterns*** son una serie de 9 principios fundamentales en el diseno de objetos y la asignacion de responsabilidades.

## Creator

***Solucion:*** Asignar a la clase B la responsabilidad de crear una instancia de la clase A si una o mas de las siguientes conclusiones se cumplen:

- B **agrega** los objetos A
- B **contiene** a objetos A
- B **guarda instancia de** objetos A
- B **usa cercanamente** a objetos A
- B tiene **la informacion inicial que sera despues pasada** para objetos A 

Por ende, B **es el credor de** A

***Problema***: Quien deberia encargarse de la creacion de las nuevas instancia de alguna clase?

En el siguiente ejemplo

![[Pasted image 20240908012840.png]]

Desde que *Sale* contiene (de hecho, agrega muchos objetos *SalesLineItem*, el patron Creator sugiere que *Sale* es un buen candidato de tener esa responsabilidad.

![[Pasted image 20240908013004.png]]

***Discusion:*** Algo muy comun de OOP es la creacion de objetos, y hacerse la pregunta de quien crea las cosas es algo muy importante. El patron Creator nos brinda sugerencias de quien deberia ser el creador de algo (siempre promoviendo el bajo acoplamiento)

En este caso si alguien agrega, guarda o contiene, es muy probable que el sea muy buen candidato. De igual manera, si alguien tiene datos, y le pasa los datos para crear, de igual manera es muy buen candidato.

***Contradicciones:*** En caso de que la creacion de un objeto particular requiera algun tipo de logica compleja, es mejor usar el [[Patron Factory]].

## Low coupling 

***Solucion:*** Asignar la responsabilidad de tal maneara que haya bajo acoplamiento

***Problema:***  Como promover la baja depedencia, bajo impacto de un cambio, y patrocionar la re-usabilidad.

**Acoplamiento** es la medida en que tan fuerte un elemento esta conectado a, tiene conocimiento de, o se depende de otro elemento. 

Un elemento con **bajo acoplamiento** (o debil) es un elemento que no depende de muchos otros elementos. Dentro de los elementos se incluyen clases, subsistemas, sistemas y asi.

Mientras que **alto acoplamiento** (o fuerte) depende de muchas otras clases. Estas clases muchas veces es indeseable, porque sucede:

- Cambios en esas clases fuerzan cambios locales
- Entenderlas de manera aislada es mas compleja
- Mas complejar de reutilizar debido a que requiere mucha cosas adicionales

Consideremos este diagrama UML inicial

![[Pasted image 20240908014448.png]]

Con este enfoque *Register* sabe de *Payment* y sabe de *Sale*, por ende, podemos decir que *Register* esta altamente acoplada

![[Pasted image 20240908014916.png]]

Una mejor manera podria ser hacerlo asi, donde cada una tiene una unica responsabilidad.

***Discusion:*** Bajo acoplamiento es un principio que siempre debe ser teniendo en cuenta durante todos los principios de diseno.

Este principio patrocina asignar responsabilidades de tal manera que su posicion no incremente el acoplameinto.

Este patrocina tener clases que sean muy *independientes*, lo que reduce el impacto de un cambio.

Una subclase es **altamente acoplada** a su superclase. La decision de derivar de una superclase necesita ser altamente considerada.

>[!IMPORTANT]
> El alto acoplamiento no es malo per se, lo malo es el alto acoplamiento de elementos que son inestables en alguna demensnion

## High Cohesion

***Solucion:*** Asignar responsabilidades de tal manera que la cohesion se mantenga alta

***Problema:*** Como mantenemos la complejdiad manejable?

En terminos del diseno en objetos, la **cohesion** (o mas precisos, la cohesion funcional) es la medida de que tan fuertemente estan relacionados y delimitadas estan las responsabilidades de un elemento.

Una alta cohesion, indica que sus funciones tienen mucho en comun, y no hace muchas cosas fuera de esas.

Una clase que tiene poca cohesion, por el otro lado, hace muchas cosas que no tienen que ver una con la otra, y eso nos trae muchos problemas como lo pueden ser:

- Mas dificiles de comprender
- Mas dificiles de re-usar
- Mas dificiles de mantener
- Delicadas y siempre cambiantes

Una abstraccion no tan granulada.

![[Pasted image 20240908020024.png]]

En este caso, porque el registro tendria que hacer el proceso de creacion de pago? En este caso es aceptable, pero si esto crece, muy probablemente no salga beneficioso.

![[Pasted image 20240908020134.png]]

***Discusion:*** Se define la alta cohesion funcional cuando todos los elementos de una clase trabajan por una sola cosa

- Muy baja cohesion: Hace muchas cosas complejas, que no tienen nada que ver
- Baja cohesion: Hace una sola cosa compleja en mas de un area funcional
- Alta cohesion: Hace una cantidad de cosas moderadas en un solo area funcional.
- Cohesion moderada: Tiene varias responsabilidades juntas pero no tan fuerte, pero no es algo grave
