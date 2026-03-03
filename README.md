# campus
<a href="https://github.com/jopeol1971-rgb/Campus_examen">Campus_Konectia</a>

## Estructura del proyecto

El proyecto está organizado en varios directorios y archivos para separar responsabilidades:

- `app.py`: punto de entrada de la aplicación Flask.
- `helpers.py`: funciones auxiliares compartidas.
- `routes/`: contiene los módulos de rutas (`admin.py`, `alumno.py`, `profesor.py`) que definen los endpoints y controladores.
- `templates/` y `static/`: recursos de la interfaz web (HTML, CSS, JS).
- `InfoDataBase/Schema.sql`: esquema de la base de datos.
- `requirements.txt`: dependencias de Python.
- Carpeta `desechables/`: archivos de apoyo o documentación temporal.

Esta organización facilita el mantenimiento y la ampliación del sistema.

## Justificación del uso de POO

Aunque Flask permite un estilo de programación más funcional, en el backend se emplea programación orientada a objetos para modelar entidades clave (usuarios, asignaturas, eventos) y encapsular lógica relacionada. El uso de clases mejora la modularidad, permite reutilizar código y facilita la prueba de componentes independientes. Además, las relaciones entre objetos reflejan mejor las entidades reales del dominio educativo.

## Explicación de la base de datos

La aplicación utiliza PostgreSQL como sistema de gestión de bases de datos. El esquema incluye tablas principales como `usuarios`, `asignaturas`, `matriculas` y la nueva `eventos`. Cada tabla está relacionada mediante claves foráneas para mantener la integridad referencial. La base de datos contiene información de autenticación, perfiles de usuarios, asignaturas disponibles y los calendarios personales de los alumnos.

Las migraciones se gestionan manualmente actualizando `Schema.sql` y aplicando los cambios con comandos SQL. 

## Descripción de roles

La aplicación define tres roles de usuario:

- **Administrador**: gestiona usuarios y asignaturas, puede modificar o eliminar datos y acceder a un panel de administración completo.
- **Profesor**: consulta las asignaturas que imparte, puede ver detalles de los alumnos matriculados y subir contenido o calificaciones.
- **Alumno**: accede a su calendario personal, ve sus asignaturas, se matricula y utiliza funcionalidades centradas en su perfil y eventos.

Los roles se controlan mediante campos en la tabla `usuarios` y lógica en el backend que restringe el acceso a rutas según el rol.

## Mejora implementada

La mejora principal introducida en esta versión es el calendario personal para alumnos. Se añadió:

- Interfaz de usuario interactiva con selección de días y creación de eventos.
- Almacenamiento de eventos en la nueva tabla `eventos`.
- Validaciones en el backend para asociar eventos al usuario autenticado y evitar colisiones de datos.
- Adaptaciones en los templates y scripts estáticos (`calendario.js`) para soportar la funcionalidad.

Esta característica amplía la utilidad de la plataforma al proporcionar una herramienta personal de organización académica para los estudiantes.
