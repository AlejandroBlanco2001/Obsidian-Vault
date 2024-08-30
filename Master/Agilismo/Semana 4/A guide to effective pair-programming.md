Tags: #PairProgramming #SoftSkills

>[!NOTE]
> La programacion en parejas como concepto es algo nuevo, sin embargo, ***Jean Bartik*** una de las pioneras de ENIAC, hizo por mucho tiempo esta practica

El pair (peer) programming es donde basicamente dos desarrolladores se sienta a escribir codigo de manera conjunta. Esto ayuda al flujo de ideas, discusion de la solucion y revision de bugs.

# Como hacer pair programming?

Esta practica cuenta con varios estilos para ser realizado

##  Driver and Navigator

Donde hay una persona que actua de conductor, basicamente es el que escribe. Este siempre debe hablar mientras hace sus cosas. Solo debe concentrarse en escribir

Mientras que el navegador, es el que mira lo que el conductor escribe, basicamente revisa el codigo al momento de ser producido. Este debe concentrarse en aspectos mas amplios del desarrollo

![[Pasted image 20240829204844.png]]

## Ping Pong

Esta practica abraza al TDD (Test-Driven Development), y es perfecto cuando tienes una tarea bien definida.

- Ping: Desarrollador 1 escribe un test que va a fallar 
- Pong: Desarrollador 2 escribe el codigo que hace que el test pase
- Ping: Desarrollador 2 escribe un test que va a fallar
- Pong: Desarrollador 1 escribe el codigo que hace que el test pase

## Strong-Style pairing

Basado en la idea:

> Primero debes hacer que el otro entienda, una vez entienda, puedes escribir el codigo

