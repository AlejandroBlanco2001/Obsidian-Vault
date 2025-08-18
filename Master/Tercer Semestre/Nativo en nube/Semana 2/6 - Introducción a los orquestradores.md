---
tags:
  - master
  - cloud
  - k8s
---
Imagina que tienes varios contenedores (aplicaciones), como hacemos para resolver las siguientes preguntas:

- Como manejamos su despliegue?
- Como escalamos cada uno de ellos sin afectar a los demás?
- Como evitamos colisiones entre los datos y accesos?
- Como despliego una version mas reciente de mi contenedor?
- ...

En un enfoque tradicional. podríamos tener varias maquinas virtuales en un cluster donde hacemos todas estas acciones para resolver las dudas previamente planteados  (coste humano + tecnológico + operación)

Sin embargo, actualmente con los contenedores podemos hacer uso de un orquestrador para manejar ***situaciones complejas con muchos contenedores como Kubernetes***

> Los orquestradores nos permiten: Aprovisionar nuevos contenedores, gestión dinámica de recursos, red y balanceo y monitoreo de los contenedores

Kubernetes (k8s) nos permite tener a un serie de nodos:

- Control plane  (Operaciones de manejo)
- Worker (Aplicaciones)