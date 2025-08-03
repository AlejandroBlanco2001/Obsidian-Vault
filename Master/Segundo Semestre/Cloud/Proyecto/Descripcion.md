La **Asociación Nacional de Baloncesto**  (ANB) nos ha contratado para desarrollar temas de modernización tecnológica en sus procesos.

Se creo la iniciativa  "**ANB Rising Stars Showcase**" que es un programa que busca descubrir a los mejores jugadores aficionados de diferentes regiones del pais, dándoles la oportunidad de competir en un torneo de exhibición frente a los cazatalentos de la liga.

El **Rising Stars Showcase** es una competencia abierta que abarca varias ciudades en el territorio nacional. Los jugadores aficionados podrán enviar videos cortos mostrando sus habilidades (entrenamientos, jugadas destacadas, lanzamientos, etc.) como parte del proceso de preselección.

Por ende, se busca desarrollar una plataforma web que permita:

- Centro de carga
- Almacenamiento y evolución de los videos
- Votacion por parte de personas y jurados especializados
# Requerimientos
- Los jugadores podrán registrarse, crear un perfil y subir sus videos de prueba
- La plataforma deberá realizar **procesamiento automático** de los video subidos:
	- Recorte de duración a un máximo de **30 segundos**
	- Ajuste de resolución y formato de aspecto
	- Inclusion del del logo oficial de la ANB al inicio y final del video
- El publico podrá ver los videos y votar
- Se genera un **ranking dinámico**, mostrando los jugadores mas votados
- Las votaciones deben ser controladas para evitar fraudes o multiples votos por el usuario.

# Impacto
Con el fin de optimizar la experiencia del usuario, la conversión de archivos se ejecuta mediante tareas asíncronas o procesos batch. Al finalizar el procesamiento, el estado del archivo se actualiza automáticamente a **"procesado"**.

Como se mencionó previamente, **se requiere implementar unicamente el backend** **y la capa de procesamiento asíncrono de la aplicación** para habilitar a los usuarios interesados en explorar la plataforma. .

#  **Análisis de capacidad**

Como se mencionó en los objetivos, una de las metas es escalar la aplicación para soportar varios cientos de miles de usuarios, razón por la que en cada una de las iteraciones del proyecto **deberá ejecutar pruebas de carga que evalúen métricas como la capacidad de procesamiento, tiempos de respuesta, concurrencia de usuarios en la aplicación y cargas de trabajo artificiales.**

> En todas las entregas del proyecto, las pruebas le permitirán comprender cómo la aplicación web y su infraestructura se comportan ante diversos niveles de carga de usuarios, alcanzando la escala de los cientos de miles.

Las pruebas de carga deberán atender interrogantes como:

- ¿la aplicación responde rápidamente?
- ¿cuántos usuarios puede manejar la aplicación con la infraestructura que actualmente la soporta?
- entre otros.

# Tecnologías 

- **Python**: 3.13 o superior. 
    
- **Frameworks:** Flask 3.1.x o FastAPI 0.115.x 
    
- **Sistema operativo**: Ubuntu Server 24.04 LTS.
    
- **Servidor web**: Nginx, configurado como proxy inverso.
    
- **Servidor de aplicaciones**: Gunicorn o Uvicorn, como servidor WSGI para la ejecución de la aplicación Python.
    
- **Motor de base de datos**: MySQL o PostgreSQL. No se acepta SQLite.
    
- **Celery**: para la gestión de tareas asíncronas, utilizando **Redis** o **RabbitMQ** como brokers de mensajería.
    
- Alternativamente, se puede usar **Kafka** en lugar de Celery, considerando que esto modifica la arquitectura hacia un modelo Pub/Sub.