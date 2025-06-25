---
tags:
  - tacticas-arquitectura
  - arquitectura-de-software
  - master
  - modificacion
---

Contamos con el patron de MVC, por sus siglas en ingles, Model-View-Controller, y tenemos el MVVM, por sus siglas en ingles, Model-View-ViewModel.

# MVC

Busca favorecer la asignacion de la responsabilidades, desacoplando los componentes y mejorando su cohesion.

- Modelo: Persistencia de los datos  
- Controlador: Logica de negocio
- Vista: Presentacion de los datos 

Los cambios deben ser realizados de manera manual, donde el modelo conoce a la vista y la notifica
# MVVM

Busca favorecer la asignacion de la responsabilidades, desacoplando los componentes y mejorando su cohesion.

- Modelo: Persistencia de los datos
- ViewModel: Comunicacion bi-direccional entre el Modelo y la Vista
- Vista: Presentacion de los datos 

En este caso, el ViewModel no se comunica con la vista

