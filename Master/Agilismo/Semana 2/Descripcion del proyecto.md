Para el proyecto todo se manejara dentro de GitHub, en las historias de usuario, probablemente sera mas facil usar el apartado de **Projects** para que todo sea mas facil:

***Ejemplo***

| Código                                                                       | Nombre       | Descripción                                                                                                                                                                                               | Responsable  |
| ---------------------------------------------------------------------------- | ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| [HU001](https://github.com/MISW-4101-Practicas/TutorialCanciones/wiki/HU001) | Crear álbum  | Como coleccionista de música quiero crear un nuevo álbum para organizar las canciones y encontrarlas fácilmente. Esta HU es necesaria pues hace parte de las funcionalidades más importantes del sistema. | <<@usuario>> |
| [HU002](https://github.com/MISW-4101-Practicas/TutorialCanciones/wiki/HU002) | Editar álbum | Como coleccionista de música quiero editar un álbum para actualizar o corregir la información. Esta HU es necesaria pues hace parte de las funcionalidades más importantes del sistema.                   | <<@usuario>> |
Dentro de la misma debemos tener la Revision con todos los criterios especificados por los lineamientos.

Historia detallada: [aca](https://github.com/MISW-4101-Practicas/TutorialCanciones/wiki/HU001)
Revision: [aca](https://github.com/MISW-4101-Practicas/TutorialCanciones/wiki/f03#revisi%C3%B3n)

## Cronograma

Semana 2:
- Se construye un modelo conceptual usando un diagrama de clases en UML para ayudar en el entendimiento del problema y se construye un glosario de términos.
- Se identifican los requerimientos y se contruye un listado de historias de usuario.

Semana 3:
- Se configura el espacio de documentación del proyecto en GitHub, el tablero de actividades para el seguimiento del proyecto  y el repositorio en sistema de control de versiones GIT donde se gestionará el código del proyecto.
- Se realiza el detalle de las historias de usuario.

## Enunciado puntos claves

- La solucion a desarrollar es ***"E-Porra"***
- Permite a un usuario administrar apuestas alrededro de carrera de cualquier tipo (caballos, formula 1, atletismo. etc)
- El usuario puede llevar el registro de las apuestas que hacen los apostadroes en un carrera, con el proposito de poder pagar correctamante a quienes hayan acertado el resultado.
	- El usuario puede organizarlas
- El ***usuario administrador***, debe abrir una pantalla donde encontrara una descripcion de "E-porra", acompanado de un listado de las carreras que tiene registrada.
	- El ***usuario administrador*** puede abrir, editar, terminar o borrar (siempre y cuando no tenga carreras).
	- Opcion de crear una nueva carrera con un nombre (requerido).
		- Nombre de cada competidor
		- Probabilidad de ganar de cada competidor (0-1), su suma debe dar 1
		- Al finalizar la apuesta, se genera un reporte con los porcentajes de cada uno de los ganadores y que ganancias o peridas tuvo el organizador "la casa"
	- El usuario puede ver una lista de apostadores existentes en el sistema, desde ahi puede:
		- Adiccionar un nuevo apostador
		- Editar informacion (que?)
		- Borrarla (si no tiene relacion con alguna apuesta)
- Cuando el usuario apostador, habra una nueva carrera, vera una pantalla con la informacion asociada a esta, mostrando:
	- Cada apuesta el valor
	- Nombre del apostador quien la hizo
	- Compeditor al que aposto
	- Puede apostar varias veces en una misma carrera
	- Editar o elminar la apuesta

### Calculo de las probabilidades

- Quien pierde, perdio, 0 ganancias.
- Las ganancias para los demas se cacula basado en una cuota, para recibir su ***cuota*** se usa la siguiente formula:
$$
couta=\frac{probabilidad}{1-probabilidad}
$$
- Luego con esta formula, calculamos las ***ganacias***

$$
ganancia = apostado + (\frac{apostado}{couta})
$$
- La ganancia de la casa corresponde a la suma de todas las apuestas menos el total pagado a los apostadores que acertaron el ganador por concepto de sus ganancias. 
	- Un valor negativo de ganancia de la casa indica que la casa debe colocar dinero adicional para cubrir el total a pagar en las apuestas ganadoras, es decir la casa pierde dinero.

De la lectura, salen las siguientes preguntas y desmunzado de la lectura para las clases

[[Modelo de clases y preguntas al cliente]]