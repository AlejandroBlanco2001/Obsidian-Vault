---
tags:
  - databases
  - query
---
> Los limites de lenguaje significan los limites de mi propio mundo - Ludwig Wittgenstein

La existencia de un ***modelo de datos***, implica la existencia de un ***lenguaje de consulta***, y tenemos que entender que dicho modelo/lenguaje *nos limita y nos obliga a pensar de cierta forma sobre nuestro problema y sus abstracciones*

Debemos recordar que este se puede plantear como un problema del [[Layered Style]], donde podemos decir que la pregunta clave es

> Como se representa en términos de la capa inferior

Por ejemplo, partamos de un caso real:
- El desarrollador visualiza el ***mundo real***, para representar las entidades en ***estructuras de datos o API's***
- El creador de RDBMS necesita convertir dichas ***estructuras de datos o API's*** en ***JSON, XML, grafos o tablas en una base de datos relacional***.
- El ingeniero de hardware necesita volver los ***JSON, XML, grafos...*** para almacenarlos en ***bytes dentro de nuestra memoria***.
- El ingeniero eléctrico necesita ***volver dichos bytes*** en ***señales eléctricas*** para que nuestro hardware la interprete.

>[!IMPORTANT]
>Cada capa debe ocultar la complejidad a la otra, de tal manera, que el de abajo pueda trabajar fácilmente 

## Relacional vs Documentos

- El modelo SQL (académicamente conocido como el modelo relacional) fue ideado por Edgar Codd a mediados de los 70.
	- Era meramente teórico, y no parecía eficiente
	- Los RDBMS (**R**elational **D**ata**B**ase **M**anagement **S**ystem) y la creación de SQL probaron que si podia serlo.
	- Fue originado por la necesidad de procesamiento de datos empresariales 

> [!NOTE]
> Actualmente podemos este caso de uso como algo mundano, cuando hoy en día como: Transacciones bancarias, transacciones locales, procesamiento en lotes...

- El triunfo de SQL oculta es mas que todo porque oculta las complejidades, donde otros modelos no pudieron hacerlo.
	- Jerárquico
	- Red
	- XML (Desapareció)
	- Objetos (Desapareció)

> [!NOTE]
> Con el crecimiento de los recursos (CPU, memoria y almacenamiento), las bases de datos relaciones se adaptaron muy bien

## NoSQL

>[!NOTE]
>Curiosamente este nombre nace de un hashtag para una convención de codigo abierto, no era un buen nombre para referirse a algo en particular.

- Una mejor manera de entender NoSQL, es ***Not Only SQL***, donde los principales motivos eran:
	- Tener una mayor escalabilidad
	- Codigo abierto y software libre sobre el codigo propietario
	- Consultas mas especializadas para casos mas particulares
	- Dinamicidad y expresividad del esquema.

## Objetos vs Relacional

> [!IMPORTANT]
> Si piensas en objetos, debe haber una traducción de esto al idioma relacional, básicamente volverlo una tabla y este proceso es **costoso mentalmente** y se denomina *desajustes de impedancia*

Nosotros los desarrolladores usualmente pensamos en objetos (la mayoría de los lenguajes aceptan OOP), y si inventaron los ORM (Object Relational Mapping) para disminuir dichas fricciones.

Tomemos como ejemplo, los perfiles de LinkedIn para la construcción de currículos y así (Relaciones 1-To-Many)

- Solución SQL antigua: Multiples tablas para cada uno de los campos asociados
- Solución SQL moderna: Guardar el atributo como un campo de tipo JSON o XML para poder hacer consultas especializadas
- Solución SQL hack: Guardar todo la estructura como un campo de texto y perder la capacidad de consultar


Aunque usar JSON pueda parecer una solución mas coherente y viable para todos los casos, y tiene ventajas como:
- Reduce el desajuste de impedancia
- Se representa de una manera natural los datos, recordemos que esto se asemeja a un árbol, básicamente natural para el JSON

## M-To-1 y M-to-M
- Normalizar y des normalizar es el producto de duplicar/des duplicar los datos
	- El modelo relacional permite hacer uniones
	- Los modelos basados en documentos, implican que las uniones se hagan de manera manual
- Aunque parezca que podemos evitar dicha conexión con los datos, ***con el tiempo estos siempre se relacionaran***

## NoSQL: Un problema antiguo?
>[!IMPORTANT]
>La manera correcta de representar los datos es un problema que existe desde antes de los modelos actuales (incluso el relacional)
>

Antes de todo teníamos el *modelo jerárquico*, que nos permitía tener un árbol de registros anidados (muy parecido a MongoDB con los documentos).
- Nos permitia tener muy buenas relaciones 1-To-M, pero muy malo para M-To-M 
- No podíamos hacer uniones con el lenguaje, tocaba manualmente ajustar todo y tener redundancia