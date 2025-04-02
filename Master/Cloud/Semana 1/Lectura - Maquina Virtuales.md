9Tags: #maquinas-virtuales

Recordemos que en un enfoque tradicional (o un computador físico), se instala y se ejecuta en un sistema operativo.

![[Pasted image 20250330163402.png]]

Para esto nace algo llamado *virtualización*, esto es una tecnología que crea recursos lógicos y los agina a recursos físicos. Este es posible haciendo uso de una capa especifica de hardware llamada el **hypervisor** .

La principal idea es desacoplar el hardware del software para dividir y compartir recursos entre varias cargas de trabajo, maquinas virtuales y/o contenedores.

Alguna de las ventajas de las maquinas virtuales es:
- Podemos correr multiples maquinas virtual es con diferentes servicios en una sola maquina física
- Contar con maquinas independientes permite aislar los problemas y continuar parcialmente con la operación
- No necesitamos tantos costos para crear ambientes personalizados rápidos y flexibles
- No todas las aplicaciones aprovechan la escalabilidad vertical de una maquina, permitiendo que estas maquinas virtuales solo usen las que estrictamente necesitan.

# Maquinas virtuales
Esto es algo que podemos hacer debido a que existe el componente llamado *monitor* (MMV), nuestras maquinas virtuales hacen uso de este MMV para poder controlar los recursos y dar los accesos.

Este es el programa encargado de construir y administrar el ambiente para las maquinas virtuales

![[Pasted image 20250330164157.png]]

Cada ambiente de ejecucción es conocido como maquina virtual huésped (guest), mientras que el servidor sobre el que corren las maquinas se conoce como anfitrión (host) 

Teniendo en cuenta lo antes mencionado, usemos este ejemplo

> Entonces, si tiene un servidor con 8 núcleos en CPU y 16 GiB en RAM que ejecuta un manejador (hipervisor), puede crear fácilmente una o varias máquinas virtuales con 2 núcleos y 2 GiB en RAM cada una e iniciarlas. Los límites con respecto a la cantidad de máquinas virtuales que puede iniciar es algo que se basa en los límites físicos del hardware real y en las restricciones definidas por el manejador (típicamente asociadas a buenas prácticas y licenciamiento).

Contamos con dos tipos de hypervisors
- Tipo 1 o bare metal: El MMV esta a cargo de todos los recursos y corre directamente sobre la maquina, sin la necesidad de un sistema operativo en la mitad. Algunos ejemplos son VMware EXSi y Red RHEV-H

![[Pasted image 20250330164611.png]]

Estos son fáciles de configurar e instalar y de un tamaño bastante pequeño para entregar la mayor cantidad de los recursos a las maquinas virtuales huéspedes. Consumen pocos recursos

- Tipo 2 o hosted: Este se ejecuta sobre un sistema operativo, lo que permite realizar numerosas personalizaciones 

![[Pasted image 20250330164846.png]]

La principal ventaja es que al tener un SO en la mitad tenemos una alta computabilidad con el hardware, debido a que el SO se encarga de manejar estos temas. Algunos ejemplos pueden ser como VMware Player o Fusion.

Debemos recordar que aunque hacen lo mismo, al tener un SO, los hypervisors de tipo 2 cuentan con una mayor latencia, y de igual manera, si el SO tiene una vulnerabilidad, nuestra maquina virtual también lo esta.

Recordemos que alguno de los criterios para seleccionar el uno o el otro depende exclusivamente de la tarea a realizar:
- Tipo 1 (Datacenters): Mayor seguridad y rendimiento
- Tipo 2 (Usuarios finales): Mayor flexibilidad

Independiente de lo que hagamos, o usemos, siempre deben garantizar lo siguiente
- Seguridad
- Fidelidad
- Eficiencia