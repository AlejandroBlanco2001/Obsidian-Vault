---
tags:
  - databases
  - query
---
>[!IMPORTANT]
El modelo de datos limita nuestro entendimiento y visualización de un problema

Una de las mayores cuestiones es preguntar inmediatamente como lo represento la capa de abajo?

1. En tu aplicación web, tendrás ***objetos*** que son manipulados por una API
2. En la transferencia de esos, tendrás formatos como ***JSON/XML/grafos/relaciones***
3. En la base de datos mismas, tendrás grafos/relaciones/JSON/XML que deben ser representados en ***bytes***
4. En el hardware, tendrás bytes que son representados como ***corrientes eléctricas***

>[!IMPORTANT]
>Siempre recuerda, cada capa trabaja con el principio de encapsulamento, cada una oculta los detalles de la capa anterior

Las abstracciones son las que nos permite comunicarnos de manera correcta entre dos grupos de personas que no hablamos el mismo idioma

# Relacional vs documentos

El modelo de datos relacional es el mas conocido y utilizado actualmente, creado por Edgar Codd en 1970. Donde nuestros datos son guardados en ***relaciones*** (tablas de SQL), y los datos se almacenan en forma de ***tuplas*** (filas de SQL).

Posterios a los *RDBMS* (Relation Database Management System), este modelo tuve un despegue increible, y una adopcion que duro por mucho tiempo, alrededor de 30 anos.

>[!IMPORTANT]
>El nacimiento de estas mismas, se debe al problema de manejar las transacciones y las operaciones por lotes, dentro de las computadoras centrales

Siempre tengamos en cuenta que ya existian las bases de datos en esa epoca, sin embargo, las relacionales ocultaron ***una capa de abstraccion***, lo que ayudo a un desarrollo mas limpio, las bases de datos previas ***necesitaban que supieras una representacion interna de los datos***

>[!NOTE]
>Tambien existian el ***modelo jerarquico*** y el ***modelo de red***

## Nacimiento de NoSQL

Las bases de datos NoSQl, nacen para abarcar todas las nuevas tecnologias de codigo abierto, no centralizadas y no relacionales fuera de SQL, dandole el significado de ***Not Only SQL***, estas nacen para atacar;

- Temas de escalabilidad 
- Codigo abierto > Codigo corporatio
- Consultas especializadas que SQL no soporta tan bien
- Frustaciones que viene de no tener siempre una manera relacional de organizar nuestros datos 

## El desajuste objeto-relacional

