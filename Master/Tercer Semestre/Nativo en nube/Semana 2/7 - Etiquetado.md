---
tags:
  - master
  - cloud
---
El etiquetado de imágenes de docker nos permite manejar versiones de nuestras imágenes, al no estipular ninguno por defecto usara ***:latest*** 

``` bash
docker build -t my_app .
docker images
  
# REPOSITORY TAG IMAGE ID CREATED SIZE
# my_app latest e57c61022b1e 11 seconds ago 156MB
```

El problema con no estipular la imagen, hace que al correr de nuevo el comando nuestra imagen actual sea huérfana o "dangled".

```bash
docker build -t my_app .
docker images


# REPOSITORY TAG IMAGE ID CREATED SIZE
# my_app latest ad218e45c717 11 seconds ago 156MB
# <none> <none> e57c61022b1e 2 minutes ago 156MB
```

# Como se debería hacer
Debe ser una etiqueta legible que nos permita saber una version de nuestra imagen (semver, por ejemplo)

```bash
docker build -t my_app:1.0.0 .
docker images

# REPOSITORY TAG IMAGE ID CREATED SIZE
# my_app 1.0.0 29e57ae3edc2 1 minute ago 156MB
```

