---
tags:
  - mobile
  - master
---
Las aplicaciones fueron evolucionando, debido a que tener una aplicacion por cada sistema operativo implicaba mucho coste:

- Capacitación de la gente
- Recursos físicos
- Limitaciones

Sin embargo, nacieron frameworks bajo la mentalidad **WORA** (Write Once Run Anywhere) que favoreció el nacimiento de las aplicaciones multi-proformas (cross-platform). Actualmente tenemos cinco tipos de aplicaciones:

- Aplicaciones nativas
	- Mejor desempeño
	- Mayor acceso a recursos
	- Android con Kotlin, iOS con Swift
	- Presenta inconsistencia de comportamiento
		- Misma app con funcionamiento diferentes para cada plataforma
	- Inconsistencia de interfaz
		- Misma app con diferente interfaz grafica para cada plataforma
- Aplicación "cross-platform" nativas
	- Siguen la filosofía WORA
		- Flutter compila Dart para luego ser compilado a nativo
	- Flutter y React Native son ejemplos
- Aplicaciones hibridas
	- Compuesto de una parte nativa con un parte web
		- Uso del explorador web WebView, que se encarga manejar los archivos web y APIs nativas
		- Requiere instalación
		- Ionic es un ejemplo
- Aplicación web progresivas (PWA)
	- Mismas restricciones de hardware que las aplicaciones web
	- Escenarios fuera de linea
	- Restricciones de aplicación web
- Aplicaciones web adaptadas para dispositivos móviles
	- No se requiere instalación
	- Soporte limitado para escenarios 'off-line'
	- Acceso limitado a los recursos
	- Bajos costos de desarrollo

La elección de nuestra herramienta depende de nuestros requerimientos.
