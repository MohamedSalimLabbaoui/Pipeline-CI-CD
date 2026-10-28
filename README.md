# Student Management — Spring Boot + Jenkins CI Pipeline

REST API for managing students, departments, courses and enrollments, built to practice a complete **CI pipeline with Jenkins and SonarQube**.

## Stack

![Java](https://img.shields.io/badge/Java_17-ED8B00?style=flat&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot_3.5-6DB33F?style=flat&logo=springboot&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=flat&logo=apachemaven&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat&logo=jenkins&logoColor=white)
![SonarQube](https://img.shields.io/badge/SonarQube-4E9BCD?style=flat&logo=sonarqube&logoColor=white)

Spring Web, Spring Data JPA, Lombok, springdoc-openapi (Swagger UI), JUnit.

## The API

Layered architecture (`controllers` → `services` → `repositories` → `entities`) with four resources:

| Resource | Purpose |
|---|---|
| Student | Create, read, update and delete students |
| Department | Manage departments |
| Course | Courses available for enrollment |
| Enrollment | Link students to courses, with a status |

Swagger UI is available once the app is running (default: `http://localhost:8080/swagger-ui/index.html`).

## CI pipeline (`Jenkinsfile`)

| Stage | What it does |
|---|---|
| **Checkout** | Pulls the repository |
| **Build & Unit Tests** | `mvn clean test` on `*UnitTest.java`, publishes JUnit reports |
| **SonarQube Analysis** | Static analysis with coverage from JaCoCo |
| **Package** | `mvn package`, archives the `.jar` as a build artifact |
| **Notifications** | E-mail on success or failure |

Requires in Jenkins: Maven (`maven3`), JDK 17, and a SonarQube server configured under the name `sonarqube`.

## Run locally

```bash
# configure the MySQL connection in src/main/resources/application.properties
./mvnw spring-boot:run
./mvnw test
```

## Author

Mohamed Salim Labbaoui, software engineering student at ESPRIT — [GitHub](https://github.com/MohamedSalimLabbaoui)
