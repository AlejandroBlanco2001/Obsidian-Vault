Tags: #arquitectura-de-software #web 

Algunas caracteristicas de las aplicaciones web actuales son:

- Diseno adaptativo
- Una sola pagina
- Accessibles
- Internacionalizables
- Progresivas
- IoT
- Sensores

Dentro de este curso, abordaremos las 4 primeras

- Adaptativa: Se ajusta al tamano del dispositivo donde se abre el navegador
- SPA: No necesitamos realizar un refresqueo de una pagina para ver e interactuar con estos cambios
- Accesible: Permite que las personas con alguno tipo de discapacidad pueda utilizar nuestra pagina
- Internacionalizacion: Disena para ser usada por distintas culturas.

## Historia

El nacimiento del protocolo de HTTP fue fundamental para la creacion de esto.

El flujo basico inicial trabaja sobre esto;
- Cliente -> Servidor (Request)
- Servidor -> Cliente (Response)

El problema con esto era que la pagina que se entregaba siempre era la misma, para solucionar esto nacio el modelo CGI/HTTP

El cambio radica que ya no se devuelve un archivo HTML, por lo contrario, ahora puede devolver un programa 

Una posterior evolucion fue el modelo (stack) LAMP, que significa

- Linux (OS sobre el que se ejecuta el servidor web)
- Apache (Servidor web)
- PHP (Lenguaje de progrmacion)
- MySQL (Base de datos)

> [!NOTE]
> Recordemos que la comunicacion es unidireccional

Con la popularizacion de JavaScript, nace el modelo AJAX que significa ***AsynchronousJavascriptAndXML***

Luego de la carga de la pagina web, estas usando el objeto XHR (peticiones asincronas) permiten no bloquar la pagina y cargar solo los nuevos cambios dentro de nuestra pagina 

>[!IMPORTANT}]
> Esto es la piedra angular de la metodologia REST API

Los frameworks mas populares del lado del cliente contamos con:
- Angular
- React
- Vue

>[!NOTE]
> La mayoria se basa en el modelo MVC


