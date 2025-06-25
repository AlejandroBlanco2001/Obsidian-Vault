---
tags:
  - CI/CD
  - DevOps
  - Agilismo
  - master
---

>[!NOTE]
>DevOps = Developer Operations

El contexto de DevOps nace dentro del marco del agilísimo, que tiene cosas como:
- Entrega de valor continuo al cliente
- Negocio + Desarrollo
- Clientes dentro del equipo
- La salida a producción es una tarea común, debemos salir siempre rápido

>[!IMPORTANT]
>Recordemos que DevOps son una serie de practivas que podemos seguir para mejorar el proceso de integracion y despliegue.

Para ejemplificar esto podemos hacer un diagrama de despliegue (Ver mas en [[Vista de Asignacion]])

![[Pasted image 20240924215201.png]]

La madurez de una pipeline de DevOps es proporcional a la rapidez de la salida a producción, una falta de madurez provoca preguntas como:

- Estamos listos para salir?
- Como sabemos que al desplegar todo va a funcionar?
- Y si el despliegue lo hace alguien manual?

![[Pasted image 20240924215642.png]]

Para DevOps tenemos practicas para CI (Continuous Deployment) y CD (Continuous Deployment), los pasos podrían ser:

| CI             | Release                   | CD                          | Operacion y Monitoreo |
| -------------- | ------------------------- | --------------------------- | --------------------- |
| Versionamiento | Manejo de configuracion   | Infraestructura como codigo | Recuperacion          |
| Comunicacion   | Configuracion como codigo | Automatizacion de pruebas   | Escalamiento          |
| Integracion    |                           |                             | Monitoreo             |
| Pruebas        |                           |                             |                       |

![[Pasted image 20240924220152.png]]