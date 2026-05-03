# BankApp - Banking Web Application

A modern Spring Boot-based banking web application with integrated CI/CD pipeline using GitHub Actions, security scanning, code quality analysis, and automated testing.

## Overview

BankApp is a secure banking application built with Spring Boot 3.3.3 and Java 17. It provides user authentication, account management, and transaction processing with comprehensive security and code quality controls through automated CI/CD workflows.

## Technology Stack

- **Backend Framework**: Spring Boot 3.3.3
- **Language**: Java 17
- **Database**: MySQL 8
- **Web Framework**: Spring MVC + Thymeleaf
- **Security**: Spring Security
- **ORM**: Spring Data JPA + Hibernate
- **Build Tool**: Maven
- **Code Quality**: SonarQube with JaCoCo code coverage
- **Security Scanning**: Trivy & GitLeaks
- **CI/CD**: GitHub Actions

## Features

- User authentication and authorization
- Secure login and registration
- User dashboard with account information
- Transaction management and history
- Spring Security integration for access control
- Role-based access control (RBAC)
- Responsive web interface with Thymeleaf templates

## Project Structure

```
src/
├── main/
│   ├── java/com/example/bankapp/
│   │   ├── BankappApplication.java
│   │   ├── config/
│   │   │   └── SecurityConfig.java
│   │   ├── controller/
│   │   │   └── BankController.java
│   │   ├── model/
│   │   ├── repository/
│   │   └── service/
│   └── resources/
│       ├── application.properties
│       ├── static/
│       │   └── mysql/SQLScript.txt
│       └── templates/
│           ├── login.html
│           ├── register.html
│           ├── dashboard.html
│           └── transactions.html
└── test/
    └── java/com/example/bankapp/
        └── BankappApplicationTests.java
```

## Prerequisites

- Java 17 (JDK)
- Maven 3.6+
- MySQL 8.0+
- Docker (for containerized deployment)

## Database Configuration

Update `src/main/resources/application.properties`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/bankappdb?useSSL=false&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=Test@123
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
```

## Build & Run

### Local Development

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd GitHub-Action-Project-01
   ```

2. **Compile the project**
   ```bash
   mvn compile
   ```

3. **Run unit tests**
   ```bash
   mvn test
   ```

4. **Build the application**
   ```bash
   mvn package
   ```

5. **Run the application**
   ```bash
   mvn spring-boot:run
   ```

The application will be available at `http://localhost:8080`

### Docker Deployment

Build and run using Docker:

```bash
docker build -t bankapp:latest .
docker run -p 8080:8080 bankapp:latest
```

## CI/CD Pipeline

The GitHub Actions workflow (`cicd.yml`) implements a comprehensive CI/CD pipeline with the following stages:

### 1. **Compile Stage**
   - Checks out code
   - Sets up JDK 17 with Maven caching
   - Compiles the project

### 2. **Security Check Stage**
   - **Trivy Scan**: Filesystem vulnerability scanning
   - **GitLeaks Scan**: Secret/credential detection in source code

### 3. **Unit Test Stage**
   - Runs all unit tests using Maven
   - Generates JaCoCo code coverage reports

### 4. **SonarQube Analysis Stage**
   - Performs static code analysis
   - Generates code coverage metrics
   - Validates quality gate requirements
   - Enforces code quality standards

## Configuration

### GitHub Secrets & Variables

Configure the following in your GitHub repository settings:

**Secrets:**
- `SONAR_TOKEN`: SonarQube authentication token

**Variables:**
- `SONAR_HOST_URL`: SonarQube server URL (e.g., `http://<sonar-host>:9000`)

## Security Features

- Spring Security for authentication and authorization
- RBAC (Role-Based Access Control)
- Encrypted database password handling
- Automated security scanning via Trivy
- Secret detection via GitLeaks
- SQL injection prevention through Spring Data JPA
- CSRF protection by default

## Code Quality & Testing

- **Unit Tests**: Comprehensive test coverage via Maven
- **Code Coverage**: JaCoCo integration for coverage metrics
- **Static Analysis**: SonarQube for code quality analysis
- **Quality Gates**: Automated quality gate checks before merge

## Development Guidelines

1. Ensure all commits pass security scans (Trivy & GitLeaks)
2. Write unit tests for new functionality
3. Maintain code coverage above defined threshold
4. Follow SonarQube quality gate requirements
5. Apply RBAC principles for access control

## License

This project is developed for educational and practice purposes.

## References

- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [SonarQube Documentation](https://docs.sonarsource.com/sonarqube/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Trivy Scanner](https://github.com/aquasecurity/trivy)
- [GitLeaks](https://github.com/gitleaks/gitleaks)
