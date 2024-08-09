>[!IMPORTANT]
> El hecho de que podamos escribir un libro sobre arquitectura, no solo relata lo importante que es, sino la cantidad de informacion que tenemos de ella

El principio basico de cualquier arquitectura debe ser tener la capacidad de suplir una necesidad de negocio. Y que su funcionalidad es ser un puente entre las metas del negocio y el sistema en si

La arquitectura puede ser disenada, analizada y documenta.

> Una arquitectura de software son las estructuras necesarias para razonar sobre el sistema. Estas estructuras comprenden elementos de software, relaciones entre ellos y propiedades.

>[!IMPORTANT]
>La arquitectura consiste en estructuras que permiten razonar.

# Arquitectura es el conjunto de estructuras de software

Estas estructuras pueden ser clasificadas en:

1. Componentes y connectores
2. Modulos
3. Asignacion

Toda estructura de software, no es necesariamente, una estructura arquitectonica

Podemos definir un componente de arquitectura, si este nos permite razonar sobre el sistema y sus propiedades. Este razonamiento habla sobre la importancia para un cliente. y funcionalidades como:

- Funcionalidad del sistema
- Manejo de caidas y errores
- Dificultad para realizar los cambios 
- Responsividad al usuario

# Una arquitectura es una abstraccion

Una arquitectura es de alto nivel, por ende, omite algunos detalles que no hablan del sistema en general.


## Arquitectura vs Diseno

>[!IMPORTANT]
>Toda arquitectura es un diseno, pero no todo diseno es una arquitectura

## Todo sistema de software, tiene un arquitecto

El simple hecho de que un sistema tenga una arquitectura, porque todo sistema tiene elementos y relaciones, sin embargo, puede ser que el arquitecto no sea alguien en particular.

Hay que entender la diferencia entre ***la arquitectura del sistema*** y su ***representacion***


## Arquitecturas malas? Si, si hay

Aunque esto suene pragmatico, hay que verlo desde el punto de vista que toda arquitectura no aborda un problema de la mejor manera

Nunca debemos escoger una al azar, debe disenarse y pensarse

## Arquitectura y comportamiento

Cada elemento dentro de una arquitectura se comporta de una manera, por esto, podemos razonar sobre como funciona, como interactuan con otros

## Arquitectura de un sistema

Es la representacion de un sistema en la que hay un mapeo entre hardware, software e interaccion humana.

- Arquitectura del software
	Esta nos permite razonar sobre la calidad, desempeno de nuestro programa
- Arquitectura del hardware
- Como los humanos interactuan con ella

Podemos razonar sobre consumo de energia, peso y dimensiones de las cosas tangibles.

## Arquitectura empresarial

Es la descripcion de la estructura y comportamiento de los procesos de una organizacion, personal y sus unidades.

>[!IMPORTANT]
>Hoy en dia es **necesario** integrar las capacidades del sistema de informacion en esta descripcion

Cosas como:

- Como se comunica con otros sistemas
- El modelado de datos que usa
- Como se usa el software por el personal
- Estandares para los equipos

# Estructuras arquitectonicas y vistas

Todos los sistemas del cuerpo (nervioso, cardiovascular, respiratorio..) son una **vista** de la arquitectura humana

## C&C (Componente-y-conector)

**Enfoque**: Se enfoca en mostrar como los elementos se comunican y actuan entre si para la ejeuccion del sistema

- Comportamientos (Componentes)
- Interacciones (Conectores)

Los componentes son ***unidades basicas de computacion***:
- Servicios
- Clientes
- Servidores
- Filtros

Los conectores son ***herramientas de comunicacion***:
- Call-Return
- Procesos de sincronizacion
- Pipes
- Operadores

**Proposito de las estructuras C&C**: Responde a preguntas como:

