---
tags:
  - git
  - CI/CD
  - Agilismo
  - master
---
Los distintos tipos de merge: 

- ***Fast-forward:*** Cuando tenemos dos ramas, y estan al dia, es decir, el ultimo commit de A, es el inicial de B), simplemente movemos el HEAD, a la ultima version de B

- ***Merge***: Cuando tenemos dos ramas, y están no están al día, es decir, B sale de algún commit que no es el ultimo de A, se genera un nuevo commit con el cambio combinado de ambas versiones.

Esto se describe de una mejor manera en la note [[Patterns for Managing Source Code Branches]]
