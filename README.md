## Descripción de la aplicación

Esta aplicación representa un catálogo digital donde la gente podría llevar un registro de sus fotos.

Actualmente se compone de las siguientes funciones:
- Login y registro mediante formulario. Se accede mediante nombre de usuario (no hay opción a recuperar las contraseñas si se pierden).
- Vista del catálogo, con opción a añadir, editar y borrar los elementos. Cada elemento consta de una foto, un título y una calificación.


## Pasos para instalarlo

1. Descargar el proyecto.
2. Abrir una terminal ubicando la ruta en la carpeta donde se encuentre el proyecto.
3. Actualizar las dependencias ejecutando 'composer install' (será necesario instalar Composer antes si no se tiene).
4. Hacer una copia del archivo .env.example y renombrarlo a .env.
5. Ejecutar 'php artisan key:generate'.
6. Ejecutar 'php artisan database:generate'.
7. Ejecutar 'php artisan migrate'.
8. Arrancar la aplicación con 'php artisan serve' y conectar mediante el navegador en la dirección proporcionada por el comando.


## Instrucciones

Utilizando la aplicación proporcionada, implementa las siguientes características:
1. Añade una nueva migración que permita añadir categorías. Cada foto puede pertenecer a una única categoría, y será obligatorio que la tenga asignada. Modifica la vista 'pictures.list' para añadir este dato al formulario. En el script que hay en public>js>pictures.js se encuentran las funciones que leen y envían los datos al servidor.
Incluye este dato también en la vista de la tarjeta cuando se pinten los datos (puedes ubicarlo por ejemplo bajo el título, o junto a las estrellas). Las categorías estarán predefinidas y los usuarios no podrán cambiarlas.
2. Implementa una funcionalidad por API que permita a los usuarios ya registrados obtener un token de acceso API, y de esa forma usarlo para consultar su colección completa en formato JSON.
3. Siguiento la estructura de los tests que hay en Feature>UserTest.php, añade una nueva clase con tests para asegurar que el funcionamiento de la API es correcto, valorando los siguientes casos:
- Intento de acceso a la función sin token: debe dar error de permiso
- Obtención del token: se debe obtener un token válido
- Acceso con token: debe permitir el acceso y devolver un json con los objetos oportunos
4. Crea un servicio automatizado que se ejecute una vez al día y lance un comando que obtenga una estadística de los datos registrados en la aplicación:
- N. de usuarios registrados
- N. de fotos guardadas
- Total de fotos por categoría y media aritmética de la nota que tienen las fotos
Que estos datos se almacenen en un log de la aplicación, de tipo diario.