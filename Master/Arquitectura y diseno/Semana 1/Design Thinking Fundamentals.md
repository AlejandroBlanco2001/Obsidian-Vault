Disenar software es descubrir y buscarla, siempre en tu primer dia como arquitecto, esta TBD.

Este enfoque de diseno, se basa en las personas y para las personas:

- Personas **afectadas** por tu diseno
- Personas que **usaran** tu diseno
- Personas que **leeran** tu diseno

>[!IMPORTANT]
>Un enfoqe humano siempre recuerda que eso es lo que busca tu software, ayudar personas 

## Principios

Estos principios se basan en pensar sobre **las personas** que son afectadas por estas soluciones y problemas que tenemos, mas que el proceso.

- Regla humana: Todo diseno debe ser ***social por naturaleza***
- Regla ambigua: Manten la ***ambiguedad***
- Regla del rediseno: Todo diseno es un ***rediseno***
- Regla de tangebilidad: Haz las ideas tangibles para ***facilitar la comunicacion***

En ingles por sus siglas, HART

### Disenar para personas

Disenar es algo inherente al humano, disenamos para personas, disenamos software con personas, el software es usado por personas.

Por ende, toda decision debe ***ser compartida con otros humanos***. De esta manera el arquiecto, debe:

- Empatizar con sus stakeholders
- Importar sus usuarios finales
- Importar los usuarios finales de esos usuarios finales
- El programador que desarrollara su arquitectura
- El tester que la prueba
- Hasta el manager que la revisa 

Esta tambien nos recuerda, que debemos **trabajar en equipo***

### Conservar la ambiguedad

Muchas veces la ambiguedad es ***sinonimo de peligro***. Y conserverla puede tener problemas graves a nivel de comunicacion.

Sin embargo, un arquitectura es una ***representacion de alto nivel***, se puede ver como algo minimalista

>[!IMPORTANT]
>Ruth Malan y Dana Bredemeyer definen un diseno de arquitectura como una arquitectura minimalista, solo muestra lo justo y necesario
>

El resto de decisiones **puntuales***, se deciden en el camino y a medida de que los otros disenadores tomen cargo.

Si la ambiguedad no reduce riesgos o atributos de calidad, entonces que siga ambigua.

### Disenar es redisenar

Recordemos que esto es algo ***evolutivo***,  lo que no sirvio ayer no quiere decir que no sirva manana. 

Todo nuestros disenos maduran y crecen con el tiempo, siempre abriendo paso a mejoras y nuevas necesidades.

+Refinar -Crear de nuevo

### Haz la arquitectura tangible

Todas nuestras ideas arquitectoncias deben trasncender, deben dejar de estar en nuestra mente.

Por eso debemos plasmarlas en algun lado, ya sea:

- Creando diagramas
- Creando la arquitectura en si (implementandola)
- Prototiparla
- Modelos de algunas partes 
- Metaforas


## Mentalidad

La mentilidad debe ser lo mas general posible, y se basa en los siguentes aspectos:

- Entender
- Explorar
- Evaluar 
- Hacer

### Entender

Involucra recoger toda la informacion posible de los stakeholders, y trabajar en ***describir*** el problema. 

Siempre debemos tener **empatia** con los requerimientos, entender quien usara el sistema y sus necesidades.

Enteder las necesidades, metas del negocio, los atributos de calidad que necesitan para lograrlo.,

### Explorar

En esta parte, nos encargamos de recoger todas las ideas posibles de manera integral.

Basicamente buscamos como combinar nuestras estructuras arquitectonicas para resolver de la mejor manera el problema.

Debemos buscar toda la informacion posible

### Hazla real

Tener ideas es chevere, pero si no las puedes transferir entre cerebros, **no sirven**.

Por ende, la parte de hacer, es cualquier manera de hacer tangible nuestra idea, como:

- Diagramas
- Creando modelos
- Protoipado
- Documentacion
- Codigo

>[!IMPORTANT]
>Es necesario escapar de la paralisis del analisis

### Evaluar

Debemos analizar que tan buena fue la solucion para nuestro problema, ya sea en su plenitud o por partes (hasta la unidad mas sencilla).

Dibujar escenarios para nuestra arquitecuta puede ser una manera de evaluarla.

Correr experimentos sobre nuestra arquitectura.

## Piensa, haz, verifica

En nuestro dia a dia siempre descubrimos cosas nuevas del software, estas cosas nuevas nos llevan a pensar si esto debe cambiar.

Por ende, nuestro arquitectura siempre debe estar ***en constante retroalimentacion***

Por ende:
- Piensa
	- Riesgos de ing.
	- Negocio
	- Atributos de calidad 
	- Trade off
