Tags #arquitectura-de-software #tacticas-arquitectura

Al momento de desarrollar una arquitectura podemos explorar que para potenciar nuestros atributos de calidad, seguimos una serie de decisiones desde un punto de alto nivel a un enfoque mas granular.

- Estilos de Arquitectura: Define el comportamiento general de nuestro sistema, donde dejamos plasmado la comunicacion entre nuestros elementos arquitectonicos.

- Tacticas de Arquitectura: Para potenciar nuestros atributos, necesitamos tomar ciertas decisiones sobre nuestros estilos (que modifican la arquitectura). Esta decision es mas granular 

- Patrones de diseno: Directo al codigo


En este caso, estudiaremos dos:

- Acceso a los recursos
	Dar prioridad sobre recursos limitados a aquellos eventos que requieren ser tratatdos en un menor tiempo

- Incremento de recursos
	Evitar lucha de recursos, generando mas recursos 

## Acceso a los recursos 

- Manejar la rata de muestreo
- Limitar la respuesta de eventos
- Dar prioridad a los eventos 
- Reducir el overhead
- Limitar tiempo de ejecuccion

## Incremento de recursos

- Incremento de recursos
- Introduccir concurrencia 
- Manejo copia de computacion
- Manejo copias de datos 
- Planificar el uso de recursos

