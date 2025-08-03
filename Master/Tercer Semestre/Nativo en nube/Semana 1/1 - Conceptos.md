---
tags:
  - cloud
  - master
---
# Contenerización 
Partamos de una ***infraestructura como servicio*** (IaaS), donde tomamos las ventajas de la ***virtualización***, esto nos permite tener sobre UNA infraestructura correr MULTIPLES maquinas virtuales

> En este caso, recordemos que las capas se denominan de la siguiente manera:
> 1. Aplicaciones
> 2. Datos
> 3. E ntornos de ejecución
> 4. Middleware
> 5. S.O
> 6. Virtualización
> 7. Servidores
> 8. Almacenamiento
> 9. Red
> Donde el proveedor se encarga del 9 al 6, y nosotros del 5 al 1

Recordemos que nuestras maquinas virtuales son finitas y limitadas, por ende, podemos realizar:
- Escalamiento horizontal: Mas maquinas, usualmente mas barato
- Escalamiento vertical: Agregar mas recursos, usualmente mas caro

Tambien hay que tener en cuenta que los contenedores tienen también problemas como cualquier modelo de despliegue, pero que es un contenedor:

> [!INFO]
> Paquete de software **ejecutable, ligero y portable** que contiene todas las dependencias, archivos y elementos necesarios para la ejecución de una aplicacion.

Muy importante es recordar que contenedores y maquinas virtuales no son lo mismo, son conceptos relacionados pero no iguales
- Contenedores
	- Uso del kernel del sistema operativo anfitrión para todos los contenedores y sus aplicaciones
- Maquinas virtuales
	- Sistema operativos autónomos que gestionan su propio kernel

![[Pasted image 20250803175158.png]]

Recordemos que los contenedores al ser aislados, tenemos capacidad de modificarlos de manera autónoma.
# Cohesion
Podemos usar un objeto como una navaja suiza para entender este concepto, donde esta *tiene muchas funciones* (responsabilidades), y esta sirve para muchas cosas.

Pero, si lo pensamos, esta no es *cohesiva*, debido a que cuenta con *demasiadas funciones* y que *no estan relacionadas* entre si, es decir, no podemos contestar la pregunta: Que hace la navaja?

>[!IMPORTANT]
> La pregunta de, ***Que hace?*** es el principal medidor de la cohesion

Podemos definir la cohesion como una medida que indica *cuan relacionadas estan las responsabilidades* de un elemento de software.

- Alta cohesion: Mas relacionadas estan las responsabilidades -> Mas facil de entender

# Acoplamiento
La medida de *cuanto un componente de software esta conectado* (tiene conocimiento) de otros componentes. Cuanto mas sea el conocimiento de un sobre otro, esto se llama *alto acoplamiento*, lo que puede generar algo muy perjudicial para nuestro sistema.
- Dificultad al entender el sistema
- Cambiar el sistema es mas complejo
- El impacto del cambio es algo mas difícil de estimar

> [!INFO]
> Otra forma de ver el acoplamiento es, se encarga de determinar el efecto que tendrá un cambio de un elemento de software sobre otro elemento.

Debemos considerar que a veces el acoplamiento *debe existir*, pero siempre debemos tratarlo de tenerlo *en la menor medida posible*

> [!IMPORTANT]
> Siempre queremos un bajo acoplamiento y una alta cohesion

# Sistemas distribuidos
Se define como:

 > Sistema en el cual diversas maquinas de computo conectadas a través de la red se presentan como una sola maquina 

Al distribuir el poder de computo en diversas maquinas se benefician *la escalabilidad*, *la disponibilidad*, *la tolerancia a fallos* y *los costos*.

Algunas de las falacias que consideramos que puede traer problemas son:
- La red es confiable
- La red es homogénea
- La red es segura
- La latencia entre componentes cero
	- Debe pensarse en la cercanía a la información
- Hay ancho de banda infinito
- La topología no cambia
	- IP's estáticas
- Hay un administrador
- Costo de transporte es cero
	- Costo económico
	- Costo en latencia; serializar, deserializar
# Monorepo y Multirepo
Un aspecto importante a la hora de desarrollar también es como *organizamos nuestro codigo fuente*, donde tenemos dos grandes vertientes: monorepo y mutlirepo