- ¿Cuáles son los principales componentes de ejecución y cómo interactúan en tiempo de ejecución?
- ¿Cuáles son los principales almacenes de datos compartidos?
- ¿Qué partes del sistema están replicadas?
- ¿Cómo avanzan los datos por el sistema?
- ¿Qué partes del sistema pueden ejecutarse en paralelo?
- ¿Puede cambiar la estructura del sistema durante su ejecución y, en caso afirmativo, cómo?


![[Pasted image 20240808235633.png]]


## Modulos

**Enfoque:** Dividen los sistemas en unidades de implementación llamadas módulos.

- **Propósito de los Módulos**: Muestran cómo un sistema está estructurado en unidades de código o datos que deben ser construidas o adquiridas.
- **Responsabilidades**: Los módulos tienen responsabilidades computacionales específicas y son la base de asignaciones de trabajo para equipos de programación.
- **Tipos de Módulos**: Pueden ser clases, paquetes, capas u otras divisiones de funcionalidad, todas consideradas como unidades de implementación.
- **Visión Estática**: Los módulos representan una forma estática de considerar el sistema, enfocándose en áreas de responsabilidad funcional más que en cómo el software se manifiesta en tiempo de ejecución.
- **Implementación de Módulos**: Incluye paquetes, clases y capas.
- **Relaciones entre Módulos**: Incluyen "usa", generalización ("es-un"), y "es parte de".

![[Pasted image 20240808235911.png]]

![[Pasted image 20240808235930.png]]

**Proposito de las estructuras de Asignacion**: Responder las siguientes preguntas: 

- ¿Cuál es la responsabilidad funcional principal asignada a cada módulo?

- ¿Qué otros elementos de software puede utilizar un módulo?

- ¿Qué otro software utiliza realmente y del que depende?

- ¿Qué módulos están relacionados con otros mediante relaciones de generalización o especialización (es decir, herencia)?

## Asignacion

-Establecen la relación entre las estructuras de software y las estructuras no software del sistema, como la organización, o los entornos de desarrollo, prueba y ejecución.

- **Propósito de las Estructuras de Asignación**: Responden a preguntas clave como:
    - ¿En qué procesador(es) se ejecuta cada elemento de software?
    - ¿En qué directorios o archivos se almacena cada elemento durante el desarrollo, las pruebas y la construcción del sistema?
    - ¿Cuál es la asignación de cada elemento de software a los equipos de desarrollo?

## Ejemplos utiles de modulos

### Decomposicion

- **Estructura de Descomposición**: Las unidades son módulos relacionados por la relación "es-un-submódulo-de", mostrando cómo los módulos se descomponen en submódulos más pequeños, recursivamente, hasta que sean lo suficientemente pequeños para ser comprendidos fácilmente.
- **Propósito Inicial**: Los módulos en esta estructura representan un punto de partida común para el diseño, donde el arquitecto enumera lo que cada unidad de software debe hacer y asigna cada tarea a un módulo para su diseño detallado y eventual implementación.
- **Productos Asociados**: Los módulos a menudo tienen productos asociados, como especificaciones de interfaces, código y planes de prueba.
- **Impacto en la Modificabilidad**: La estructura de descomposición influye significativamente en la modificabilidad del sistema, determinando si los cambios pueden limitarse a unos pocos (preferiblemente pequeños) módulos.
- **Organización del Proyecto**: Esta estructura se utiliza como base para la organización del proyecto de desarrollo, incluyendo la estructura de la documentación, y los planes de integración y prueba del proyecto.

![[Pasted image 20240809000416.png]]

---
### Uso

- **Estructura de Uso**: En esta estructura, que es importante pero a menudo pasada por alto, las unidades también son módulos y quizás clases.
- **Relación de Uso**: Las unidades están relacionadas por la relación de uso, una forma especializada de dependencia. Un software utiliza otro si la corrección del primero requiere la presencia de una versión funcional (no un stub) del segundo.
- **Propósito de la Estructura de Uso**: Se utiliza para diseñar sistemas que puedan ser extendidos para agregar funcionalidad o de los cuales se puedan extraer subconjuntos funcionales útiles.
- **Desarrollo Incremental**: La capacidad de crear fácilmente un subconjunto de un sistema permite el desarrollo incremental.
- **Deuda Social**: Esta estructura también sirve como base para medir la deuda social—la cantidad de comunicación que realmente ocurre, en comparación con la que debería estar ocurriendo, entre los equipos—ya que define qué equipos deberían estar comunicándose entre sí.

