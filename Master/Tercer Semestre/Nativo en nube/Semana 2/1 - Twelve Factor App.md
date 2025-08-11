---
tags:
  - master
  - cloud
  - DevOps
LInk: https://12factor.net/es/
---
Son una serie de principios para establecer una metodología en el desarrollo de aplicaciones modernas

1. Codebase) Un codigo base sobre el que hacer el control de versiones y multiples despliegues
2. Dependencies: Declarar y aislar explícitamente las dependencias
3. Configurations: Guardar la configuración en el entorno
4. Backing Services: Tratar a los "backing services" como recursos conectables
5. Build. Release, Run: Separar completamente la etapa de construcción de la etapa de ejecución 
6. Proceses: Ejecutar la aplicacion como uno o mas procesos sin estado
7. Port binding: Publicar servicios mediante asignación de puertos
8. Concurrency: Escalar mediante el modelo de procesos
9. Disposability: Hacer el sistema más robusto intentando conseguir inicios rápidos y finalizaciones seguras
10. Dev/prod parity: Mantener desarrollo, preproducción y producción tan parecidos como sea posible
11. Logs: Tratar los logs como una transmisión de eventos
12. Admin processes: Ejecutar las tareas de gestión/administración como procesos que solo se ejecutan una vez