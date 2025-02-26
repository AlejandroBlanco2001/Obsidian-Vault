Tags: #arquitectura-de-software #disponibilidad #atributos-de-calidad 

## Monitor
Para este caso se crea un componente externo que actúa como un monitor, que de periódicamente este siendo notificado del estado de salud de los otros micro-servicios .

![[Pasted image 20250215191903.png]]

## Votación
Se puede implementar igual que en el caso sincrónico (Ver [[3 - Tácticas para disponibilidad]]), en este caso, es un componente que se comunica a través de la cola de mensajería

![[Pasted image 20250215192040.png]]

## Separación de responsabilidad
También podemos manejar unas colas para asignarse los comandos y otras para asignarse las consultas.
