Tags #QA #e2e 

Cuando realizamos nuestras pruebas de punta a punta, estas estan sujetas a trabajar sobre nuestro HTML (probablemente eso es lo unico que haran), por ende, siempre tenemos que tener en cuenta que esta ***UI va a cambiar***, y no queremos que nuestras pruebas se vean afectadas por lo mismo.

Por ende, podemos usar la arquitectura de ***PageObject***, donde basicamente al API se encarga de la aplicacion, mas no del HTML

![[Pasted image 20241105213247.png]]

Nuestras pruebas de punta a punta deben basarse en una API que se encargue de ***esconder los detalles de como manipuar UI***, tu solo debes preocuparte que al momento de leerlos, tenga sentido para un cliente.

Aunque el termino "page" puede resultar un poco desconcertante, lo ideal es que esta se refiera a esa abstraccion de nuestra interfaz,

Esta arquitectura no deberia realizar aserciones, deberia encargarse unicamente de brindarnos herramientas para manipular nuestra aplicacion.

Aunque este tambien pude ocultar mas operaciones dentro de la UI, que solo la UI en si, como lo pueden ser temas de asincronia .