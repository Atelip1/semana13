# Gestión de usuarios – Parte de Pilar

Proyecto funcional de ejemplo para la Semana 13: CRUD persistente con Spring Boot, Hibernate y Spring Data JPA. Incluye estructura MVC y patrón Strategy para seleccionar consultas.

## Requisitos
- JDK 17
- Maven 3.6+ (o usar Maven Wrapper si se agrega)
- IDE recomendado: IntelliJ IDEA, Eclipse o Visual Studio Code con extensiones Java

## Ejecutar
1. Descomprimir el proyecto.
2. Abrir la carpeta `gestion-usuarios-pilar` en el IDE.
3. Verificar que el proyecto use Java 17.
4. Ejecutar `mvn spring-boot:run` desde la carpeta que contiene `pom.xml`.
5. Abrir `http://localhost:8080/usuarios`.

La base H2 se guarda en `./data/usuariosdb`, por lo que los registros permanecen después de reiniciar la aplicación.

## Funcionalidades
- Crear, listar, editar y eliminar usuarios.
- Buscar por email.
- Listar usuarios con edad estrictamente mayor que 18.
- Validar campos obligatorios, formato del correo y correo duplicado.
- Patrón Strategy: `BusquedaUsuarioStrategy`, `TodosLosUsuariosStrategy` y `MayoresDe18Strategy`.

## Estructura MVC
- **Model:** `model/Usuario.java` representa la entidad persistida.
- **View:** `templates/usuarios.html` muestra formulario y tabla.
- **Controller:** `controller/UsuarioController.java` recibe las solicitudes web.
- **Service:** `service/UsuarioService.java` contiene reglas de negocio.
- **Repository:** `repository/UsuarioRepository.java` accede a la BD usando Spring Data JPA.
- **Strategy:** `strategy/` encapsula distintas formas de obtener usuarios.

## Base de datos H2
Con la aplicación encendida, abrir `http://localhost:8080/h2-console`:
- JDBC URL: `jdbc:h2:file:./data/usuariosdb`
- User Name: `sa`
- Password: dejar vacío

## Pruebas sugeridas
1. Registrar tres usuarios con edades 17, 18 y 19.
2. Pulsar **Mayores de 18**: solo debe aparecer el de 19.
3. Buscar por un email existente y luego uno inexistente.
4. Editar un registro y comprobar el cambio.
5. Eliminar un registro.
6. Reiniciar la aplicación y verificar que los registros restantes siguen guardados.

## Nota para la entrega
Las capturas de evidencia deben tomarse al ejecutar el proyecto en el equipo. No se incluyen capturas ficticias ni se afirma que el proyecto ya fue probado en el entorno del estudiante.
