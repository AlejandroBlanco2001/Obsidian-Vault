Tags #QA 

 Recordemos que los Monkey y los Ripper se basan en distrubuciones de datos para elegir y alcanzar ciertos estados, esto tiene su ventaja:

- Datos de entrada aleatorios
- Comportamiento erratico

Recordemos que un Monkey es un sujeto tonto, y que con el tiempo se va ejercitando y mejorando hasta ser muy preciso, es decir, al inicio probablemente no encontrara nada util o se quedara atascado. Por ende, este puede demorar en ser util

Un Ripper es como un Monkey pero mas consciente de que hace.

Para ambos casos podemos ejecutar con una semilla (para que pueda ser reproducible) o sin semilla (sin reproducir)

- Si usamos una semilla, debemos tener todo poblado, para tener el mismo resultado, sin eso, no podemos hacer nada util.

