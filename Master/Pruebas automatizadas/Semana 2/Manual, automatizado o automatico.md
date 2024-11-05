Tags #QA 

# Prueba manuales
Son pruebas realizadas ***por personas directamante***, estas se carcterizan por ser muy valiosas, pero bastantes costosas.

Por eso mismo siempre debemos optimizar el consumo y distribucion de los recursos de pruebas.


# Pruebas automaticas
Son pruebas que ***no requieren intervencion humana***, estas generan:

- Reporte
- Instrucciones de ejecuccion
- Trazabilidad del error

Esto se puede ver que no requiere intervencion humana en ningun paso, y debe cumplir con esto si o si:

- Ejecuccion autonoma
- Generacion de reportes sin intervencion humana
- Generacion automatica de secuencias de eventos
- Oraculo inferido automaticamente.

# Pruebas automatizadas
Son pruebas que existe ***soporte de una maquina para la generacion o ejecuccion*** de la prueba, sin embargo, aun tiene componente humano.

>[!NOTE]
>Combinacion de esfuerzos


>[!IMPORTANT]
>Toda prueba automatica es automatizada, pero no toda prueba automatizada es automatica


# Oraculo de pruebas

Mecanismo que nos permite determinar si una prueba es exitosa o fallida, es decir, el conjunto de comportamientos de los resultados esperados al ejecutar una prueba.

- Usualmente definido por quien disena o ejecuta la prueba
- Derivvados de los requerimientos o conocimientos previo de la empresa o tester
- Generacion automatica de oraculos es un problema abierto de investigacion

## Tipos de oraculo
- ***Especificados***: Generados a partir de un **modelo**, o **diseno**, que especifica el comportamiento o salida esperada.
- ***Derivados***: Inferidos a partir del **comportamiento del sistema** u otro elemento de referencia
- ***Implicitos***: Basados en **conocimiento genenral** sobre el comportamiento o salida esperada.

