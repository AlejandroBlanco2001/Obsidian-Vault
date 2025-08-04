---
tags:
  - master
  - cloud
  - DevOps
  - CI/CD
  - git
---
Un aspecto importante a la hora de desarrollar también es como *organizamos nuestro codigo fuente*, donde tenemos dos grandes vertientes: monorepo y mutlirepo

En un *multirepo* (o polirepo), contemplamos tener un repositorio distinto por proyecto, servicio o componente, cada uno siendo administrado y versionado de manera independiente

```
git
/auth-service
├── src/
├── tests/
└── README.md

git
/billing-service
├── src/
├── tests/
└── README.md

git
/ui-components-repo
├── src/
├── examples/
└── README.md
```

Alguna de las ventajas de esta manera puede ser:
- Autonomía total para equipos, que pueden definir su ciclo de vida de forma independiente.
- Versionamiento individualizado, lo que permite liberar cada componente cuando esté listo.
- Aislamiento claro de responsabilidades, facilitando la gobernanza y control de acceso.
- Menores riesgos en los procesos de mezcla y construcción de los componentes.
- Procesos de code review y pruebas más sencillos.

y tambien tenemos problemas como:
- Coordinación de cambios más difícil, especialmente cuando hay dependencias entre proyectos.
- Requiere mayor esfuerzo para mantener consistencia de estilo y configuración entre repositorios.
- Duplicación de código o configuraciones comunes, si no se usan paquetes compartidos bien mantenidos.
- Incrementos en la gestión de todos los repositorios por parte de los equipos. Es más difícil tener una vista clara y completa de todo el código, sus dependencias y su calidad.
- Comunicación y colaboración entre equipo puede ser más difícil dado que los equipos normalmente trabajan en silos.

Por otro lado, tenemos el otro enfoque de *monorepo*, donde mantenemos todos nuestros servicios, proyectos o componentes en un mismo repositorio

```
git
/my-system
├── users-service/         ← servicio de usuarios
│   ├── terraform/         ← infrastructura de la aplicación
│   └── src/               ← código de la aplicación
├── pets-service/           ← servicio de mascotas
│   ├── terraform/         ← infrastructura de la aplicación
│   └── src/               ← código de la aplicación
├── libs/
│   └── auth-utils/        ← Librería compartida para autenticación
└── infrastructure-cross/  ← Módulo de infrastructura para todos los proyectos

```

Entre las ventajas de usar este enfoque se encuentran:
- Facilidad para realizar cambios coordinados entre múltiples proyectos.
- Reutilización de código y facilidad para identificar dependencias entre proyectos. Lo que permite evaluar de mejor forma el impacto de un cambio.
- Consistencia en configuraciones y convenciones a través de todo el repositorio.
- Revisión de código más contextualizada, ya que todo vive en el mismo lugar.
- Mejora la colaboración y comunicación entre equipos, dado que se ve fácilmente en que están trabajando todos los equipos.

Y entre sus desventajas se encuentran:
- Puede generar problemas de rendimiento en grandes escalas (repositorios con millones de líneas de código).
- Requiere herramientas especializadas o procesos correctamente definidos para gestionar cambios, dependencias y procesos de CI/CD.
- Cambios pequeños pueden generar grandes ciclos de CI si no se optimiza correctamente.
- Dificultad para asegurar que todos los cambios están correctamente probados y revisados.