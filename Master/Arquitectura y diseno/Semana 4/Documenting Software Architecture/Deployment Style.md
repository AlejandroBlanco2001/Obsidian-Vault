Tags #arquitectura-de-software #design #diseno-uml #alocacion

En este estilo, los elementos de la vista de C&C son permitidos para ser asignados a nuestro hardware de la plataforma de computo donde se ejecuta el software.

Una asignacion valida asegura que los requerimientos exrepsados por los elementos de software son satisfechos por el hardware.

![[Pasted image 20240830235024.png]]
# Elementos, relaciones y propiedades

Algunos de los elementos son los componentes usados en la vista de C&C. Estos se asume que se corren en una pieza de computo en algun computaador, por ende, los elementos nativos de este son piezas de computo como:

- Procesos
- Hilos
- Puertos
- Memoria

En este caso la mayoria de las relaciones son formas especiales de los conectores ***allocated-to*** , estas pueden ser dinamicas, es decir, pueden cambiar mientras el sistema se ejecuta.

- Migrates-to: Relación de un elemento de software en un procesador con el mismo elemento de software en un procesador diferente, esta relación indica que un elemento de software puede moverse de un procesador a otro pero no existe simultáneamente en ambos procesadores. 
	
- Execution-migrates-to: Similar a las dos anteriores, esta relación indica que la ejecución se desplaza de un procesador a otro, pero que la residencia del código no cambia. Una copia de un proceso existe en más de un procesador, pero sólo uno está activo en un momento dado. La ejecución del proceso «migra» cuando se cambia el proceso activo

Las propiedas importantes son las propiedas intrinsecas del hardware y como afectan al software. Como satisface esto la necesidad del software. Propiedas asignadas al hardware:

- Propieedades del CPU
- Propiedades de la memoria
- Disk o almacenamiento
- Ancho de banda
- Tolerencia al fallo

Propieadades de los sistemas de software

- Consumo de recursos
- Restricciones y requisitos del recuros
- Seguridad critica

Propiedades relevantes:
- Migration trigger: Si la asignacion cambia en tiempo de ejeccucion, se debe especificar el que la invoca.

# Beneficios 

Una vista de despliegue ayuda a analizar el ***rendimiento***, la ***disponibilidad***, la ***confiabilidad*** y la ***seguridad***. Apoya a los testers en la comprensión de las dependencias y a los integradores en la planificación de la integración. El rendimiento puede mejorarse optimizando la asignación del software al hardware, reduciendo cuellos de botella y equilibrando la carga de trabajo. La disponibilidad y la confiabilidad se mejoran gestionando fallos mediante la duplicación o migración de componentes. La seguridad se refuerza limitando servicios, utilizando firewalls y protecciones físicas. Las arquitecturas modernas buscan mantener flexible el despliegue, garantizando que los cambios no requieran modificaciones en el código. Sin embargo, los arquitectos deben evitar hacer suposiciones rígidas sobre el despliegue.

# Diagrama 

![[Pasted image 20240831010742.png]]

Una vista de despliegue en UML, que muestra la plataforma de hardware que soporta un sistema Java EE. La dependencia deploy muestra qué artefactos se despliegan en qué nodos. Entorno de ejecución es un nodo que ofrece un entorno para ejecutar tipos específicos de componentes. Para saber qué componentes se despliegan en un nodo específico, es necesario consultar la vista de instalación para ver qué componentes van dentro de cada artefacto.

Traducción realizada con la versión gratuita del traductor DeepL.com