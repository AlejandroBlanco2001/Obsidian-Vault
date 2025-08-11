---
tags:
  - cloud
  - master
  - arquitectura-de-software
LInk: https://learning-oreilly-com.ezproxy.uniandes.edu.co/library/view/cloud-native-architecture/9781484272268/html/511610_1_En_3_Chapter.xhtml
---
>[!IMPORTANT]
>Recordemos que estos principios y patrones son para darnos una guía a donde encaminar nuestro desarrollo, no son una camisa de fuerza

Primeramente recordemos que es un principio de arquitectura

> Es una regla o ley que es usualmente seguida cuando se hacen decisiones de arquitectura importante, estos no son mandamientos

Estas decisiones cumplen un papel importante mas allá de lo tecnológico, moldean el futuro de una organización hacia su futuro desarrollo, puesto que esto impacta en todos los niveles que tenemos.

Una buena forma de validar que algo es un buen principio:

- Entendible: Debe estar escrito en lenguaje plano que es ***facil de entender***
- Robusto: Debe asegurar ***decisiones de buena calidad*** sobre la arquitectura y los planes
- Completo: La declaración debe ser ***precisa y completa***
- Consistente: Todos deben funcionar de una manera ***consistente y complementarse***
- Estables: Deben ***resistir y acomodarse*** a los cambios necesarios
- Resilientes: Debe ***permitir el auto-saneamiento tan rápido*** como sea posible

# API First

Las API son algo bastante viejo en el mundo del IT, sin embargo, pero estas eran limitadas al uso *interno de las aplicaciones*.

Hoy en día, esto debe ser un hecho para todas nuestras aplicaciones, todas deben estar diseñadas con ese enfoque en mente para ser accesibles a través de interfaces REST HTTP.

- La API es la primera interfaz de usuario de una aplicacion
- La API viene primero, luego la implementación
- La API es descriptiva
- La API estipula un contrato entre el proveedor y el consumidor

![[Pasted image 20250811154923.png]]

Donde nos ofrece los siguientes beneficios:

- Los equipos de desarrollo pueden trabajar en paralelo: API first implica establecer el contrato. La creación de un contrato entre servicios que es seguido por el equipo en todas las empresas permite a esos equipos trabajar en múltiples API al mismo tiempo.

- Reduce el coste de desarrollar una aplicación: la reutilización del enfoque API first permite reciclar el código de un proyecto a otro, de modo que los equipos de desarrollo siempre tienen una arquitectura básica con la que pueden trabajar.

- Aumenta la velocidad de comercialización: las API automatizadas y detectables pueden descubrirse rápidamente y automatizar el desarrollo con herramientas fácilmente disponibles como Swagger.

- Mejora la experiencia del desarrollador: los consumidores de API suelen ser el equipo de desarrollo. API first garantiza que los desarrolladores tengan una experiencia positiva al utilizar las API.

- Reduce el riesgo de fallo: la posibilidad de error se reduce considerablemente gracias a la fiabilidad y coherencia inherentes al diseño y la implementación.]

# Polylithic Architecture Principle

Cada microservicio se encuentra encargado de una funcionalidad del dominio, donde buscamos generar la sensación de un solo sistema a partir de subsistemas mas granulares.

En este caso, creamos servicios basados netamente en el dominio usando metodologías que lo favorezcan como DDD

![[Pasted image 20250811155347.png]]

Sus propiedades son las siguientes:
- Encapsulación: Los servicios esconden su implementación y solo exponen sus firmas
- Simplicidad: Todos tienen una única responsabilidad
- Sin Estado: Solo son codigo, no guardan estado
- Puras: Estos pueden ser puros, por lo cual facilita su comprensión

De igual manera esto parte de otras dos ideas:
- Cada subsistema granular tiene que esa en su propio contenedor y aislado de los demás subsistemas
- Cada subsistema maneja única y exclusivamente sus datos, y solo expone interfaces bien definidas.

# Polyglot Persistence Principle

De la creación del principio anterior, nace también una abstracción para los datos, donde cada microservicio debería tener sus datos y usar lo que necesita

> Debemos tener el almacenamiento correcto, para el dato correcto

![[Pasted image 20250811155817.png]]

# Modeled with Business Domain Principle

El MBDP es hacer uso de la metodología DDD (Domain Driven Design), donde nos suple la necesidad de hacer que nuestra solución responda a cambios en el negocio que son muy complejos de manejar.  

Se usa para desacoplar los sistemas existentes que no necesitas conocer de antemano o de una empresa con una distribución compleja

![[Pasted image 20250811160047.png]]

# Consumer First Principle

Es el hecho de diseñar nuestras API con el consumidor en mente, antes que el mismo diseno. Para esto debemos saber que quiere el consumidor.

- Quienes son mis consumidores?
- Quienes son en la organización?
- Necesitan algún tipo de colaboración por parte de otro sistema?

Una vez tienes estas preguntas resueltas, debes trabajar con tu equipo de diseno para manejar un contrato de API ***igual para todo el mundo*** con el fin de tener una consistencia entre las APIs.

# Decentralize Everything Principle

El DEP, establece que todo debe ser descentralizado para otorgarle una mayor libertad a los equipos de desarrollo sin perder la gobernanza y los estándares.

> Debes brindar las herramientas para la autonomía del equipo involucrado, sin necesariamente coordinar con mucha gente y quitarles su libertad.

- Descentralizar los microservicios que están aislados de otros microservicios para ayudar al equipo a lograr objetivos como la capacidad de prueba, la extensibilidad, la escalabilidad, etc. Aplicar el diseño basado en el dominio y el contexto delimitado para descentralizar los microservicios basados en el dominio.

  - Implementar los microservicios de forma independiente en cualquier entorno sin afectar a otros servicios, utilizar contenedores y emplear la tecnología Kubernetes mediante el uso de la infraestructura como código.

- Descentralizar la gobernanza, popularizada por Amazon. Esto promueve la innovación y la rapidez de comercialización.

- Descentralizar DevOps y permitir que cada equipo tenga su propio proceso con las diversas herramientas de autoservicio. Centralizar las herramientas no ayuda.

- Descentralizar la gestión de datos y utilizar el principio políglota para descentralizar los datos de cada microservicio. Pero hay que tener cuidado con las licencias, la dependencia de los datos, las transacciones, etc.

# Culture of Automation Principle

El principio de la cultura de la automatización (CAP) establece que es imprescindible que las organizaciones creen primero una base que favorezca la automatización. La automatización debe integrarse en la cultura de la empresa y ser plenamente aceptada en todos los niveles del negocio.

- Cambiar la mentalidad
- Crea una comunidad de automatización basada en la practica
- Ten un repositorio con un codigo compartido de automatizaciones
- Crea una mentalidad de producto, no de proyecto
- Trata la automatización como un producto, no como un proyecto
- Incluye la IA en tus procesos de automatización

# Single Source of Truth Principle

Mas que una herramienta, esto es una practica que debe agregar toda la información generada de distintas fuentes en un solo punto. En un negocio usualmente existen los silos de datos, esto nos inhibe de tomar decisiones basados en los datos.

Debemos tratar de usar todas las herramientas a nuestro alcance para poder unificar nuestros datos para tomar mejores decisiones.