![[Pasted image 20240809000548.png]]

### Capas 

- **Estructura de Capas**: Los módulos en esta estructura se llaman capas.
- **Definición de Capa**: Una capa es una "máquina virtual" abstracta que proporciona un conjunto cohesivo de servicios a través de una interfaz gestionada.
- **Uso entre Capas**: Las capas pueden utilizar otras capas de manera controlada; en sistemas estrictamente en capas, una capa solo puede utilizar una única capa adicional.
- **Portabilidad del Sistema**: Esta estructura otorga al sistema portabilidad, es decir, la capacidad de cambiar la máquina virtual subyacente.
-
![[Pasted image 20240809000740.png]]

---
### Clases

- **Estructura de Clases (o Generalización)**: Los módulos en esta estructura se llaman clases.
- **Relaciones entre Clases**: Las clases están relacionadas mediante una relación de "hereda-de" o "es-una-instancia-de".
- **Propósito de la Estructura de Clases**: Esta vista permite razonar sobre colecciones de comportamientos o capacidades similares y diferencias parametrizadas.
- **Reuso y Funcionalidad Incremental**: La estructura de clases facilita el razonamiento sobre la reutilización y la adición incremental de funcionalidad.
- **Documentación Orientada a Objetos**: Si existe documentación de un proyecto que haya seguido un proceso de análisis y diseño orientado a objetos, generalmente se refiere a esta estructura.

![[Pasted image 20240809000901.png]]

---
### Modelo de datos

- **Modelo de Datos**: Describe la estructura de información estática en términos de entidades de datos y sus relaciones.
- **Ejemplo de Entidades**: En un sistema bancario, las entidades típicas incluyen Cuenta, Cliente y Préstamo.
- **Atributos de las Entidades**: Por ejemplo, la entidad Cuenta puede tener atributos como número de cuenta, tipo (ahorros o cheques), estado y saldo actual.
- **Relaciones entre Entidades**: Una relación puede establecer que un cliente puede tener una o más cuentas, y una cuenta está asociada con uno o más clientes.

![[Pasted image 20240809000955.png]]


## Ejemplos utiles de C&C

1. **Estructura de Servicios**: Las unidades en esta estructura son servicios que interoperan a través de un mecanismo de coordinación de servicios, como mensajes.
2. **Propósito de la Estructura de Servicios**: Es importante para diseñar un sistema compuesto de componentes que pueden haber sido desarrollados de manera independiente.

---

1. **Estructura de Concurrencia**: Esta es una estructura C&C (Componentes y Conectores) que permite al arquitecto identificar oportunidades de paralelismo y localizar dónde puede ocurrir la contención de recursos.
2. **Componentes y Conectores**: Las unidades son componentes, y los conectores son sus mecanismos de comunicación.
3. **Hilos Lógicos**: Los componentes se organizan en "hilos lógicos", que son secuencias de cálculos que podrían asignarse a un hilo físico separado más adelante en el proceso de diseño.
4. **Propósito de la Estructura de Concurrencia**: Se utiliza al inicio del proceso de diseño para identificar y gestionar problemas relacionados con la ejecución concurrente.

## Ejemplos de Asignacion

### Estructura de Despliegue

1. **Propósito**: Muestra cómo el software se asigna a elementos de hardware para procesamiento y comunicación.
2. **Elementos**: Incluye elementos de software (generalmente un proceso de una estructura C&C), entidades de hardware (procesadores) y vías de comunicación.
3. **Relaciones**:
    - **"Asignado a"**: Indica en qué unidades físicas residen los elementos de software.
    - **"Migra a"**: Si la asignación es dinámica.
