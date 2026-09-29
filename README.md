# BoardgameListingWebApp

## Description

**Board Game Database Full-Stack Web Application.**
This web application displays lists of board games and their reviews. While anyone can view the board game lists and reviews, they are required to log in to add/ edit the board games and their reviews.

## Technologies

### Application

- Java
- Spring Boot
- Thymeleaf
- Thymeleaf Fragments
- HTML5
- CSS
- JavaScript
- Spring MVC
- JDBC
- H2 Database Engine (In-memory)
- JUnit test framework
- Spring Security
- Twitter Bootstrap
- Maven

### DevOps and Deployment

- Docker
- Jenkins
- Kubernetes
- SonarQube
- Amazon Web Services (AWS) EC2

## DevOps Architecture

This project includes a containerized build and deployment workflow for the Spring Boot application:

1. **Containerization:** The application is packaged with a Docker multi-stage build. The first stage uses Maven to compile and package the application, while the second stage runs the packaged JAR on a lightweight JRE runtime image.
2. **Continuous Integration:** Jenkins automates the build workflow through dedicated Compile, Test, and Maven Build stages.
3. **Code Quality:** SonarQube is included in the development workflow to support static code analysis and code-quality monitoring.
4. **Kubernetes Deployment:** The Docker image is deployed to Kubernetes with **2 application replicas** for availability. A Kubernetes **LoadBalancer Service** exposes the application to external traffic.
5. **Infrastructure:** The application was deployed using AWS EC2.

## CI/CD Pipeline

The Jenkins pipeline performs the following stages:

- **Compile:** Compiles the Java source code and verifies that the project builds successfully.
- **Test:** Runs the JUnit test suite.
- **Maven Build:** Packages the Spring Boot application into a deployable artifact and prepares it for containerization and deployment.

## Kubernetes Deployment

The application runs on Kubernetes with:

- 2 replicas of the application pod
- A LoadBalancer Service for external access
- Docker as the container runtime image source

This setup provides repeatable deployments, basic workload availability, and a clear separation between application packaging and runtime execution.

## Features

- Full-Stack Application
- UI components created with Thymeleaf and styled with Twitter Bootstrap
- Authentication and authorization using Spring Security
  - Authentication by allowing the users to authenticate with a username and password
  - Authorization by granting different permissions based on the roles (non-members, users, and managers)
- Different roles (non-members, users, and managers) with varying levels of permissions
  - Non-members only can see the boardgame lists and reviews
  - Users can add board games and write reviews
  - Managers can edit and delete the reviews
- Deployed the application on AWS EC2
- JUnit test framework for unit testing
- Spring MVC best practices to segregate views, controllers, and database packages
- JDBC for database connectivity and interaction
- CRUD (Create, Read, Update, Delete) operations for managing data in the database
- Schema.sql file to customize the schema and input initial data
- Thymeleaf Fragments to reduce redundancy of repeating HTML elements (head, footer, navigation)

## How to Run

1. Clone the repository
2. Open the project in your IDE of choice
3. Run the application
4. To use initial user data, use the following credentials.
   - username: bugs    |     password: bunny (user role)
   - username: daffy   |     password: duck  (manager role)
5. You can also sign-up as a new user and customize your role to play with the application! 😊

## DevOps Workflow

```text
Source Code
    |
    v
Jenkins: Compile -> Test -> Maven Build
    |
    v
Docker Multi-Stage Build
    |  Maven build stage -> Lightweight JRE runtime stage
    v
Container Image
    |
    v
Kubernetes: 2 Replicas + LoadBalancer Service
    |
    v
AWS EC2
```
