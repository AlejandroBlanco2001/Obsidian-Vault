---
tags:
  - arquitectura-de-software
  - Lectura
LInk: https://www.youtube.com/watch?v=czzAVuVz7u4&t=1070s
---
- Un codigo complicado no es lo mismo que un codigo complejo
- Hay (posiblemente) tres razones para que un software se vuelva complejo
	- Codificación defensiva
	- Escalado
	- Abstracciones débiles
	- Perdida de idea entre el problema y el desarrollador

# Razones

## Codificación defensiva
- Strong parsing - Una validación se propaga y no siempre la hace en todo el codigo
- Librerías quitan estas complejidades (el uso de tipos también)
- Vigilancia no es una estrategia
- ***Menos grados de fallas y simplificar valores conocidos***

## Escalado
- Usuarios (o la carga) puede crecer exponencialmente
- Problema algorítmico ya esta resuelto, pero nacen nuevas necesidades como:
	- Legales
	- Éticos
	- Manejo de datos
	- Tecnologías a usar
- ***Escalar es un problema en si***
- ***Reconstruir por cada gran cambio, debe ser una mentalidad siempre latente***

## Abstracciones débiles
- Como copiar una cadena
	- Implementación inicial = sencilla
	- Implementación actual = misma idea, pero con mas optimizaciones, por ende mas compleja
- Las interfaces son iguales pero las optimizaciones causan cambios
- ***El uso de Interfaces nos permite esconder la complejidad***
- ***La falta de comprensión causa poderes o irreverencia***

## Perdida de idea entre el problema y el desarrollador 
- El codigo no refleja el dominio del problema, por ende, podemos:
	- Re-escribir lado
	- Ignorarlo
	- Parchearlo
- ***Asumir es peligroso***

> [!IMPORTANT]
> Nuestros problemas se pueden volver hiperespacios, donde contienen multiples dimensiones

Parte del ejemplo de la programación web
- 3 navegadores
- 4 LTS
- 3 dimensiones de pantalla
- 3 plataformas

Nos genera ***108 posibles combinaciones***, por ende, podemos considerar un problema la existencia de las aplicaciones multiplataforma, de igual manera toca recordar ***mucha gente nos lleva a muchos problemas***.
# Homeostasis

>[!NOTE]
>La invención del cinturón de seguridad no llevo a menos muertes en la carretera

Por ende nace, la definicion de ***homeostatis del riesgo***

>[!IMPORTANT]
>Se define como al aumentar la sensación de seguridad, provoca un crecimiento en el umbral de riesgos que estamos dispuestos a tomar.

Para nosotros como desarrolladores nace un homónimo, que seria la ***homeostasis de la complejidad***

>[!IMPORTANT]
>Si tu sistema muestra un comportamiento estable con el tiempo, eres capaz de arreglar las cosas mas rápido, por ende, no tienes miedo a introducir mas complejidad

Sin embargo nacen las siguientes preguntas:
- ***Quien o que estipula la complejidad de nuestro sistema***
- ***Al tener mas gente podemos partir la complejidad***
- ***El valor del dinero para el desarrollador, que tanto dinero te hace soportar esta complejidad***
- ***El problema del Carbon es mas o menos parecido a la complejidad del software***

# Tipos de complejidad
- Problemas de complejidad es algo que existe hace mucho tiempo
- Complejidad puede ser:
	- Accidental: Cosas que pasan pero no son inherentes al problemas (Un hack en el codigo)
	- Esencial: Cosas que pasan pero eran completamente necesarias (Resolver una ecuación diferencial en un simulador físico)

 > [!IMPORTANT]
 > ***Software Architecture degrades with the changes made to the software*** 
 
Hay maneras convencional (y otras mas extremas de acabar con ciertas complejidades), como lo puede ser buscar dependencias y erradicarlas, como lo puede ser el caso de Excel con su propio compilador de C++.

Por otro lado, también tenemos que acordarnos de que ***la complejidad no es mala***, sin embargo, nacen cosas nueva como ***lidiar con la complejidad***

- Nuevas tecnologías no implican directamente que habrá menos complejidad
- No puedes arreglar el problema, pero puedes hacer algo nuevo 
	- Iterar sobre algo siempre de cero, te vuelve cada vez mejor
	- Las cosas las cambiamos nosotros

# Como podemos lidiar con ella
- Siempre podemos cambiar el dicho de ***haz mas con menos***, a ***haz menos con menos***
	- Este te permite hacer las cosas mas visibles, mas fáciles de razonar, por ende, mas fáciles de pulir

> [!IMPORTANT]
> ***La complejidad es muy difícil de reducir, pero algo que siempre podemos hacer, es volver la solución peor de lo que ya es.***

Algunas de las alternativas actuales para ciertos problemas serian:
- La complejidad que trae el cloud, se puede atacar con ***Local First Software***
	- Que tal si hacemos que nuestro software sirva directamente en el computador primero, y usamos la nube como una colaboradora
	- Automerge es un ejemplo real

>[!IMPORTANT]
>***Arreglo computadoras que no existen, en un centro de datos el cual no conozco para personas que no conozco***

# Conclusiones
- Complejidad sucede cuando sus partes interactúan
- Complejidad es una consecuencia natural de las cosas
- Nuevas herramientas no implica menos complejidad
- No acabaremos la complejidad pero podemos "hackear nuestra idea de ella"
	- Quemar todo y empezar de nuevo
	- 0 dependencias
	- Reducir el alcance
	- Arquitecturas simples
- Tambien podemos ***abrazarlas y quererla***

> [!IMPORTANT]
> ***Nunca es mas fácil, solo vas mas rapido***