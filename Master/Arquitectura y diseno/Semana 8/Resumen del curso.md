---
tags:
  - arquitectura-de-software
  - master
---
Los temas mas importantes del curso fueron:
- Requisitos de calidad 
- Puntos de Vista / Vistas
- Estilo de Arquitectura
- Tacticas de Arquitectura
- Patrones de diseno

# Requisitios de calidad
Recordemos que una buena toma de requisitios es clave, esto nos permite tomar mejores decisiones, en este caso usamos los ***escenarios de calidad*** con sus partes:

- Fuente
- Estimulo
- Artefacto
- Respuesta
- Medida de la respuesta
- Ambiente

# Punto de vista  y vistas
Un ***punto de vista*** es la respuesta a una persona interesada del proyecto y que funcion debe cumplir , y las vistas son los modelos a tomar en cuenta, donde tenemos vistas para:

- Componentes y conectores
- Modulos
- Asignacion

Podemos tomar muchas referencias para estos puntos de vista, por ejemplo:

- Desarrollo
- Contexto
- Vista
- Funcional
- Concurrencia
- Informacion
- Operacion

# Estilos de Arquitectura
Una vez sepamos organizarlos, y nuestros modelos estan completos, podemos tomar un estilo de arquitectura para satisfacer un atributo de calidad, estos son patrones de diseno a nivel de arquitectura.

Los mas famosos son los orientados a Componentes y Conectores, en este caso podemos clasificarlos en:

- Orientado a flujos
	- Pipe & Filter
- Llamada - Retorno (Baja latencia)
	- Cliente - Servidor
	- Punta a Punta
	- SOA
- Orientado a Eventos (Bajo acoplamiento)
	- Publicador - Subscriptor
- Orientado a depositios
	- Datos compartidos

El estilo por capas nos ayuda a organizar el software en modulos, el estilo por niveles nos ayuda a disenar en funcion de la seperacion y mantenimiento

# Tacticas de Arquitectura
Luego de tener nuestra arquitectura, necesitamos aplicar ciertos detalles para mejorar nuestros atributos de calidad, en este caso se llaman ***tacticas de arquitectura***, para el desempeno usamos:

- Acceso a los recursos: Prioridad sobre recursos limitados
- Incremento de recursos: Reducir la lucha por los mismos

