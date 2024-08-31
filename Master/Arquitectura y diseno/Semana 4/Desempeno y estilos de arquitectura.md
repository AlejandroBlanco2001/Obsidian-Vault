Tags #atributos-de-calidad #arquitectura-de-software #diseno-uml 

![[Pasted image 20240831014813.png]]

El modelo de [[N-Niveles]] favorece la escalabilidad y el desempeno de nuestro sistema, debido a:

- Unidades de software independientes y ejecutadas en paralelo
- Posibilidad de utilizar conectorees con tiempos de respuestas baja

>[!NOTE]
>Las colas de mensajeria actuales procesan cientos de miles de mensajes por segundo. Se introduce minima latencia

![[Pasted image 20240831015014.png]]

Otra ventaja que nos ofrece, es que en temas despliegue, los componentes se pueden ejecutar en nodos de computacion separados o en uno mismo.

![[Pasted image 20240831015114.png]]

De igual manera nos permite escalar de manera horizontal (mas nodos de ejecuccion)

![[Pasted image 20240831015146.png]]

O de manera vertical (mas fuerza de computo)

![[Pasted image 20240831015204.png]]