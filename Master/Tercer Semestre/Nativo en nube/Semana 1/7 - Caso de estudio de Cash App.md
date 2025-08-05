---
tags:
  - cloud
  - arquitectura-de-software
  - master
LInk: https://learning-oreilly-com.ezproxy.uniandes.edu.co/videos/how-square-scaled/0636920459774/0636920459774-video329996/
---
## Introducción

- Cash App es una empresa que permite el envió y recibimiento de dinero
- Cash App empezó como un proyecto sin fe, donde tenían únicamente una base de datos MySQL
	- Con el tiempo, esta se fue inflando hasta que exploto y como la escalaron 
- Contaban con lo siguiente:
	- 40 ingenieros
	- 5 anos de trabajo
	- 500k líneas de codigo
	- 200 tablas de MySQL
- Algunas de las alternativas que se usaron fueron:
	- Load shedding, donde podían rechazar el 10% de la carga y recibir el 90%
	- Modo "Offline" para poder guardar las peticiones dentro del teléfono hasta que el servidor estuviera arriba de nuevo, pero podia causar retrasos en las transferencias
	- Mover algunas tablas a bases de datos orientadas en llave-valor
	- Capa de cache y lecturas en replicas
		- Lecturas  en base de datos era mas eficiente para el caso movil
	- Todo lo antes descrito solucionaba era el tamaño de los datos (*data size*) y el rendimiento de lectura (*read throughput*)
- Pero el verdadero problema apareció cuando encontraron problemas con el rendimiento de escritura (*write throughput*), para solucionar esto puedes:
	- Comprar mas hardware
	- Romper el monolito, y luego tener cada uno su base de datos
	- *Sharding*, donde cuentas con un esquema compartido entre las bases de datos y luego cada una es una partición
- Decidieron hacer sharding

## Sharding
 - Debemos poder partir nuestra base de datos en varios shards
- Debemos tener un buen mecanismo para mandar las peticiones a su shard correspondiente
- Problemas de Cross-Shard donde no sabíamos que no podíamos tener todo los datos en un shard, entonces debemos poder manejar la búsqueda entre ellos
- Optaron por usar Vitess donde el se encarga del manejo d e multiples instancias de bases de datos MySQL
- 
![[Pasted image 20250804223207.png]]