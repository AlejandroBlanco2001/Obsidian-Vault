Tags: #cloud #CasoEstudio 

>[!TIP]
>Moverse a microservicios (o usarlos) es una tarea exigente, y mientras estas en el proceso estaras mucho tiempo en la parte de DevOps y Support.

Pinterest es una aplicación que nos permite tener un moto de navegación visual.
- Pin: Es una marca de algo que te gusta (bookmark)
- Board: Colección de ideas

Ellos cuenta con:
- 200M de usuarios por mes
- 100B+ de pines
- 3B+ de boards
- 10B+ de recomendaciones por día
- 450+ ingenieros

# Alguna de las funcionalidades
## Recomendaciones al home
> Contenido fresco, basado en contexto y relevante, pasando de 10B de pins a 5K pins.

Algunos de los desafíos fueron: 
- Recorrer el grafo (Boards -> Pins)
- Elección de candidatos
- Puntuar y entregar entre billones de objetos.

Como resultado de esto se obtuvo:
- Random Walks
- Mas conexiones = Mas puntaje
- 100k pasos < 50ms

## Visual Search
> Define la similitud visual entre objetos dentro de un PIN. Esto aplica en sistemas estáticos como imagenes o basados en tiempo real

# Infraestructura general 

![[Pasted image 20250402171134.png]]

Podemos dividir esto como:
- Izquierda -> Lógica de negocio
- Derecha -> Analítica

Alguna de las métricas que tienen de su aplicación puede ser:
- 1M de peticiones por segundo
- 175PB de datos
- 10^4 servidores
- 10^3 servicios

Ellos cuenta con una carga bastante distinta donde Django y los microservicios hacen una parte, y por otro lado, cuentas con el tema de analíticas.

# Plataforma de computo como unificadora
> Manera mas rápida de llevar una idea a producción, sin preocuparme de la infraestructura

Se partieron en varios principios:
- Simplificar la experiencia de los desarrolladores a la mitad de e2e.
- Estructura de infraestructura integrada
- Gobernanza de la infraestructura

## Developer XP
Para muchos desarrolladores el flujo de trabajo es:

- Code
- Test
- Build
- Deploy & Delivery
- *Operate* (Compleja y requiere mucho contexto)

Esto se reduce a fomentar los siguientes pasos a través de las herramientas de UI/CLI/API de nuestra plataforma integrada de desarrollo interno:

![[Pasted image 20250402172355.png]]

# Transición a microservicios
> Siempre recuerda que la adopción de las tecnologías nuevas a un nuevo grupo, siempre influye en su estado anímico, siempre hay que entender al equipo de desarrollo.

## Orquestación
Para el tema de la orquestación se tomaron en cuenta muchos parámetros como:
- Coste de integración
- Escalabilidad
- Recursos y asignación de tareas
- Soporte
- etc...

## Adopción de K8S
Para adoptar esta tecnología necesitamos saber las siguientes cosas:

- On Call / Soporte
	- ![[Pasted image 20250402174444.png]]
- App Tooling
	- ![[Pasted image 20250402174403.png]]
- Platform
	- ![[Pasted image 20250402174758.png]]
	- ![[Pasted image 20250402174034.png]]
- Cluster  
	- ![[Pasted image 20250402173608.png]]

