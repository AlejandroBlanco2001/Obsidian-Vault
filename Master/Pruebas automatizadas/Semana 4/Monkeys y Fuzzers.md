Tags #QA #PruebasAutomaticas

# Pruebas de reconocimiento

Son las pruebas que ejecutamos para realizar un analisis inicial de la aplicacion bajo pruebas en la GUI, en estas podemos utiilizar varias tecnicas:

- Monkeys (basicamente pruebas aleatorias)
- Ripping (Pruebas de exploracion sistematica)

En este caso, el **oraculo** de las pruebas no es fijo ni explicito, este es mas bien implicito.

## Monkeys

Este nace de la ***teoria del mono infinito***, donde suponemos que si tenemos un mono que golpea de una manera aleatoria un teclado, eventualmente, el mono seria capaz de escribir la obra completa de Cervantes. 

Este parte de la generacion aleatoria de:

- Eventos
- Datos

Dentro de sus beneficios, estan:

- Economicas
- Rapida ejecucion
- Buena para detectar casos "raros"
- Permite generar un modelo de la aplicacion

Dentro de sus desventajas, estan:

- Estancamiento, debido a que no es posible el movimiento de estado (Login a otras paginas)
- Replicabilidad de la secuencia de eventos generados puede ser compleja
- Expresividad de los resultados obtenidos (legible)


## Recordatorio sobre Oraculos

### Especificados

Generados a partir de un ***modelo***, o ***diseno***, que especifica el comportamiento o salida esperada.

### Derivados

Inferidos a partir del ***comportamiento de sistema*** u otro elemento de referencia.

### Implicitos

Basados en conocimiento general sobre el ***comportamiento general*** sobre el comportamiento o salida esperada.

# Prueba de regresion

Son las pruebas que ejecutamos que para verificar que algo no se rompio entre versiones, es decir, tenemos una version X, donde ejecutamos las pruebas de reconocimiento, salen unos errores, corregimos para la version X+1 y las mismas pruebas actuan como correcion (Regresion).

![[Pasted image 20241102114744.png]]