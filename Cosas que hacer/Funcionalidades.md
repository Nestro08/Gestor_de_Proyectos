## Planificar todas las funcionalidades de la aplicación

Para poder desarrollar esto:

Clase Proyecto: creamos el objeto proyecto con todos sus parámetros para después poder llamarlo desde otras clases.

GestorProyectosBD: Esta clase lo que nos permitirá será crear, modificar y eliminar, dependiendo que opción elijamos, aquí está la lógica para hacer las consultas a la base de datos.

Crear: para poder crear un nuevo proyecto lo que haremos será rellenar los parámetros que nos pide. Después de rellenar todos los parámetros al darle al botón de guardar, la aplicación se comunicará con la BDD y se guardará en ella.

Modificar: para poder modificar las características del proyecto lo que haremos será poner el mismo nombre de nuestro proyecto y rellenar con los campos que vamos a introducir como nuevos.

Eliminar: para poder eliminar un proyecto solo pondremos el nombre del proyecto y guardaremos, con eso se eliminará el proyecto.

UsuarioConectado: esta clase es un constructor de la información del usuario que está conectado

SesionActual: esta clase nos da un registro de quien hace las modificaciones de cada proyecto, utilizando la clase UsuarioConectado para saber que usuario es.

Además de todo esto, empezamos a añadir la posibilidad de añadir las modificaciones en una tabla llamada auditoria. Por último empezamos a hacer la base de datos no relacional en FireBase, pero nos dio algunos problemas a la hora de poder subir los archivos, esto es algo que estamos investigando para futuro desarrollo.