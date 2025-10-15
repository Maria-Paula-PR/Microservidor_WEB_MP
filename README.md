# Microservidor_WEB_MP

API para Plataforma de Cursos Online (Estilo Udemy)

Este repositorio contiene el código fuente del microservicio de backend para una plataforma de cursos en línea, desarrollado con Django y Django REST Framework.

1. Descripción del Proyecto

Este proyecto sirve como la API principal para una plataforma educativa, gestionando todos los recursos necesarios para su funcionamiento: usuarios, cursos, lecciones, inscripciones y comentarios. La arquitectura está diseñada para ser robusta, escalable y fácil de mantener, utilizando Docker para garantizar la consistencia entre los entornos de desarrollo y producción.

2. Añadir Nuevas Dependencias
Si necesitas añadir nuevas librerías de Python (como django-allauth, PyJWT, requests), debes agregarlas al final del archivo requirements.txt que se encuentra en la carpeta del backend.

# /backend/requirements.txt

Django==...
# ... otras dependencias
django-allauth
PyJWT
requests



Después de guardar los cambios, la imagen de Docker se reconstruirá automáticamente en el siguiente paso.

3. Ejecución del Proyecto

Paso 1: Construir y Levantar los Contenedores
Este comando construirá la imagen de Docker (instalando las dependencias de requirements.txt) y levantará todos los servicios (backend y base de datos) en segundo plano.

docker-compose up --build -d



Paso 2: Ejecutar las Migraciones de la Base de Datos
Una vez que los contenedores estén corriendo, ejecuta los siguientes comandos para preparar la base de datos.

# Crea los nuevos archivos de migración si has modificado los modelos
docker-compose exec backend python manage.py makemigrations

# Aplica las migraciones para crear las tablas en la base de datos
docker-compose exec backend python manage.py migrate



Paso 3: Crear un Superusuario
Este paso es necesario para acceder al panel de administrador de Django.

docker-compose exec backend python manage.py createsuperuser



Sigue las instrucciones en la terminal para crear tu cuenta de administrador.

¡Listo! El servicio ya estará corriendo en http://localhost:8000.

Comandos Adicionales Útiles

Acceder al Shell de Django:
Para interactuar directamente con tus modelos de Django y ejecutar código Python en el contexto de tu aplicación.

docker-compose exec backend python manage.py shell
