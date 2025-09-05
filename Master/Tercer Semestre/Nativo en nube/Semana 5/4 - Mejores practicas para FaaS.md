---
tags:
  - cloud
  - master
---
# Responsabilidad única
Deben seguir el principio S de los SOLID.

![[Pasted image 20250904235709.png]]
# No encadenar funciones
No debe haber llamado directo entre funciones, toda la comunicación entre ellas debe ser manejado por una fuente de información tercera (cola, cache, base de datos...)

![[Pasted image 20250904235752.png]]

# Ligeras
Las funciones deben mantener el menor tamaño posible siempre

![[Pasted image 20250904235813.png]]

# Sin estado (statless)
Ellas no deben contar con un estado interno, todo debe ser guardado por una fuente de formation tercerizada como una base datos 

![[Pasted image 20250904235855.png]]

# Entrypoint separado de lógica
Manejar un modelo donde ambas estén separadas (como lo hace Nest JS)

![[Pasted image 20250904235942.png]]

# Evite funciones de larga duración
El nombre lo dice todo, están hechas para tareas cortas y esporádicas, si estas duran una larga cantidad es menos inviable.

![[Pasted image 20250905000035.png]]

# Use colas para comunicar funciones
En lugar de pasar información entre ellas, use una cola para enviar los mensajes.

![[Pasted image 20250905000105.png]]