Este es una variacion del [Driver and Navigator](#Driver-and-Navigator), donde se busca la transferencia de conocimiento, donde el navegador es alguien con mucha experiencia mientras que el segundo no tanta.

En este escenario, el conductor confia ciegamente en el navegador y debe estar comodo "con no entender". Todas esas preguntas se resuelven despues

Mayor seguimiento en el articulo de [[Strong-Style Pairing]] por Llewellyn Falco.
## Pair 

Este esta mucho mas enfocado en cubrir la parte no relacionada al codigo durante el desarrollo de una historia de usuario, por ejemplo:

- Planeacion
	- Entender el problema
	- Solucion
	- Acercamientos
- Busqueda y exploracion
	- Definir preguntas a contestarse en comun y dividirlas
- Documentacion
	- Deberian ser revisadas las features y generar la documentacion necesaria para cada caso.


## Manejo del tiempo

Esto puede ser bastante consumidor de tiempo, puede llevar a sesiones de una hora o mas, por ende, se debe contar con mecanismo para mitigar estas largas sesiones.

Por ejemplo, usar la tecnica de Pomodoro para empezar a realizar las rotaciones.

## Rotacion de parejas

Debes empezar a rotar tu pareja, debido a que puede ocasionar los siguientes escenarios:

-  Un silo de conocimiento, donde el conocimiento sobre una feature en particular no sale de las personas involucradas
- Creacion de vinculos 
- Confianza excesiva de las personas, generando posibles sesgos

El numero de rotaciones y el tiempo debe ser determinado por la sesnsacion del equipo.

## Tiempo y mas tiempo

Cosas como el espacio y los tiempos, deben tener todo definido:

- A que hora
- Donde
- El espacio adecuado
- Que dias y cuantas horas

# Cosas para evitar

- Siempre prestale atencion al otro, no te pongas con el telefono o hacer otra cosa.
- No hagas micro-management, deja a la otra persona fluir
- Siempre espera un tiempo antes de comentar algo.
- Comparte el teclado, no seas acaparador
- Pair programming no significa sesiones de 8 horas.
- No seas el que dice ***"Esta"***  debe ser la manera

## Beneficios del pair programming

![[Pasted image 20240829211106.png]]

**Compartición de Conocimientos** El beneficio más evidente del emparejamiento es la compartición de conocimientos. Trabajar en pareja en una pieza de código ayuda a distribuir el conocimiento sobre tecnología y dominio, previniendo silos de información. Además, al discutir un problema con otra persona, se incrementa la probabilidad de encontrar una buena solución, ya que se consideran más alternativas.

>[!NOTE]
>No temas emparejarte en tareas que desconozcas. Mantenerse en áreas cómodas puede limitar tu aprendizaje y la difusión de conocimientos. Si notas que un miembro del equipo trabaja siempre en los mismos temas, sugiérele variar para compartir su experiencia. Crear una matriz de habilidades y colgarla en el área del equipo puede ayudar a distribuir el conocimiento.

**Reflexión** El emparejamiento obliga a discutir enfoques y soluciones, lo que ayuda a reflexionar sobre nuestra comprensión y la calidad de nuestras soluciones. Esto aplica tanto al código como al diseño técnico y a las historias de usuario.

>[!NOTE]
>Construye confianza para crear un ambiente donde ambos puedan hacer preguntas y hablar abiertamente sobre lo que no entienden. Es fundamental tener sesiones regulares de 1:1 y de retroalimentación.


**Mantenimiento del Enfoque** Trabajar en pareja facilita un enfoque estructurado. Cada uno debe comunicar por qué está haciendo algo y hacia dónde se dirige, evitando distracciones y asegurando el cumplimiento de objetivos.

>[!NOTE]
>Planifiquen juntos, discutan los pasos necesarios y utilicen técnicas como Pomodoro para mantener el enfoque. La comunicación constante es clave.

**Revisión de Código en Tiempo Real** El emparejamiento permite detectar errores y mejorar el código a medida que se escribe, en lugar de hacerlo después.

>[!NOTE]
> Haz preguntas para entender y mejorar las soluciones. Si necesitas más revisión de código, reflexiona sobre la calidad de tu emparejamiento.

**Dos Modos de Pensar Combinados** El emparejamiento combina la perspectiva táctica del "driver" con la perspectiva estratégica del "navigator", mejorando la calidad del código al considerar tanto los detalles como el panorama general.

>[!NOTE]
>Cambia de roles regularmente y evita que el "navigator" entre en modo táctico. Esto ayuda a refrescarse y a practicar ambos modos de pensamiento.


**Propiedad Colectiva del Código** La propiedad colectiva del código implica que el código es propiedad de todo el equipo y cualquier persona puede hacer cambios en cualquier parte.

>[!NOTE]
>El emparejamiento no garantiza la propiedad colectiva; es necesario rotar a los miembros del equipo para evitar silos de conocimiento.


**Reducción del WIP del Equipo** Limitar el trabajo en progreso (WIP) mejora el flujo del equipo. El emparejamiento ayuda a reducir la multitarea y a enfocarse en menos tareas a la vez.

>[!NOTE]
>Limita el WIP al número de pares en el equipo y hazlo visible en el espacio del equipo o en herramientas de gestión de proyectos en línea.


**Rápida Integración de Nuevos Miembros** El emparejamiento facilita la incorporación de nuevos miembros al equipo al compartir conocimientos sobre el proyecto y la organización.

>[!NOTE] 
>Asegúrate de proporcionar el contexto general antes de la primera sesión de emparejamiento y usa la máquina del nuevo miembro para configurar su entorno. Ten un plan de incorporación con temas a cubrir y marca los temas a medida que se aborden en las sesiones de emparejamiento.

# Desafios

- Tener una sesion puede ser canson (a nivel de energia)
	- Tener breaks
- El componente humano es dificil de mantener
	- Conversar antes de programar, establecer palabras, tematicas, formas 
- Reuniones reuniones reuniones que cortan la sesion
	- Tener reglas definidas para cuando aceptas las reuniones
- Diferencias de niveles
	- Nunca asumas nada basado en el nivel del otro, escuchense y colaborense
	- Ver la charla en [[Patterns of Effective Teams]]
- Dinamica de poderes (color, nivel, genero)
	- Liberate de prejuicios y trabajar con una persona
- Empeazar sin saber
	- Haz una spike, investiga, sal de dudas
- Perdida del contexto
	- Esto es algo que debe pasar, con el tiempo esto se perdera
- Debes ser vulnerable
	- Debes estar dispuesto a equivocarte y no saber
- 