- Haz
	- Modelos
	- Prototipos
	- Planes
	- Listas de alternativas
- Verifica
	- Escenaris
	- Alternativas de comparacion
	- Test
	- Comparaciones
	
![[Pasted image 20240810030700.png]]

### Iteracion

1. **Duración de la Iteración**: Las iteraciones pueden durar desde unos pocos minutos hasta varios días, con una preferencia por ciclos más cortos, aunque los más largos pueden ser necesarios para investigaciones más profundas.

2. **Proceso Consistente**: Cada iteración sigue los mismos pasos, aunque la ejecución varía según la mentalidad de diseño adoptada.

3. **Pensar**: 
   - Determina qué esperas aprender.
   - Identifica las preguntas clave y los riesgos.
   - Crea un plan para responder a las preguntas o reducir los riesgos.

4. **Hacer**: 
   - Ejecuta el plan.
   - Crea algo tangible que descubra información de manera rápida y económica.

5. **Verificar**: 
   - Examina críticamente los resultados del paso "Hacer".
   - Utiliza las ideas obtenidas para decidir el siguiente movimiento, lo que lleva de nuevo al paso "Pensar".

6. **Proceso Continuo**: 
   - Los sistemas de software nunca están terminados; solo se lanzan.
   - El enfoque de diseño no tiene fin y se aplica siempre que revises o evoluciones la arquitectura.

## Esta mentalidad no tiene orden

- **Cuatro Mentalidades de Diseño**: Piensa en las cuatro mentalidades de diseño como cuatro cajas de herramientas, cada una con herramientas ajustadas para un tipo particular de trabajo de diseño. 
    
	- **Entender**:
	    - Se enfoca en las necesidades de los interesados y cómo especificar esas necesidades como requisitos.
	- **Explorar**:
	    - Se centra en la lluvia de ideas para resolver el problema tal como lo entendemos, utilizando patrones, tecnología y otras soluciones.
	- **Hacer**:
	    - Modela el sistema para tener algo concreto sobre lo que razonar y compartir.
	- **Evaluar (Evaluate)**:
	    - Pone a prueba nuestros modelos y requisitos.
- **Cambios de Mentalidad**:
    - Las mentalidades cambian con frecuencia y rapidez. Durante una sola conversación, podemos cambiar de mentalidad varias veces. En un taller, se crean situaciones que obligan a los participantes a adoptar nuevas mentalidades para llegar a un resultado deseable.
- **Arquitectos Experimentados**:
    - Los arquitectos experimentados suelen atacar la arquitectura desde diversas perspectivas de forma instintiva gracias a años de práctica. Ser consciente de las cuatro mentalidades de diseño nos proporciona nuevas técnicas para salir de un estancamiento. Si te quedas atascado, elige una nueva mentalidad para desbloquearte.
![[Pasted image 20240810031044.png]]

## Ejemplo practico

Un interesado nos da una nueva restricción que podría afectar el rendimiento del sistema.

- **Pensar**: Sabemos que el rendimiento es crucial, pero no tenemos claro qué significa "buen rendimiento" en este contexto. Adoptamos la mentalidad de **entender** y decidimos capturar escenarios de rendimiento.
    
- **Hacer**: Creamos y documentamos algunos escenarios de rendimiento.
    
- **Verificar**: El equipo y los interesados revisan y dan feedback sobre los escenarios.

Surgen nuevos riesgos. ¿Podemos cumplir con los requisitos de rendimiento bajo esta nueva restricción?

- **Pensar**: Adoptamos la mentalidad de **evaluar** y planeamos un experimento para probar cómo la restricción afecta el rendimiento.
    
- **Hacer**: Escribimos scripts simples, recopilamos datos y ejecutamos el experimento.
    
- **Verificar**: Los resultados muestran que la restricción impacta el rendimiento, pero solo ligeramente.

Aunque el impacto es pequeño, necesitamos mostrar esto a los interesados para evaluar su gravedad.

- **Pensar**: Para comunicar mejor el problema, adoptamos la mentalidad de **hacer** y creamos un prototipo que simula el impacto en el rendimiento.
    
- **Hacer**: Desarrollamos un prototipo que demuestra el flujo de trabajo y las posibles caídas de rendimiento.
    
- **Verificar**: Los interesados experimentan la desaceleración y comprenden que el impacto no es aceptable.

El prototipo reveló un problema que no habíamos anticipado. Luego, volvemos a **entender** para ajustar los requisitos y pasamos a **explorar** nuevas soluciones. Así, el ciclo continúa.

El ciclo de pensar-hacer-verificar es flexible y se adapta según la situación, el equipo y la experiencia.