En un *multirepo* (o polirepo), contemplamos tener un repositorio distinto por proyecto, servicio o componente, cada uno siendo administrado y versionado de manera independiente

```
git
/auth-service
├── src/
├── tests/
└── README.md

git
/billing-service
├── src/
├── tests/
└── README.md

git
/ui-components-repo
├── src/
├── examples/
└── README.md
```

Alguna de las ventajas de esta manera puede ser:
- Autonomía total para equipos, que pueden definir su ciclo de vida de forma independiente.
- Versionamiento individualizado, lo que permite liberar cada componente cuando esté listo.
- Aislamiento claro de responsabilidades, facilitando la gobernanza y control de acceso.
- Menores riesgos en los procesos de mezcla y construcción de los componentes.
- Procesos de code review y pruebas más sencillos.

y tambien tenemos problemas como:
- Coordinación de cambios más difícil, especialmente cuando hay dependencias entre proyectos.
- Requiere mayor esfuerzo para mantener consistencia de estilo y configuración entre repositorios.
- Duplicación de código o configuraciones comunes, si no se usan paquetes compartidos bien mantenidos.
- Incrementos en la gestión de todos los repositorios por parte de los equipos. Es más difícil tener una vista clara y completa de todo el código, sus dependencias y su calidad.
- Comunicación y colaboración entre equipo puede ser más difícil dado que los equipos normalmente trabajan en silos.

Por otro lado, tenemos el otro enfoque de *monorepo*, donde mantenemos todos nuestros servicios, proyectos o componentes en un mismo repositorio

```
git
/my-system
├── users-service/         ← servicio de usuarios
│   ├── terraform/         ← infrastructura de la aplicación
│   └── src/               ← código de la aplicación
├── pets-service/           ← servicio de mascotas
│   ├── terraform/         ← infrastructura de la aplicación
│   └── src/               ← código de la aplicación
├── libs/
│   └── auth-utils/        ← Librería compartida para autenticación
└── infrastructure-cross/  ← Módulo de infrastructura para todos los proyectos

```

Entre las ventajas de usar este enfoque se encuentran:
- Facilidad para realizar cambios coordinados entre múltiples proyectos.
- Reutilización de código y facilidad para identificar dependencias entre proyectos. Lo que permite evaluar de mejor forma el impacto de un cambio.
- Consistencia en configuraciones y convenciones a través de todo el repositorio.
- Revisión de código más contextualizada, ya que todo vive en el mismo lugar.
- Mejora la colaboración y comunicación entre equipos, dado que se ve fácilmente en que están trabajando todos los equipos.

Y entre sus desventajas se encuentran:
- Puede generar problemas de rendimiento en grandes escalas (repositorios con millones de líneas de código).
- Requiere herramientas especializadas o procesos correctamente definidos para gestionar cambios, dependencias y procesos de CI/CD.
- Cambios pequeños pueden generar grandes ciclos de CI si no se optimiza correctamente.
- Dificultad para asegurar que todos los cambios están correctamente probados y revisados.
# Documentación como codigo
Dentro del mundo del desarrollo, hay una falencia muy grave que es la *documentacion*, muchas veces la unica manera de saber como las cosas funcionan es ver las cosas con tus ojos o buscar documentacion que probablemente este desactualizada.

Por ende nace una filosofía llamada DaC (Documentation as Code), donde nuestra documentación sufre los mismos procesos, efectos y rigurosidad como:

- Llevar versionamiento y trazabilidad de la documentación, lo que implica que cada cambio en la documentación puede ser trazado, comentado y revertido al igual que el código. Además, permite identificar cual es la documentación asociada a una versión en específica de código.
- Tener control de manera colaborativa por medio de pull y merge requests que son comentados y aprobados por pares.
- Automatizar las actividades de documentación tales como: la validación del contenido, detección de enlaces rotos, generación de documentación, y actualización y publicación continua.
- Empoderar a cada miembro del equipo en la gestión de la documentación dado que hacen uso de las mismas herramientas (git) y formatos ya conocidos (Markdown) por ellos.

Profundizar con lecturas [[Write the Docs - DaC]], [[What is Docs as Code, Your Guide to Modern Technical Documentation]] y [[Five fast facts about docs as code at GitLab]]