4. **Uso**: Permite razonar sobre el rendimiento, integridad de datos, seguridad y disponibilidad, especialmente en sistemas distribuidos.
5. **Interés Especial**: Es clave para lograr el atributo de calidad de desplegabilidad.

![[Pasted image 20240809001204.png]]

---

### Estructura de Implementación

1. **Propósito**: Muestra cómo los elementos de software (generalmente módulos) se asignan a las estructuras de archivos en los entornos de desarrollo, integración, prueba o control de configuración del sistema.
2. **Importancia**: Es crucial para la gestión de actividades de desarrollo y procesos de construcción.

---

### Estructura de Asignación de Trabajo

1. **Propósito**: Asigna la responsabilidad de implementar e integrar los módulos a los equipos que llevarán a cabo estas tareas.
2. **Implicaciones**: La estructura de asignación de trabajo tiene tanto implicaciones arquitectónicas como de gestión, clarificando las decisiones sobre quién hace el trabajo.
3. **Conocimiento del Arquitecto**: El arquitecto sabrá la experiencia requerida en cada equipo.
4. **Ejemplo de Amazon**: La decisión de Amazon de asignar un equipo único a cada uno de sus microservicios es un ejemplo de una estructura de asignación de trabajo.
5. **Gestión de Proyectos Grandes**: Es útil identificar unidades de funcionalidad común y asignarlas a un solo equipo, en lugar de que sean implementadas por todos los que las necesiten.
6. **Vías de Comunicación**: Esta estructura también determinará las principales vías de comunicación entre los equipos, como conferencias web regulares, wikis, listas de correo, etc.

### Resumen 

| **Estructura de Software**    | **Tipos de Elementos**             | **Relaciones**                                              | **Útil para**                                                                                            | **Preocupaciones de Calidad Afectadas**                          |
| ----------------------------- | ---------------------------------- | ----------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| **Estructuras de Módulos**    |                                    |                                                             |                                                                                                          |                                                                  |
| **Descomposición**            | Módulo                             | Es un submódulo de                                          | Asignación de recursos, estructuración y planificación de proyectos; encapsulación                       | Modificabilidad                                                  |
| **Uso**                       | Módulo                             | Usa (es decir, requiere la presencia correcta de)           | Diseñar subconjuntos y extensiones                                                                       | "Subsetabilidad", extensibilidad                                 |
| **Capas**                     | Capa                               | Permitido usar los servicios de; proporciona abstracción a  | Desarrollo incremental; implementación de sistemas sobre "máquinas virtuales"                            | Portabilidad, modificabilidad                                    |
| **Clase**                     | Clase, objeto                      | Es una instancia de; es una generalización de               | En sistemas orientados a objetos, factorizar la comúnidad; planificación de extensiones de funcionalidad | Modificabilidad, extensibilidad                                  |
| **Modelo de Datos**           | Entidad de datos                   | {uno, muchos}-a-{uno, muchos}; generaliza; especializa      | Ingeniería de estructuras de datos globales para consistencia y rendimiento                              | Modificabilidad, rendimiento                                     |
| **Estructuras C&C**           |                                    |                                                             |                                                                                                          |                                                                  |
| **Servicios**                 | Servicio, registro de servicios    | Adjunción (vía paso de mensajes)                            | Análisis de planificación; análisis de rendimiento; análisis de robustez                                 | Interoperabilidad, disponibilidad, modificabilidad               |
| **Concurrencia**              | Procesos, hilos                    | Adjunción (vía mecanismos de comunicación y sincronización) | Identificación de ubicaciones donde existe contención de recursos, oportunidades de paralelismo          | Rendimiento                                                      |
| **Estructuras de Asignación** |                                    |                                                             |                                                                                                          |                                                                  |
| **Despliegue**                | Componentes, elementos de hardware | Asignado a; migra a                                         | Mapear elementos de software a elementos del sistema                                                     | Rendimiento, seguridad, energía, disponibilidad, desplegabilidad |
| **Implementación**            | Módulos, estructura de archivos    | Almacenado en                                               | Control de configuración, actividades de integración y pruebas                                           | Eficiencia en el desarrollo                                      |
| **Asignación de Trabajo**     | Módulos, unidades organizacionales | Asignado a                                                  | Gestión de proyectos, mejor uso de la experiencia y los recursos disponibles, gestión de la comúnidad    |                                                                  |

