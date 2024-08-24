Un solo diagrama no puede mostrar nuestra arquitectura a todo el mundo, puesto que, no puede encapsular todo en un solo momento.

De igual manera, los intereses de las personas involucradas no necesitan tener la misma visualizacion necesaria.

Por eso nacen los puntos de ***vista de arquitectura***, estas son plantillas que ayudan a identificar los principales modelos de arquitectura para poder expresar a nuestro cliente nuestras decisiones de arquitectura relevantes para el.

>[!IMPORTANT]
> Basicamente nos permite generar un diagrama para cada tipo de interesado en nuestro proyecto, de esta manera, podemos resolver sus necesidades

Existen ***catalogos de punto de vista*** que nos permite contestar a la pregunta de cuantos necesitamos

>[!NOTE]
> En este curso tomaremos como referencia los propuestos por Rozanski, y son: Despliegue, Concurrencia, Operacion, Desarrollo, Informacion, Funcional y Contexto.

Sin embargo, para propositos del curso, usaremos solo 3:  Funcional, Despliegue y Concurrencia

| Punto de vista | Definicion                                                                                                                                | Ilustra                                                                |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Funcional      | Ayuda al arquiecto a describiri los elementos funcionales, presentar las interfaces ofrecidas y relacion e interaccion de los componentes | Filosofia de arquitectura seguida por el arquitecto                    |
| Despliegue     | Como seran desplegados los componentes indicados en la vista funcional.                                                                   | Nos permite ver servidores, canales de comunicacion y  almacenamiento. |
| Concurrencia   | Nos permite describir la estrategia de ejecuccion de los componentes en el punto de vista funcional                                       | Hablamos de la comunicacion entre hilos y procesos.                    |
