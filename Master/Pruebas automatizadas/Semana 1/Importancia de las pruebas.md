Tags #QA 

Las pruebas son un practica para asegurar la calidad de nuestro producto, sin embargo, esta no es la unica manera de medir la calidad.

![[Pasted image 20241011201620.png]]

Las pruebas siempre deben ser realizadas en cada etapa del desarrollo con el fin de:

1. Explorar el espacio de estados y entradas del sistema.
2. Reducir la probabilidad de que un defecto aparece
3. Encontrar desviaciones e incosistencias de la implementacion
4. Encontrar desviaciones del diseno con respecto a lo que los usuarios finales quieren y necesitan

>[!IMPORTANT]
>Basicamente las pruebas deben promover la mejora continua de la aplicacion y no solo el control de defectors en un momento dado

## Verificacion y validacion?

***Validar*** refiere a probar que el producto haga lo que debe hacer
- Interna: El software hace lo que dice los requerimientos
- Externa: El software hace lo que debe ser desde el punto de vista del usuario

***Verificar*** refiere a medir o evaluar si el software cumple las especificaciones de diseno, nuestras arquitecturas o estandares de calidad del codigo.

Las prueba de software usualmente ***validan***

***Analisis estatico***: Esto significa analizar el codigo sin ejecutarlo como  lo pueden ser la revision del codigo manual o la verificacion manual (Sonar)
***Analisis dinamica***: Esto significa analizar el codigo en ejecuccion como lo pueden ser la pruebas de software y depuracion
