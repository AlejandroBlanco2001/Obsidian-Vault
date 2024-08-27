Tags #arquitectura-de-software #modulos

Necesitamos describir como funciona en la unidad mas pequena nuestro sistema, esta descripcion es la **vista de modulos**

>[!NOTE]
>El hecho de poder repartir nuestro sistema en unidades manejables es una gran pieza en nuestro planteamiento

Como minimo nos muestra las relaciones de nuestro codigo fuente, que cosas se ven afectadas entre si y nos refleja atributos como ***modificabilidad***, ***portabilidad*** y ***reuso***

>[!IMPORTANT]
>Un arquitecto es aquel que puede ser profeta, si no es capaz de verlo, no es arquitecto

![[Pasted image 20240826224846.png]]

## Elementos

El elemento a manejar se llama ***modulo***, este refiere a muchas posibles estructuras de software como lo pueden ser unidades de programacion (Programas en C, Clases en Java o C#, Unidades Delphi, procesos almacenados de PL/SQL, paquetes de Java o C# namespaces)

>[!NOTE]
>Un moduloe es una implementacion que sigue una(s) ***responsabilidad***

## Relaciones

### Es parte de 
En este tipo de relacion, contamos con submodulos dentro de nuestros modulos, podemos verlo como una agreacion

### Depende de
En este caso marcamos una dependencia de un modulo con otro.

### Es un
Se refiere al contexto de generalizar/especializar entre un modulo hijo y un modulo padre.

## Propiedades

- Nombre: El nombre del modulo y su funcion, aunque tambien puede decirnos su composicion "A.B.C", se refiere al mdoulo C que es un submodulo de B, donde este ultimo es un submodulo de A

- Responsabilidad: Es una afirmacion sobre que debe hacer

- Visibilidad de interfaces: Deben exponer como acceder a ellas

 ![[Pasted image 20240826225643.png]]

- Informacion de implementacion
- Relacion con unidad de codigo fuente: Archivos que constituyen el modulo.
- Informacion sobre pruebas: Debe contener su plan de pruebas, casos de pruebas y datos de prueba
- Manejo de informacion: Fechas y costo
- Restricciones: Informacion privada del modulo


## Casos de uso

- Construccion: Tener una idea de como lucira el codigo fuente

- Analisis: El análisis incluye dos técnicas clave: *la trazabilidad de requisitos* y el *análisis de impacto*. La trazabilidad asegura que los módulos del sistema cumplan con los requisitos funcionales, mientras que el análisis de impacto predice el efecto de modificar el sistema. Documentar secuencias entre módulos muestra cómo se cumplen los requisitos, y las dependencias entre módulos son esenciales para un análisis de impacto efectivo. Para ello, el diseño debe ser completo y la información de dependencias precisa.

 - Comunicacion: Una vista de modulos nos permite explicar el sistema a alguien no tan familiarizado con el sistema.

## DSM (Dependency Structure Matrix)

Es una tablq que nos permite ver los modulos como las columnas y las cabeceras y dependencias como celdas. Es una matriz cuadrada ($n\times n$)
donde el elemento $M_{ij}$ no es cero si hay dependencia entre el modulo I y el modulo J.

## ERD (Entity Relationship Diagram)

Este es mas para las bases de datos, y es mas para modelado de datos.

# Estilo por capas

En este caso, nuestra unidad minima es algo que llamamos ***capa***. Cada capa representa un grupo de modulos que ofrence un conjunto de servicios. 

En las capas deben tener una relacion de tipo "permitido-a-usar-" de tipo unidireccional (basicamente uso de una direccion).

>[!NOTE]
>Una capa es una agrupación de módulos que juntos ofrecen un conjunto cohesionado de servicios a otras capas. Las capas se relacionan entre sí por la relación estrictamente ordenada que se permite utilizar.

Cada capa es un pedazo del software que se expone de manera publica.

![[Pasted image 20240827001258.png]]

En este caso es un ejemplo erroneo, porque permite a C (un modulo inferior) usar a B, que es el que lo utiliza en primea instancia.

>[!IMPORTANT]
>
Si mucha de nuestras capas superiores hacen uso de nuestras capas mas inferiores, esto es denominado ***layer bridging***, y es sintoma de un mal diseno. Ya que no favorece la portabilidad y modificacion del sistema

![[Pasted image 20240827001630.png]]

## Elementos

En este caso, nuestro elemento son las ***capas***. Es un requesito que esta capa (que puede ser cualquier cosa de software) exponga una interfaz

Estas tienen una relacion de uso (***puede-usar***), este deberia tener especificado:

- Contenido: Descripcion de la capa debe proveer lineamientos de que deberian hacer los modulos de esta capa y como se implementan. Tambien puede tener un listado con los modulos ***(Estos son unicos por capa)***
- Como se usaran las capas: Es decir se permite usar capas inferiores, muy inferiores? Se permiten segmentos horizontales?

## Casos de Uso

Potencia los atributos de calidad de ***facilidad de modificacion*** y ***portabilidad*** del sistema. El solo hecho de las capas se refiere al cncepto del principio de ocultar informacion.

>[!NOTE]
> La teoria plantea que un cambio en una capa inferior puede ser escondida detras de una interfaz y no impactara capas por encima de el.

En este caso, la advetencia es que la ***interfaz*** que exponemos significa mucho mas que una API. En este caso, una interfaz encarna todas las asumpciones de una entidad externa.

Un mito es es que la introduccion de capas agrega sobrecarga de tiempo de ejecuccion. Esto no es completamente real en muchos sentidos (simplemente en implementaciones nativas), pero en procesos de compilado/enlaze/carga reducen mucho este problema.

Por ejemplo, imagina un servicio no utilizado, que ocupara memoria y espacio para ser ejecutado, sin embargo, un proceso sofisticado de compilado/enlaze/carga puede remover eso.

## Formas de notacion

### Pila
En este caso, podemos ver que su adjacencia indica su relacion de uso

![[Pasted image 20240827073000.png]]

Esto puede ser leido como 

![[Pasted image 20240827073120.png]]

### Segmentada


![[Pasted image 20240827073141.png]]

### Anillada

![[Pasted image 20240827073232.png]]
En este caso no se puede pasar de uno anillado a uno en pila, debido a que la adjacencia significa uso. 
### Sidecar

![[Pasted image 20240827073441.png]]

Debe dejarse en claro quien usa a quien.

![[Pasted image 20240827073449.png]]

### UML
Son especificados con paquetes. Debes especificar segmentos, capas y la relacion de uso

![[Pasted image 20240827073510.png]]