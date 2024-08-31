Tags #diseno-uml #arquitectura-de-software #design 

Recordemos que nuestra arquitectura sera usadas por humanos para humano, asi que concentrarse netamente en la arquitectura como un conjunto de software, no es un buen enfoque.

>[!IMPORTANT]\
>Recordemos que los modulos, C&C y los elementos de asignacion son parte de la arquitectura, y ***son los que nos permite razonar sobre un sistema***

Estas vistas son encargas de relacionar componentes de software, como lo son (elementos de la vista de modulos o componentes y conectores) con elementos que no son software.

Contamos con varios estilos como;

- Deployment style: Describe la relacion entre los componentes del software y conectores con el hardware de ejecuccion del programa
 
- Install style: Describe la relacion entre los componetes y sus estructuras en los sistemas de archivos del entorno de produccion.
 
- Work assignment stlye: Describe la relacion entre los modulos del sistema y las personas/equipos o organizaciones de trabajo unitarios asignados al desarrollo del mismo.

- ![[Pasted image 20240830232158.png]]


![[Pasted image 20240830232219.png]]

# Elementos, relaciones y uso

La relacion de estos elementos se basa en la ***allocated-to*** (asignado con). Usualmente hablamos de los estilos asignacion en terminos de relacion de piezas de software con su entorno.

Una sola pieza de software puede ser asignada a muchos elementos ambientales. Si estas asignaciones cambian con el tiempo, el arquitecto debe contemplar dichas dinamicas

Sus propiedades especificas que se deben incluir varian segun su propositio. La meta usualmente es comparar las propiedades requeridas por el el elemento de software con elemento ambiental propuesto.

***Por ejemplo***; Para asegurar el tiempo de respuesta de un componente, es necesario que este se ejecute (sea asignado a) a un procesador que provea ***suficiente rapidez*** de tiempo de ejecuccion, donde ***suficientemente rapido*** sea (de acuerdo a IEEE) la realizacion de 754 multiplicaciones de puntos flotantes de simple precision en 50 microsegundos.

O es posible que una plataforma de computo no permita que una tarea use mas de 10Kb de memeoria virtual. En este caso, un modelo de ejecucion del software, puede ser usado para determinar la cantidad de memoria virtual requerida,

# Ejemplos

[[Deployment Style]]

