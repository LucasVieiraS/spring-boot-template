# Spring Boot Template

A minimal and opinionated **Spring Boot 3 + JDK 17** starter template.  
The goal is to provide a production-shaped base with sensible defaults, so each new project starts clean and consistent.

[![Java](https://img.shields.io/badge/Java-17-blue.svg?style=flat&logo=java)]()
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen.svg?style=flat&logo=springboot)]()
[![Build](https://img.shields.io/github/actions/workflow/status/lucasvieiras/springboot-template/maven.yml?branch=main&style=flat)]()
[![License](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat)]()

---

## Why this setup

This template is designed to cover the foundations most real-world Spring Boot services need:

- **Spring Boot 3 + JDK 17**  
  Current industry baseline (LTS). Most companies standardize on 17 for production support.

- **Spring Web**  
  For REST controllers and APIs.

- **Spring Data JPA + PostgreSQL**  
  PostgreSQL is widely adopted, and JPA abstracts persistence without locking into a vendor.

- **Flyway**  
  For database migrations. Safer than relying on Hibernate’s `ddl-auto` in production.

- **Lombok**  
  Reduces boilerplate (getters/setters/builders) while keeping entities and DTOs concise.

- **MapStruct**  
  Type-safe DTO ↔ Entity mapping at compile time. Avoids reflection and manual boilerplate.

- **Springdoc OpenAPI**  
  Auto-generates API documentation. Swagger UI is available at `/swagger-ui.html`.

- **Actuator**  
  Health checks and metrics for observability.

- **Global Exception Handler**  
  Centralized error handling with consistent JSON responses.

- **Testcontainers**  
  Runs integration tests against real Postgres instances. Prevents “works on my machine” problems.

- **Docker Compose support**  
  Local development with Postgres (and optional pgAdmin).

---

## Project structure

```
src/main/java/com/github/lucasvieiras/springboot_template
├── config/         # API prefix config, OpenAPI config, @ConfigurationProperties
├── controllers/    # REST controllers
├── dtos/           # Request/response DTOs
├── entities/       # JPA entities
├── exceptions/     # GlobalExceptionHandler + custom exceptions
├── mappers/        # MapStruct interfaces
├── repositories/   # Spring Data JPA repositories
└── services/       # Business logic
```

---

## Running locally

### Prerequisites
- JDK 17+
- Maven 3.9+
- Docker and Docker Compose

### Start database
```bash
docker compose -f infra/docker-compose.yml up -d
```

### Run application
```bash
./mvnw spring-boot:run
```

Application runs at: `http://localhost:8080`  
Swagger UI: `http://localhost:8080/swagger-ui.html`  
Health endpoint: `http://localhost:8080/api/v1/health`

---

## Testing

Unit and integration tests are run with:

```bash
./mvnw verify
```

Integration tests (`*IT.java`) use **Testcontainers** to spin up a PostgreSQL container automatically.

---

## License

[MIT](LICENSE) © 2025 [Lucas Vieiras](https://github.com/lucasvieiras)
