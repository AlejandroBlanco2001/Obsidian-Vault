---
tags:
  - master
  - cloud
  - docker
  - Lectura
---
Lectura sobre **Container Security (Liz Rice )**

# Capitulo 1 sobre la sección Container Threat Model
Como todo sistema, los contenedores tienen sus problemas pero poder pensar en ellas debemos comenzar por el apartado de *quienes estan involucrados*:
- Atacante externo - Alguien que intenta acceder al deployment
- Atacante interno - Alguien que logre acceder al deployment
- Actor malicioso interno - Desarrolladores o administradores que cuenta con permisos del deployment
- Actor interno involuntario - Alguien que sin querer puede causar problemas
- Procesos de la aplicacion - De pronto ofrecen formas de acceder al sistema desde ellos

Al momento de razonar sobre ellos debemos considera que permisos tiene cada uno:
- Que acceso tienen usando credenciales
- Que permisos tienen dentro del sistema
- Que permiso de red tienen 

Para poder planear un ataque podemos verlo desde la siguiente perspectiva y explora cada superficie de ataque según la sección donde estamos

![[Pasted image 20250804235823.png]]

- Codigo de la aplicacion vulnerable: Este es el primer pilar de ataque; las imágenes y dependencias con la cual contamos en nuestro codigo estan expuestas a *vulnerabilidades*, es nuestro deber escanear nuestras imágenes y actualizar nuestras dependencias.

- Configuración mal hecha dentro de la imagen del contenedor: Luego de tener nuestras imagens armadas, debemos configurar nuestra imagen, pero que pasa si: *damos privilegios de root al ejecutor*, o por ejemplo, le damos *mas permisos de los necesarios*?, esto siempre debe ser evitado

- Ataques a la maquina de construcción (Build machine attacks): Si alguien puede modificar la forma en que la imagen es construida, esto expone *un peligro para nuestro contenedor final*.

- Ataque de cadena de suministros (Supply chain attacks): Supongamos que logramos construir nuestra imagen sin problemas, y la subimos a nuestro registro; Pero que pasa si al momento del pull alguien *logra entrometerse en el proceso (tampering)*, y darnos una imagen distinta a la nuestra.

- Contenedores mal configurados: Al igual que antes, los contenedores pueden contener errores de configuración, privilegios de mas y así, *nunca debería ejecutar un YAML que descargaste sin revisarlo*

- Maquina host vulnerable: Nuestros contenedores correrán sobre maquinas host, debemos siempre revisar que estas no corran software con herramientas vulnerables, es una buena idea *siempre tener la menor cantidad de software instalado en estas maquinas*

- Secretos expuestos: Siempre debemos validar como nuestras herramientas pasan los secrets a nuestros contenedores y su codigo

- Red insegura: Debemos siempre validar las reglas de red de nuestros contenedores para evitar intrusiones en su comunicación y/o funcionamiento.

- Fuga de contenedores (Container escape vulnerabilities): Nuestros ejecutores de codigo como `containerd` y `CRI-O` son bastante robustos, sin embargo, existe el chance de que algún día pueda pasar que cierta capa de codigo se escape del contendor y se ejecute en la maquina host. *En estos casos, siempre debemos considerar maneras mas seguras de aislar nuestro maquinas/contenedores.*
# Capitulo 6 sobre la sección Dockerfile best practices for security

Al igual que protegemos nuestras maquinas (el contenedor), debemos empezar por proteger nuestra imagen de Docker:

- Base Image
	- Siempre trata de usar tu imagen de un registro seguro
	- Algunas imágenes de terceros pueden estar con codigo malicioso
	- Cuanto mas pequeña es la imagen, mas probable que no tenga codigo malicioso, por ende, la superficie de ataque es mas pequeña.
		- Construir desde cero para binarios
		- Imágenes mínimas
	- Ten en cuenta si usas una etiqueta para traer o un digest, usar un digest hace tu imagen mas reproducible, sin embargo, deja la puerta abierta a versiones vulnerables.
- Multi-Stage builds
	- Esto es una forma de quitar cosas innecesarias de la imagen final
	- Por ejemplo, podemos tener un stage en Go que traiga todas las dependencias para compilar, luego, hacemos otro stage que copie estos a la imagen final y quedarnos solo con el binario necesario.
- Nada de usar el Root
	- Evitar usar el usuario root para correr comandos y ejecutar el contenedor, la instrucción `USER` logra esto
- Comandos `RUN`
	- Este comando te permite ejecutar cualquier codigo arbitrario en tu maquina, por ende, es necesario evitar que cualquier persona ataque nuestra imagen (y menos tener esta con las configuraciones por defecto)
	- Siempre trata de ajustar usuarios, reglas y permisos dentro de la misma para evitar esto
	- Audita dichos comandos y sus usos
- Volúmenes
	- Cuando hacemos un mount debemos evitar que montemos carpetas sensibles
- Datos sensibles
	- No guardar nada sensible en la imagen de docker
- Binarios setuid
	- No debemos guardar dichos binarios para evitar escalo de privilegios
- Evita montar cosas innecesarias
	- Cuanto menos guardemos en la imagen, mas pequeña son y menos superficie de ataque tenemos.
- Incluye todo lo que tu contenedor necesita
	- Todo lo que el contenedor necesita, que lo tenga de antemano, no des la opción de descargar dependencias de manera dinámica