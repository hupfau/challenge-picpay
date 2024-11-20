# Backend Challenge - PicPay

This repository contains the solution for the **Backend Challenge for the PicPay position**, a simplified payment system where users can transfer money to other users or merchants.

---

## Technologies Used

- **Java 17**
- **Spring Boot 3.1.2**
- **JPA/Hibernate**
- **In-Memory H2 Database**
- **Lombok**
- **Maven**

---

## How to Run the Project

To run the project locally, follow the steps below:

1. **Build the project** with Maven:
    ```bash
    mvn clean install
    ```

2. **Start the server**:
    ```bash
    mvn spring-boot:run
    ```

    The server will be available at localhost:8080 by default. If you want to run it on a different port, you can configure it in the application.properties file by adding:
    ```bash
    server.port=YOUR_DESIRED_PORT
    ```

3. **Database**:
    The project uses an in-memory H2 database. You can access the H2 console at `http://localhost:8080/h2-console`.

    **Database configuration** is defined in the `src/main/resources/application.properties` file:
    ```properties
    spring.datasource.url=jdbc:h2:mem:testdb
    spring.datasource.driver-class-name=org.h2.Driver
    spring.datasource.username=sa
    spring.datasource.password=
    spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
    spring.h2.console.enabled=true
    ```

---

## API Endpoints

### **POST /users**

Create a new user.

- **Request**:
    ```json
    {
      "firstName": "John",
      "lastName": "Doe",
      "document": "12345678901",
      "email": "john.doe@example.com",
      "password": "password_example",
      "balance": 100.0,
      "userType": "COMMON"
    }
    ```

- **Response**:
    - Status: `201 Created`
    - Body: Details of the created user.

### **GET /users**

Get a list of all users.

- **Response**:
    - Status: `200 OK`
    - Body: A list of users (with their details).

### **POST /transactions**

Create a new transaction between two users.

- **Request**:
    ```json
    {
      "value": 100.0,
      "payer": 4,
      "payee": 15
    }
    ```

- **Response**:
    - Status: `200 OK`
    - Body: Details of the created transaction.

---
## Final Considerations

This project is a simplified model of the PicPay payment system, with features for user registration and transactions between users.
