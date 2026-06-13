# EasyCRUD
---

## Features

### Student Management

* Create student records
* Retrieve student details
* Update student information
* Delete student records

### Backend Services

* RESTful API architecture
* Spring Boot framework
* Spring Data JPA integration
* Environment-based configuration
* Database-driven persistence

### DevOps

* Docker containerization
* Jenkins CI/CD pipeline
* Automated build and deployment
* Maven-based build management

---

## Technology Stack

| Component        | Technology                  |
| ---------------- | --------------------------- |
| Backend          | Spring Boot                 |
| Language         | Java                        |
| Build Tool       | Maven                       |
| Database         | MariaDB                     |
| ORM              | Spring Data JPA / Hibernate |
| Containerization | Docker                      |
| CI/CD            | Jenkins                     |
| Version Control  | Git                         |
| Repository       | GitHub                      |

---

## Architecture

```text
Developer
    │
    ▼
GitHub Repository
    │
    ▼
Jenkins Pipeline
    │
    ├── Checkout Source
    ├── Build Application
    ├── Execute Tests
    ├── Build Docker Image
    └── Deploy Application
    │
    ▼
Docker Container
    │
    ▼
Spring Boot Application
    │
    ▼
MariaDB Database
```

---

## Project Structure

```text
EasyCRUD/
│
├── src/
│   ├── main/
│   └── test/
│
├── Dockerfile
├── Jenkinsfile
├── pom.xml
├── README.md
│
└── target/
```

---

## Prerequisites

Ensure the following software is installed:

* Java 17 or higher
* Maven 3.8+
* MariaDB 10+
* Docker
* Jenkins
* Git

---

## Database Setup

### Install MariaDB

```bash
sudo apt update
sudo apt install mariadb-server -y
```

### Secure Installation

```bash
mysql_secure_installation
```

### Login to MariaDB

```bash
mysql -u root -p
```

### Create Database

```sql
CREATE DATABASE student_db;
```

### Create Database User

```sql
GRANT ALL PRIVILEGES ON student_db.* TO 'username'@'localhost' IDENTIFIED BY 'password';

FLUSH PRIVILEGES;
```

### Create Students Table

```sql
USE student_db;

CREATE TABLE students (
    id BIGINT NOT NULL AUTO_INCREMENT,
    name VARCHAR(255),
    email VARCHAR(255),
    course VARCHAR(255),
    student_class VARCHAR(255),
    percentage DOUBLE,
    branch VARCHAR(255),
    mobile_number VARCHAR(255),
    PRIMARY KEY (id)
);
```

---

## Configuration

Configure the following environment variables:

```properties
DB_HOST=localhost
DB_PORT=3306
DB_NAME=student_db
DB_USER=username
DB_PASS=password
```

---

## Build Instructions

Clone the repository:

```bash
git clone https://github.com/CloudwithKetan/EasyCRUD.git
cd EasyCRUD
```

Build the project:

```bash
mvn clean install
```

Package the application:

```bash
mvn clean package
```

---

## Deployment Guide

### Local Deployment

Run the application:

```bash
mvn spring-boot:run
```

or

```bash
java -jar target/*.jar
```

Verify application availability:

```text
http://localhost:8080
```

---

### Docker Deployment

Build Docker image:

```bash
docker build -t easycrud .
```

Run container:

```bash
docker run -d \
-p 8080:8080 \
-e DB_HOST=localhost \
-e DB_PORT=3306 \
-e DB_NAME=student_db \
-e DB_USER=username \
-e DB_PASS=password \
easycrud
```

Verify deployment:

```bash
docker ps
```

---

## CI/CD Pipeline

The project includes a Jenkins pipeline for automated software delivery.

### Pipeline Stages

1. Source Code Checkout
2. Dependency Resolution
3. Application Build
4. Automated Testing
5. Docker Image Build
6. Deployment

### Pipeline Flow

```text
GitHub
   │
   ▼
Jenkins
   │
   ├── Checkout
   ├── Build
   ├── Test
   ├── Docker Build
   └── Deploy
   │
   ▼
Application Environment
```

---

## API Endpoints

| Method | Endpoint       | Description       |
| ------ | -------------- | ----------------- |
| POST   | /students      | Create Student    |
| GET    | /students      | Get All Students  |
| GET    | /students/{id} | Get Student By ID |
| PUT    | /students/{id} | Update Student    |
| DELETE | /students/{id} | Delete Student    |

---

## Post Deployment Validation

Verify the following after deployment:

* Application is running successfully
* Database connection is established
* CRUD APIs are accessible
* Docker container is healthy
* Jenkins pipeline completed successfully

Example:

```bash
curl http://localhost:8080/students
```

---

## Security Considerations

* Store credentials using environment variables.
* Use Jenkins Credentials Manager for sensitive data.
* Restrict database access to authorized hosts.
* Enable HTTPS in production environments.
* Avoid hardcoding secrets in source code.

---

## Future Enhancements

* JWT Authentication & Authorization
* Swagger/OpenAPI Documentation
* Role-Based Access Control (RBAC)
* Kubernetes Deployment
* Monitoring with Prometheus & Grafana
* Centralized Logging
* Automated Integration Testing

