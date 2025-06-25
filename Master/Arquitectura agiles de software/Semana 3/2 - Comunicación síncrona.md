---
tags:
  - microservicios
  - arquitectura-de-software
  - tacticas-arquitectura
  - master
---
Al tener los microservicios totalmente aislados uno del otro nos da muchas ventajas a nivel de despliegue y manejo de cambios de cada uno, pero tenemos un gran problema, ***como se comunican?***

Tenemos una opción que es la **manera síncrona**, donde cada uno de ellos se comunica directamente con el otro atreves de peticiones por medio de sus APIs.

- Consultas: Extraer información sin afectar al estado de la aplicación, por ejemplo, traer los usuarios del sistema
- Comandos: Afectan el estado de la aplicación, por ejemplo, crear una orden de compra

Para ocultar a los consumidores la disponibilidad y a quien deben solicitar las cosas, podemos implementar un ***API Gateway*** donde este se encarga de redirigir a cada uno de los microservicios.

Al hacer esto de manera sincrónica, siempre debemos esperar que el otro responda, y de igual manera, puede pasar que uno de los microservicios involucrados, no este disponible, causando que el otro se vea afectado.

Para solucionar esto, podemos separar los microservicios en cuales hacen comandos y cuales consultas, donde podemos tener dos instancias de la base de datos, donde usamos una para escribir y otra para lectura, este patrón se conoce como [[CQRS]] (Command Query Responsability Segregation)

