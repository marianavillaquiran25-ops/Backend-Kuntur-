# Backend Kuntur

Backend API desarrollado con **Spring Boot** para gestionar servicios y operaciones de la plataforma Kuntur.

## 📋 Tabla de Contenidos

- [Descripción](#descripción)
- [Requisitos Previos](#requisitos-previos)
- [Instalación](#instalación)
- [Configuración](#configuración)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [API Endpoints](#api-endpoints)
- [Uso](#uso)
- [Tecnologías](#tecnologías)
- [Contribuir](#contribuir)
- [Licencia](#licencia)

---

## 📝 Descripción

Backend-Kuntur es una aplicación REST API construida con Spring Boot que proporciona funcionalidades para:

- Gestión de usuarios y autenticación
- Administración de recursos y servicios
- Procesamiento de datos
- Integración con base de datos relacional
- Manejo de errores y validaciones

---

## 🔧 Requisitos Previos

Antes de comenzar, asegúrate de tener instalado:

- **Java 11 o superior** ([Descargar](https://www.oracle.com/java/technologies/downloads/))
- **Maven 3.6+** ([Descargar](https://maven.apache.org/download.cgi))
- **Git** ([Descargar](https://git-scm.com/))
- **Base de datos**: MySQL, PostgreSQL o H2 (según configuración)
- **IDE recomendado**: IntelliJ IDEA o Eclipse

---

## 💻 Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/marianavillaquiran25-ops/Backend-Kuntur-.git
cd Backend-Kuntur-
```

### 2. Compilar el proyecto

```bash
mvn clean install
```

### 3. Ejecutar la aplicación

```bash
mvn spring-boot:run
```

La aplicación estará disponible en: **http://localhost:8080**

---

## ⚙️ Configuración

### Archivo `application.properties`

Configura los parámetros de la aplicación en `src/main/resources/application.properties`:

```properties
# Configuración del servidor
server.port=8080
server.servlet.context-path=/api

# Configuración de base de datos
spring.datasource.url=jdbc:mysql://localhost:3306/kuntur_db
spring.datasource.username=root
spring.datasource.password=your_password
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA/Hibernate
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect

# Logging
logging.level.root=INFO
logging.level.com.kuntur=DEBUG
```

### Archivo `application.yml` (alternativo)

```yaml
server:
  port: 8080
  servlet:
    context-path: /api

spring:
  datasource:
    url: jdbc:mysql://localhost:3306/kuntur_db
    username: root
    password: your_password
    driver-class-name: com.mysql.cj.jdbc.Driver
  
  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true
    properties:
      hibernate:
        dialect: org.hibernate.dialect.MySQL8Dialect
```

---

## 📂 Estructura del Proyecto

```
Backend-Kuntur-/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/kuntur/
│   │   │       ├── controller/       # Controladores REST
│   │   │       ├── service/          # Lógica de negocio
│   │   │       ├── repository/       # Acceso a datos
│   │   │       ├── model/            # Entidades JPA
│   │   │       ├── dto/              # Data Transfer Objects
│   │   │       ├── config/           # Configuraciones
│   │   │       └── KunturApplication.java  # Clase principal
│   │   └── resources/
│   │       ├── application.properties
│   │       └── application.yml
│   └── test/
│       └── java/                     # Pruebas unitarias
├── pom.xml                           # Dependencias Maven
└── README.md                         # Este archivo
```

---

## 🔌 API Endpoints

### Ejemplo de endpoints principales

#### Usuarios

```
GET    /api/users              - Obtener todos los usuarios
GET    /api/users/{id}         - Obtener usuario por ID
POST   /api/users              - Crear nuevo usuario
PUT    /api/users/{id}         - Actualizar usuario
DELETE /api/users/{id}         - Eliminar usuario
```

#### Autenticación

```
POST   /api/auth/login         - Login de usuario
POST   /api/auth/register      - Registro de nuevo usuario
POST   /api/auth/logout        - Logout de usuario
POST   /api/auth/refresh       - Refrescar token
```

#### Recursos

```
GET    /api/resources          - Obtener todos los recursos
GET    /api/resources/{id}     - Obtener recurso por ID
POST   /api/resources          - Crear nuevo recurso
PUT    /api/resources/{id}     - Actualizar recurso
DELETE /api/resources/{id}     - Eliminar recurso
```

---

## 🚀 Uso

### Ejemplo de solicitud con cURL

```bash
# Login
curl -X POST http://localhost:8080/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username":"user@example.com","password":"123456"}'

# Obtener usuarios
curl -X GET http://localhost:8080/api/users \
  -H "Authorization: Bearer YOUR_TOKEN"

# Crear usuario
curl -X POST http://localhost:8080/api/users \
  -H "Content-Type: application/json" \
  -d '{"name":"Juan","email":"juan@example.com","password":"secure_pass"}'
```

### Ejemplo con Postman

1. Importa la colección desde `postman_collection.json` (si existe)
2. Configura las variables de entorno
3. Ejecuta las solicitudes en orden

---

## 🛠️ Tecnologías

| Tecnología | Versión | Descripción |
|-----------|---------|------------|
| Spring Boot | 2.7+ | Framework web |
| Spring Data JPA | 2.7+ | Persistencia de datos |
| Spring Security | 2.7+ | Autenticación y autorización |
| MySQL/PostgreSQL | 8.0+ | Base de datos relacional |
| Maven | 3.6+ | Gestor de dependencias |
| JUnit | 4.13+ | Testing |
| Lombok | 1.18+ | Reducción de boilerplate |

---

## 🧪 Pruebas

Ejecutar pruebas unitarias:

```bash
mvn test
```

Ejecutar pruebas con cobertura:

```bash
mvn test jacoco:report
```

---

## 📦 Dependencias Principales

```xml
<!-- Spring Boot Web -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>

<!-- Spring Data JPA -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>

<!-- MySQL Driver -->
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.33</version>
</dependency>

<!-- Lombok -->
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <optional>true</optional>
</dependency>
```

---

## 🤝 Contribuir

Las contribuciones son bienvenidas. Para contribuir:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

---

## 📄 Licencia

Este proyecto está bajo la licencia MIT. Consulta el archivo `LICENSE` para más detalles.

---

## 👤 Autor

**Mariana Villaquirán**
- GitHub: [@marianavillaquiran25-ops](https://github.com/marianavillaquiran25-ops)

---

## 📞 Soporte

Si tienes preguntas o problemas:

- Abre un [Issue](https://github.com/marianavillaquiran25-ops/Backend-Kuntur-/issues)
- Revisa la [Documentación](https://spring.io/projects/spring-boot)
- Contacta al equipo de desarrollo

---

**Última actualización:** Junio 2026
