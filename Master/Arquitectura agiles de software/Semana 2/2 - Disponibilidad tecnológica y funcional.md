Tags: #disponibilidad #arquitectura-de-software #atributos-de-calidad 

Como describimos [[1 - Introduccion]] sobre la disponibilidad, hablamos en todo sentido de la misma, es decir, disponibilidad de:

- Hardware (Discos duros, fuentes de poder)
- Software (Componentes)

Para calcular la posible disponibilidad de nuestro sistema, usamos:

$$ Disponibilida = \frac{MTBF}{MTBF + MTTB}$$
Donde 

- MBTB = Tiempo medio entre fallas 
- MTTB = Tiempo medio de recuperación 

Al usar esta medida, usualmente obtenemos lo que llamamos los 9 de disponibilidad 

| ***Disponibilidad*** | ***Tiempo fuera de servicio al año*** |
| -------------------- | ------------------------------------- |
| 99.0%                | 3 días con 15.6 horas                 |
| 99.9%                | 8 horas y 46 segundos                 |
| 99.99%               | 57 minutos y 34 segundos              |
| 99.999%              | 5 minutos y 35 segundos               |
| 99.9999%             | 30 segundos                           |
Esta medida de disponibilidad, aplica para la ***disponibilidad tecnológica***.

Pero para la ***disponibilidad funcional*** (Detectar fallas de componentes), esto se puede ver:

- En la vista funcional:  Componentes que detectan y corrigen fallas
- En la vista de información: Como se maneja la replicación de los datos
- En la vista de concurrencia: Unidades de procesamiento redundantes
- En la vista de despliegue: Nodos de ejecución con estrategias de respaldo
- En la vista de operación: Decisiones para favorecer la disponibilidad en los distintos entornos

Como arquitecto, debemos ***reducir la indisponibilidad funcional a todo coste***, desde la vista funcional y de información principalmente.

El arquitecto también debe buscar la ***reducción de la disponibilidad tecnológica***, desde la vista de despliegue principalmente.

