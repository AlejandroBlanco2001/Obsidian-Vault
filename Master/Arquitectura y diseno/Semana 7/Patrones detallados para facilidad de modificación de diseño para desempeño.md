El atributo de calidad de facilidad de modificacion se refiere a disminuir:
- Menor tiempo posible
- Menor esfuerzo posible
- Menor impacto posible

Uno de los principales problemas de los objetos, es el proceso de ***creacion***, y luego la asignacion de su responsabilidad como lo es discutido en los patrones ***GRASP***,de igual manera, esto es tratado por los patrones ***SOLID***.

Algunos de los patrones que podemos usar:
- Creacion (GoF)
- Creador (GRASP)
- Inversion de dependencias (SOLID)

![[Pasted image 20240921004259.png]]

Aproximacion 1

![[Pasted image 20240921004318.png]]

En este caso, si el software escala, el Envio deberia cambiar porque el Envio y la Notificacion pueden cambiar o incluir nuevas cosas.

Aproximacion usando la inversion de control
	![[Pasted image 20240921004532.png]]
