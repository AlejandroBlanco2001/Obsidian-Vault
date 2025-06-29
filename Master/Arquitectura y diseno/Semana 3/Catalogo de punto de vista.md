---
tags:
  - arquitectura-de-software
  - diseno-uml
  - master
---
Que vistas debe incluir una arquitectura (Catalogo de puntos de vista) depende del proyecto a utilizar y sus necesidades:

- 4+1 (Krutchan)
- Views and beyonds (Clements)
- Views and perspectives (Rozanski & Woods)

Rozanski & Woods proponen 7 punto de vistas 

| Punto de vista | Proposito                                                                                                                                                              | Objetivos                                                                                                                                                                                  | Dirigdo                                                       |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------- |
| Contexto       | Describir las relaciones, dependencias e interacciones entre el sistema y su ambiente<br><br>- Personas<br>- Sistemas<br>- Entidades externas                          | - Definir el alcance y responsibilidades<br>- Identificar entidades externas<br>- Identificar medios de interaccion<br>- Impacto del sistema en el ambiente                                | Todos, especialmente desarrolladores                          |
| Funcional      | Describir como funciona el sisetma                                                                                                                                     | - Describir la capacidad funcional del sistema<br>- Definir las interfaces externas del sistema<br>- Definir las estructuras internas del sistema<br>- Dejar claro la filosofia del diseno | Todos                                                         |
| Informacion    | Describir la forma en que el sistema almacena la infromacion                                                                                                           | - Presentar la estructura y contenido de la informacion<br>- Uso y proposito de la informacion<br>- Presentar flujos de informacion<br>- Evaluar la calidad de infromacion                 | Administradores de base de datos y arquitectos de informacion |
| Concurrencia   | Describir la estructura de concurrencia del sistema y relaciona elementos funcionales con uniades de concurrencia:<br><br>- Hilos<br>- Procesos<br>- Grupo de procesos | - Definir la estructura de tareas<br>- Relacionar elementos funcionales<br>- Manejo de estado<br>- Sincronizacio e integridad<br>- Escalabilidad<br>- Manejo de fallas                     | Desarrolladores y administradores de infraestructura          |
| Desarrollo     | Como soporta la arquitectura el proceso de desarrollo                                                                                                                  | - Organizacion modular<br>- Procesamiento comun<br>- Estandirzacion en el diseno <br>- Organizacion del codigo                                                                             | Desarrolladores                                               |
| Despliegue     | Describir el ambiente en el cual el sistema sera desplegado                                                                                                            | - Plataforma de ejecucion requerida<br>- Especificacion y cantidad de hardware <br>- Compatiblidad tecnologica                                                                             | Administradores de intraestructura                            |
| Operacion      | Como opera el sistema y como sera administrado el sistema                                                                                                              | - Implicaciones del diseno en el mantenimiento y funcionamiento del sistema                                                                                                                | Administradores de intraestructura                            |
