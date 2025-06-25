---
tags:
  - master
  - Agilismo
---

| Clase      | Atributos                        | Metodos                                                                                                                                     | Preguntas                                                                                                                                                                                                                                                          |     |
| ---------- | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --- |
| Usuario    | email<br>clave                   | setEmail(email: string) : void<br><br>getEmail(): string<br><br>setPassword(password: string): void<br><br>getPassword(): string            | Que se refieren con informacion del usuario fuera de la normal como correo y contrasena?<br><br>El administrador puede apostar a una carrera desde su cuenta de admin?<br><br>Necesitamos un historial de las apuestas por persona?                                |     |
| Carrera    | uuid<br>nombre                   | getUUID(): UUID<br><br>setNombre(nombre: string): void<br><br>getNombre(): string                                                           | La carrera no cuenta con un rango de tiempo de fecha de inicio y/o fecha de finalizacion?<br><br>es necesario saber la modalidad de la carrera (caballos, carros)?<br><br>Importa la edad de la persona?<br><br>Necesitamos el historial apuestas por carrera?<br> |     |
| Competidor | nombre<br>winningProbability<br> | getName(): String<br>setNombre(nombre: string): void<br><br>getWinningProbability(): float<br><br>setWinningProbability(probability): float | Las probabiliades del competidor pueden ser cambiadas una vez guardadas?<br><br>es necesario llevar un historial de que competidores-carreras?                                                                                                                     |     |
| Apuesta    | uuid<br>usuario<br>carrera<br>   |                                                                                                                                             | Es necesario saber cuando se hizo y/o se modifico?                                                                                                                                                                                                                 |     |
|            |                                  |                                                                                                                                             |                                                                                                                                                                                                                                                                    |     |


- Solo puedes borrar una persona si no tiene apuestas.
- La apuesta se modifica todo menos la carrera y mientras no este terminada
- Editar competiciones mientras no termina
- No alminar competidores si tienen apuestas
- Competiciones no se repiten entre carreas
- Carreras ordenadas alfabéticamente
- No hay admin 
- Del usuario solo su nombre

#master
#Agilismo