## Relacion entre las estructuras

- **Perspectivas de Diseño**: Cada estructura ofrece una perspectiva y un enfoque de diseño diferentes sobre un sistema, siendo válida y útil en su propio contexto.
    
- **Interrelación de Estructuras**: Las estructuras no son independientes; los elementos de una estructura están relacionados con los elementos de otras. Por ejemplo, un módulo en una estructura de descomposición puede manifestarse como uno, parte de uno, o varios componentes en una estructura C&C, reflejando su versión en tiempo de ejecución.
    
- **Mapeo entre Estructuras**: Generalmente, las relaciones entre estructuras son de muchos a muchos.

![[Pasted image 20240809001804.png]]

- **Ejemplo Visual**:
    
    - **Vista de Descomposición**: Muestra dos módulos (cliente y servidor) en un sistema cliente-servidor.
    - **Vista C&C**: Muestra el mismo sistema con diez clientes y un servidor en ejecución, resultando en dos módulos y once componentes (más diez conectores).
- **Uso de las Vistas**:
    
    - La vista de descomposición (izquierda) es útil para el diseño de módulos y planificación.
    - La vista C&C (derecha) es más adecuada para análisis de rendimiento, predicción de cuellos de botella y gestión del tráfico de red, tareas que serían extremadamente difíciles o imposibles con la vista de descomposición.
- **Estructura Dominante**:
    
    - Algunos proyectos consideran una estructura como dominante y ajustan otras estructuras en función de la estructura dominante.
    - La estructura de descomposición de módulos suele ser dominante, ya que refleja la estructura del equipo de desarrollo.
    - En otros proyectos, la estructura dominante podría ser una estructura C&C que muestra cómo se logra la funcionalidad del sistema y/o atributos críticos de calidad en tiempo de ejecución

## Menos es mas

- **Menos es Mejor**: No todos los sistemas requieren la consideración de muchas estructuras arquitectónicas. Para sistemas pequeños, a menudo es suficiente trabajar con menos estructuras.
    
- **Estructuras para Sistemas Pequeños**:
    
    - **C&C Única**: En lugar de utilizar varias estructuras C&C, normalmente una sola es suficiente.
    - **Estructura de Procesos**: Si solo hay un proceso, la estructura de procesos se reduce a un solo nodo y no necesita ser representada explícitamente en el diseño.
    - **Estructura de Despliegue**: Si el sistema se implementa en un solo procesador y no habrá distribución, la estructura de despliegue es trivial y no necesita considerarse más.
- **Retorno de Inversión**: Debes diseñar y documentar una estructura solo si aporta un retorno positivo de la inversión, generalmente en términos de reducción de costos de desarrollo o mantenimiento.
    
## Que estructura me sirve mas ?

- **Elegir Estructuras**: Considera cómo las diferentes estructuras proporcionan perspectiva y aprovechamiento para los atributos de calidad más importantes del sistema.
- **Documentación**: Elige las estructuras que mejor contribuyan a la entrega de esos atributos clave, no todas las estructuras disponibles.

En resumen, la elección de estructuras debe basarse en su capacidad para mejorar los atributos de calidad del sistema y aportar beneficios concretos en términos de desarrollo y mantenimiento.

## Patrones arquitectonicos

En algunos casos, los elementos arquitectónicos se combinan de maneras que resuelven problemas específicos.
    
- **Utilidad y Documentación**: Estas combinaciones han demostrado ser útiles a lo largo del tiempo y en diversos dominios, por lo que han sido documentadas y difundidas.
    
