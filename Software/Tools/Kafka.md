---
tags:
  - arquitectura-de-software
  - kafka
---
Esta herramienta es catalogada como un ***message broker****

> * Es un largo debate debido a que aunque si actúa como uno, cuenta con muchas otras cosas y funcionalidades que lo permiten ser usado para otras cosas fuera de ser un message broker, 

Se basa en la arquitectura Pub-Sub, donde tenemos nodos clientes que se encargar de **producir** (escribir) sus **eventos** (mensajes) y clientes que se **suscriben** (leen y procesan) dichos eventos.

Dichos eventos, se guardan en **tópicos**, que pueden ser vistos como un sistema de archivos, donde cada archivo seria un evento.

> [!IMPORTANT]
> Kafka patrocina una arquitectura multi-subscriptor y multi-consumidor, es decir, un tópico puede tener ningún, uno o muchos subscriptores/consumidores.

La particularidad de Kafka, es que luego de que un mensaje es consumido, ***este no es borrado***, tu puedes configurar el tipo de persistencia que tendrá este tópico y las reglas del mismo.

Una idea muy importante para temas de escalabilidad, es la noción de que ***los tópicos pueden ser particiones***, 