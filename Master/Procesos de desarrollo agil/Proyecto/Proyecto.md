## Contexto previo 

Empresa: Soft One

> “En Forma”, una aplicación que le permite a un entrenador gestionar todo lo relacionado con los ejercicios que realizan las personas que entrena.

Contamos con una versión inicial del programa, por lo tanto, contamos con un esqueleto ya montado (no es de cero).

> Entidades: Entrenador, Entrenados, Ejercicios

Al momento de iniciar la aplicación, el entrador ve una pantalla  principal con el **listado de personas que entrena**, opciones para **agregar una nueva persona** y para acceder **a los ejercicios disponibles**.

Dentro del ***listado***, cada persona tiene las opciones de:
- Editar su información
- Ver los entrenamientos que ha realizado
- Retirar a la persona
- Borrar su información
	- Siempre y cuando no tenga entrenamientos registrados

Dentro de las ***opciones de mostrar los entrenamientos de las personas***:
-  Listado de ejercicios que ha realizado
	- Nombre del ejercicio
	- Fecha
	- Cantidad de repeticiones
	- Tiempo que le tomo en HH:MM:SS
- Agregar uno nuevo
- Editar uno existente
- Borrar  uno existente
- Botón para obtener el IMC y su categoría
	- Calculo del consumo calórico por cada fecha en la que se ha entrenado

Para la opción de ***agregar una persona***: 
- Registrar
	- Nombre
	- Apellidos
	- Fecha de inicio
	- Talla
	- Peso
	- Edad
	- Medidas en cm
		- Brazos
		- Pecho
		- Abdomen
		- Cintura
		- Piernas

Para la opción del ***listado de ejercicios***:
- Listado de los ejercicios disponibles que se utilizan en los entrenamientos
- Crear ejercicios
	- Nombre
	- Descripción
	- Aproximación de calorías quemadas por repetición
	- Video de YouTube
- Editar el ejercicio existente
- Borrar el ejercicio existente
	- Solo si no esta en uso

> Objetivo: Necesitamos crear un MVP para obtener una ronda de financiamiento

Por ende debemos:
- Mejorar la UI
- Mejorar la navegación (UX)
## Funcionalidades nuevas 

### Extender que el entrenado pueda ser la aplicación también

El entrenado debe poder:
- Consultar la información de los entrenamientos que ha realizado
- Gestionar su información personal
- Reporte de sus entrenamientos
	- Incluir el que?
- Durante la creación, se debe asignar usuario y contraseña

### Creación de rutinas
- Crear rutinas de entrenamientos.
- Una rutina creada, es disponible para cualquier entrenador.
- Una rutina puede ser asignada a cualquier cliente.

Nombre?
Coste calórico?

### Creación de un administrador
- Un administrador para gestionar los entrenadores
- Agregar un entrenador
	- Registrar su información personal
		- Nombre
		- Identificación
		- Apellido
		- Teléfono
		- Dirección
	- Asignarle usuario y contraseña
- Editar entrenador
- Borrar entrenador
	- Si no tiene nadie entrenando
