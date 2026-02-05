Introducción: en este segundo modulo lo que hicimos fue crear un inicio de sesión conectado a la base de datos. Esta parte es un componente critico de la capa de seguridad de la aplicación. Su propósito principal es gestionar el proceso de autenticación, actuando como intermediario entre el formulario de inicio de sesión y la base de datos.

## GestorInicioSesionBD

-            Validación y Filtros de Acceso: cuando un usuario ingresa, la clase ejecuta la consulta SQL que une las tablas de Credenciales y Usuarios, antes de validar la contraseña comprueba: la existencia del usuario y el estado de la cuenta para saber si esta activa o no.

-            Cifrado: esta clase se basa en que nunca maneja contraseñas reales, sino “huellas digitales”.

o   Recupera un valor aleatorio único para cada usuario (salt).

o   Utiliza el algoritmo SHA-256 combinando el salt con la contraseña escrita. Para asegurarnos que el cifrado en Java sea idéntico al que se realiza en el SQL Server usaremos el UTF_16LE.

-            Trazabilidad y Auditoria: gracias al procedimiento sp_set_session_context nos permite que la base de datos “sepa” que usuario está realizando las consultas, lo cual es muy importante para poder tener un registro de auditorías.

## ConexionBD

Introducción: la clase ConexionBD actúa como el gestor de enlace de la aplicación. Su función es centralizar todos los parámetros técnicos necesarios para localizar y acceder al servidor.

-            Parámetros de conexión: esta clase define constantes privadas que contiene la ubicación y las llaves de acceso al servidor.

-            Configuración de la URL de JDBC: la variable URL incluye las reglas de comportamiento de la conexión (puerto, seguridad y TrustServerCertificate)

-            Método getConnection(): cada vez que se invoca utiliza el DriverManager para intentar abrir una sesión con el servidor, si los datos son correctos devuelve un objeto Connection que la aplicación usara para enviar consultas.

## Método VerificarUsuario

Introducción: método que aplica la lógica de autenticación de todo lo que hemos explicado anteriormente, este método hace:

-            Realiza una validación previa para asegurar que los campos no estén vacíos en el hello-view.fxml.

-            Llama a la clase que analizamos anteriormente (GestorInicioSesionBD) para comprobar las credenciales contra la base de datos real.

-            Respuesta visual: si el acceso resulta ser correcto, saluda al usuario cambia a la pantalla del menú, si no, cambia el color del mensaje a rojo para indicar el error reconocido.