---
tags:
  - UI/UX
  - master
---
El **UX Design** y el **PDS** pueden integrarse para mejorar la calidad del software, alineando necesidades de negocio y experiencia de usuario desde el inicio.  
Mientras el **UX Design** suele tener 4 etapas (_Descubrir, Comprender, Acotar y Aproximación_), el **PDS** se enfoca en 3 macrofases (_Levantamiento de requerimientos, Construcción, Validación_).

La propuesta es **usar las dos primeras etapas del UX Design como cimiento** de las fases iniciales del PDS.

---

### **1. Fase inicial del PDS – Levantamiento de Requerimientos**

Participan: **UX Designers, Business Analysts (BA), Arquitectos de Software y Líderes Técnicos**.

Puede ejecutarse en:

- Una única iteración (3–6 semanas) para proyectos bien definidos.
- Iterativamente en cada sprint si el alcance es incierto.
    

Se trabajan **dos flujos paralelos**:

1. **Diseño de la experiencia** (UX Research, conceptualización de usuarios y necesidades).
2. **Diseño de arquitectura de software** (estructuras técnicas iniciales).
    

---

#### **Etapa Descubrir**

- Investigación y recolección de información para entender problemas y metas.
- **BA**: recopila requisitos de negocio, flujos de proceso y especificaciones técnicas derivadas.
- **UX Researcher**: define perfiles de usuario, necesidades y problemas mediante observación y entrevistas.
- Se pueden incluir **herramientas de diseño de marca** (propuesta de valor, estrategia de comunicación, hipótesis de producto).
    

**Subpaso: Contextualización**

- Comprender el propósito del proyecto y expectativas del cliente.
- Analizar procesos internos y centrales de la empresa.
- Recopilar antecedentes mediante entrevistas con patrocinadores e interesados (_Debriefing_).
    

---

#### **Etapa Interpretar**

Objetivo: **transformar la información en recursos visuales** para entender el problema y proponer soluciones.

- **BA**: crea el **Modelo de Proceso de Negocio** (B2E, B2B o B2C).
- **UX Researcher**: elabora **User Personas** usando datos cualitativos y cuantitativos.
- **UX Strategist**: desarrolla **User Journeys**, **Customer Journeys** y, según el proyecto, **Service Blueprints** para mapear la experiencia global.
- **UI/Interaction Designers**: investigan tendencias visuales y funcionales mediante _mood boards_, _style tiles_, _benchmarks_ y _desktop research_.
    

---

#### **Paso Acotar**

- Generar y evaluar ideas creativas.
- Seleccionar las funcionalidades para el **MVP**, clasificándolas:
    
    1. **Línea Base**: mínimas para resolver las principales necesidades del usuario.
    2. **Primarias**: esenciales para cumplir objetivos clave.
    3. **Secundarias**: complementarias a las primarias.
    4. **Notables**: innovadoras y deseables, pero costosas o complejas.
        

---

### **2. Fase de Implementación y Desarrollo**

Con el MVP aprobado, se inicia **Construir y Validar**, que se basa en producción ágil y prototipado iterativo.

---

#### **Etapa Aproximación**

- **UX Strategist**: diseña la **Arquitectura de la Información**.
- **Interaction y UI Designers**: crean mapa de navegación y flujo de interacción (entrada de datos, salidas y retroalimentación).
- Entregables clave: prototipos validados en cada iteración.
    

---

#### **Iteraciones de Prototipado**

1. **Baja fidelidad** (maquetas de papel):
    
    - Realizadas por UI/Interaction Designers y UX Strategist.
    - Probadas con usuarios bajo la guía del UX Researcher.
    - Sirven para validar hipótesis y decidir si continuar (_perseverar_) o replantear (_pivotar_).
        
2. **Wireframes navegables**:
    
    - Versión limpia sin diseño visual final.
    - Permiten pruebas de comprensión y usabilidad tempranas.
        
3. **Alta fidelidad**:
    
    - Con **Style Tile** y **Design System** aprobados.
    - Incluye diseño visual, patrones de interacción y componentes de interfaz.
    - Usados en pruebas de usabilidad con clientes y usuarios finales.
        

---

#### **Transición al desarrollo**

- El **Design System** se entrega al equipo de **front-end**.
- Los desarrolladores crean una **biblioteca de componentes reutilizables** para construir las vistas de forma eficiente.
- Se mantiene un ciclo ágil de mejora continua basado en retroalimentación.
    

---

### **Elementos no tecnológicos posteriores**

- **Gestión del cambio** para lograr adopción por parte de usuarios.
- **Recompra aprobada**: clientes satisfechos que solicitan nuevas fases o servicios.