- **Definición de Patrones**: Los patrones arquitectónicos son composiciones de elementos arquitectónicos que proporcionan estrategias empaquetadas para resolver ciertos problemas en un sistema.

## Que hace "buena" a una arquitectura?

### Arquitectura Inherente
- **No hay arquitecturas inherentemente buenas o malas**: Las arquitecturas son más o menos adecuadas para propósitos específicos.
- **Contexto Importante**: Una arquitectura debe evaluarse en el contexto de objetivos específicos.

### Recomendaciones de Proceso
1. **Responsabilidad de Arquitecto**:
   - La arquitectura debe ser diseñada por un solo arquitecto o un pequeño grupo con un líder técnico identificado.
   - Esto garantiza la integridad conceptual y consistencia técnica.

2. **Requisitos de Atributos de Calidad**:
   - La arquitectura debe basarse en una lista priorizada de requisitos de atributos de calidad bien especificados.
   - Estos requisitos guiarán los compromisos que siempre ocurren, siendo la funcionalidad menos importante en comparación.

3. **Documentación de la Arquitectura**:
   - La arquitectura debe documentarse usando vistas que representen una o más estructuras arquitectónicas.
   - Las vistas deben abordar las preocupaciones de los stakeholders más importantes y pueden elaborarse a lo largo del tiempo.

4. **Evaluación de la Arquitectura**:
   - La arquitectura debe evaluarse para verificar su capacidad de entregar los atributos de calidad importantes.
   - Esta evaluación debe ocurrir temprano en el ciclo de vida y repetirse según sea necesario para asegurar que los cambios no vuelvan obsoleto el diseño.

5. **Implementación Incremental**:
   - La arquitectura debe permitir la implementación incremental para evitar la integración total de una vez y para descubrir problemas temprano.
   - Se puede utilizar un sistema "esquelético" para ejercitar los caminos de comunicación y desarrollar el sistema de manera incremental.

### Reglas Estructurales
1. **Definición de Módulos**:
   - La arquitectura debe presentar módulos bien definidos con responsabilidades funcionales basadas en el ocultamiento de información y la separación de preocupaciones.
   - Los módulos de ocultamiento de información deben encapsular aspectos que probablemente cambien, aislando el software de esos cambios.

2. **Patrones Arquitectónicos**:
   - A menos que los requisitos sean sin precedentes, los atributos de calidad deben lograrse usando patrones arquitectónicos y tácticas bien conocidos.

3. **Independencia de Productos Comerciales**:
   - La arquitectura no debe depender de una versión específica de un producto o herramienta comercial.
   - Si es necesario, la estructura debe facilitar el cambio a diferentes versiones de manera sencilla y económica.

4. **Separación de Producción y Consumo de Datos**:
   - Los módulos que producen datos deben separarse de los módulos que consumen datos para aumentar la modificabilidad.
   - La separación permite una actualización escalonada e incremental.

5. **Correspondencia Módulo-Componente**:
   - No se debe esperar una correspondencia uno a uno entre módulos y componentes.
   - En sistemas con concurrencia, múltiples instancias de un componente pueden estar en ejecución, y cada componente puede estar construido a partir de un módulo diferente.

6. **Asignación de Procesos a Procesadores**:
   - Cada proceso debe ser escrito de manera que su asignación a un procesador específico pueda cambiarse fácilmente, incluso en tiempo de ejecución.

7. **Patrones de Interacción de Componentes**:
   - La arquitectura debe presentar un número pequeño de patrones simples de interacción de componentes.
   - Esto facilita la comprensión, reduce el tiempo de desarrollo, aumenta la fiabilidad y mejora la modificabilidad.

8. **Áreas de Contención de Recursos**:
   - La arquitectura debe contener un conjunto específico (y pequeño) de áreas de contención de recursos, con resoluciones claramente especificadas y mantenidas.
   - Por ejemplo, si la utilización de red es una preocupación, se deben producir y hacer cumplir directrices para niveles aceptables de tráfico de red.