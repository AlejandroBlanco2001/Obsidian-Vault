---
tags:
  - arquitectura-de-software
  - diseno-uml
  - estilo-arquitectonico
  - master
  - modular
---
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