Uno de los mayores inconvenientes de las bases de datos relacionales es que estas las aplicaciones que las utilizan son todas basadas en lenguajes de programacion orientados a objetos (Java, C#, Python, Go...).

Entonces, si todos nuestros codigo usan ***objetos*** porque debemos tener una capa de abstraccion extra para convertir estos en tablas , relaciones y tuplas?.

>[!IMPORTANT]
> Esto recibe un nombre especial en electronica, lo que se llama ***desajuste de impedencias***

En este contexto, nacen los ORMs para evitar esta duplicacion de codigo base, sin embargo, no logran completamante ocultar estos detalles.

Imagina que quieres construir un modelo relaciona para LinkedIn donde quieres almacenar la informacion de una persona, basicamente quieres guardar su curriculum, y necesitas:

- Informacion basica del usuario
- Cargos
- Industria
- Formacion acdemica
- Contacto

Si lo pensamos bien, en estos casos, usar un ***JSON***, es una forma mas apropiada y sencilla de almacenar esta informacion, para esto podriamos usar MongoDB, CouchDB y sus alternativas.

>[!NOTE]
>El lenguaje de modelado de datos se asemeja al lenguaje de dominio del programa, en este caso, el desarrollador es mas libre y al mismo tiempo mas responsble de que hace 

Si lo pensamos, en algun punto obtener informacion de la persona puede ocasionar varias consultas para obtener esos datos, sin embargo, dentro del almacenamiento por JSON, simplemente con el archivo tenemos todo.

>[!NOTE]
>Un dato curioso es que un JSON, es un arbol 

Recuerda que si tratas de hacer lo mismo con una base de datos relacional a una base de datos basada en documentos, todo el tema de uniones, no los hara la base de datos directamante, lo hara tu codigo (con costo en memoria), ***lo que afecta directamente el rendimiento de tu software***.

>[!IMPORTANT]
>Recuerda que con el tiempo, ***los datos siempre cambian***, no solo en contenido, sino en significado y conexiones.

Y si te imaginas, cada vez que tus datos muten y crezcan, puede ser que la base de datos de documentos comience a flaquear y decaer, y hayas tomado una mala decision basicamente.

## Bases de datos orientadas a documentos, lo mismo que otras veces?

Este problema sobre relaciones muchos a muchos y sus consultas, no es un problema nuevo, es mas, desde antes de las bases de datos relacionales y NoSQL, ya existia ese problema y se remonta al inicio de las mismas bases de datos informaticas.

### Pequeno viaje en la historia

El primer sistema de procesamiento de datos en lotes era el IMS de IBM, que se uso para el Apolo en el viaje a la Luna, este fue desarrollado usado el ***modelo jerarquico***.

Basicamente, se basa en la estructura de datos en arbo (Muy parecido a lo que hace hoy en dia JSON con MongoDB), este funcionaba de manera muy eficiente para relaciones uno a muchos, sin embargo cuando era muchos a muchos, comenzaba de flojear.

Esto provoco  redundancia (Desnormalizar los datos) o resolver manualmente dichos problemas para completar las uniones.

>[!NOTE]
>Ese problema de 1970, es el mismo que se tiene con las bases de datos no relacionales basadas en documentos hoy en dia!!

## Modelo de Red

> Este fue estandarizado por el CODASYL (Conference on Data System Languages)

Este era muy parecido al modelo jerarquico (Es decir, contamos con un arbol), sin embargo, en este caso, un registro puede tener multiples padres. Este simple cambio, permitia tener relaciones muchos a uno y muchos a muchos.

Estas referencias, no eran valores raros o inventados, eran punteros en un lenguaje de programacion que el desarrollador colocaba y se almacenaban en disco, para encontrar estos registros teniamos que seguir la cadena de estos, esto se denomino ***ruta de acceso***.

Este recorrido en el mundo jerarquico tenia sentido, parecido a una lista enlazada, sin embargo, al tener un arbol con multiples padres, era posible tener ***muchos caminos hacia un mismo lugar***.

Por ende, navegar sobre esto involucraba ubicar un *cursor* por la base de datos, y comenzar a iterar hasta encontrar el registro indicado, si este tenia multiples padres, debiamos recorrer todos los caminos posibles.

Esta asignacion manual, y complejidad de busquedas, volvio al modelo inflexible.

## Modelo Relacional

El modelo relacional elimino por completo las estructuras de arboles y grafos (a simple vista) para el desarrollador, haciendo uso solo de relaciones y tuplas, lo que ***escondia toda la complejidad*** para los desarrolladores, la forma de referenciar otras cosas eran mas intiutivas y sencillas de leer.

Estas venian con un [[Query Optimizer]], lo que se encargaba de realizar, diagnosticar y mejorar el orden de ejecuccion de nuestra consulta con el fin de hacer lo mejor posible, esto claramente eran nuestras ***rutas de acceso***, sin embargo, ya dejaron de ser problema del desarrollador y mas del motor.

Las bases de datos relacionales sobreviven debido a su optimizador de consultas, estas son el corazon de la mejora, al ser de ***proposito general*** son indistintas de nuestro lenguaje de programacion.

De igual manera, podemos recalcar lo siguiente, mientras nuestras relaciones sean uno a uno, o muchos a muchos, no son fundamentalmente distintas. 

### Almacenes triples y SPARQL

Este es una forma de abstraer las bases de datos basadas en ***grafo de propiedades***, se denomina almacén triple, donde contenemos una tripleta de la forma `(sujeto, predicado, objeto)`

Donde el `sujeto` equivale a el vértice dentro de un grafo, el `objeto` puede ser dos cosas:
- El valor de un tipo de de datos primitivos
- Otro vértice del grafo

Por ejemplo 

```
_:lucy a :Person
_:lucy :name "Lucy"
_:lucy :bornIn _:Idaho
....
```

>[!NOTE]
>Como un recordatorio, el uso de `_:` denota a un vertice

Un formato que tiene la www (World Wide web) es el ***modelo de datos RDF*** (Resource Description Framework), donde esta creado principalmente para el intercambio de recursos, específicamente sus metadatos.

Debido a que usa el format Turtle (Lenguaje para almacenes triples), es posible ingresarlos dentro de la URI (Unique Resource Identifier), por ejemplo:

```
http://my.company.com/namespace#within
http://my.company.com/namespace#lives_in
```

Cuando hablamos de SPARQL, hablamos del equivalente del modelo de datos para RDF, donde si hacemos una comparación de las consultas hechas en Cypher (Base de datos modelado en grafos) y SPARQL (base de datos basada en el modelo de datos RDF), esta queda mucho mas concisa y clara de leer.

#### Es posible que el modelo de grafos, sea una segunda ola del modelo de redes?

Un pensamiento valido es pensar que una es la continuación o mejora de la otra, sin embargo, la respuesta mas rápida es un **No**.

- En **CODASYL**, hay una restricción por esquema a nivel lógico que no permite una dinamicidad en los hijos de la misma, sin embargo, en el modelo de grafos, cada vértice puede ser creado sin tener en cuenta un esquema previo 
- En **CODASYL**, teníamos que seguir las famosas **rutas de acceso** para llegar a un registro particular, mientras que en la base de datos de grafos, una búsqueda por ID es lo único para llegar a un vértice en concreto.
- En **CODASYL**, los hijos de un registro eran un conjunto ordenado, por lo que la base de datos debía mantenerlos ordenados (afectaba la disposición de la información), en las bases de datos de grafo, no es necesario
- En **CODASYL**, todo era imperativo, por el otro lado, todo era declarativo.

## Los primeros avances: Datalog

Datalog es el primero de todos estos lenguajes de consulta, altamente estudiado en la década de los 80, es uno de los primeros en construir la base de los previamente mencionados.

Aun en día es usado en sistemas basados en modelos de datos Datomic y Cascalo, que constituyen una implementación de Datalog, para consultar grandes conjuntos de datos en Hadoop.

Podemos decir que es muy parecido al formato de almacenamiento triple, sino que usa el formato de `predicado (sujeto, objeto)` 

```
name (namerica, 'North America')
type (namerica, continent)

name (usa, 'United State')
```