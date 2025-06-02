# Inventra - Inventory Management API

[![Java Version](https://img.shields.io/badge/Java-21-blue.svg)](https://www.oracle.com/java/technologies/downloads/#java21)
[![Spring Boot Version](https://img.shields.io/badge/Spring%20Boot-3.5.0-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Maven Build](https://img.shields.io/badge/Build-Maven-red.svg)](https://maven.apache.org/)

Inventra is a robust RESTful API for managing an inventory system. It allows users to perform CRUD (Create, Read, Update, Delete) operations on products and their categories. Built with Spring Boot, it provides a solid backend foundation for inventory-related applications.

## ✨ Features

*   **Category Management**: Full CRUD operations for product categories.
*   **Product Management**: Full CRUD operations for products, including association with categories.
*   **RESTful API**: Clean and intuitive API endpoints.
*   **Input Validation**: Ensures data integrity through validation of request payloads.
*   **Centralized Exception Handling**: Provides consistent and informative error responses.
*   **Spring Data JPA**: Simplifies database interactions with MySQL.

## 🛠️ Technologies Used

*   **Java 21**: Core programming language.
*   **Spring Boot 3.5.0**: Framework for building the application.
    *   Spring Web: For building RESTful APIs.
    *   Spring Data JPA: For data persistence.
    *   Spring Boot Starter Validation: For input validation.
*   **Hibernate**: JPA provider.
*   **Maven**: Build automation and dependency management.
*   **MySQL**: Relational database for storing inventory data.
*   **Lombok**: Reduces boilerplate code (e.g., getters, setters, constructors).
*   **Jakarta Validation API**: For defining and validating constraints on objects.

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

*   **JDK 21** (Java Development Kit)
*   **Maven** (Can use the included Maven Wrapper `mvnw`)
*   **MySQL Server**: Running and accessible.

## 🚀 Setup & Installation

1.  **Clone the Repository (Placeholder)**
    ```bash
    # git clone <repository-url>
    # cd Inventra
    ```
    *(For now, you are working with the project locally.)*

2.  **Database Setup**
    *   Ensure your MySQL server is running.
    *   Create a database named `inventra_db`:
        ```sql
        CREATE DATABASE inventra_db;
        ```
    *   Configure your database credentials in `src/main/resources/application.properties`:
        ```properties
        spring.datasource.url=jdbc:mysql://localhost:3306/inventra_db
        spring.datasource.username=your_mysql_username # Typically 'root' for local dev
        spring.datasource.password=your_mysql_password # Leave blank if no password
        ```
        *Note: The project is currently configured to use `root` with no password.*

3.  **Build the Project**
    Open a terminal in the project's root directory and run:
    *   On Windows:
        ```bash
        .\mvnw.cmd clean package
        ```
    *   On macOS/Linux:
        ```bash
        ./mvnw clean package
        ```
    This will compile the code, run tests, and package the application into an executable JAR file in the `target/` directory (e.g., `Inventra-0.0.1-SNAPSHOT.jar`). The application can then be run using `java -jar target/Inventra-0.0.1-SNAPSHOT.jar`.

## 🔌 API Endpoints

All endpoints are prefixed with `/api`. The API communicates using JSON.

### Category Endpoints (`/api/categories`)

*   **`POST /api/categories`**: Create a new category.
    *   Request Body:
        ```json
        {
            "name": "Category Name"
        }
        ```
*   **`GET /api/categories`**: Get all categories.
*   **`GET /api/categories/{id}`**: Get a specific category by its ID.
*   **`PUT /api/categories/{id}`**: Update an existing category.
    *   Request Body: Same as POST.
*   **`DELETE /api/categories/{id}`**: Delete a category.

### Product Endpoints (`/api/products`)

*   **`POST /api/products`**: Create a new product.
    *   Request Body:
        ```json
        {
            "name": "Product Name",
            "stock": 100,
            "price": 99.99,
            "categoryId": 1
        }
        ```
*   **`GET /api/products`**: Get all products.
*   **`GET /api/products/{id}`**: Get a specific product by its ID.
*   **`PUT /api/products/{id}`**: Update an existing product.
    *   Request Body: Same as POST.
*   **`DELETE /api/products/{id}`**: Delete a product.

## ⚙️ Configuration

*   **Database Connection**: Located in `src/main/resources/application.properties`.
    *   `spring.datasource.url`
    *   `spring.datasource.username`
    *   `spring.datasource.password`
*   **JPA & Hibernate**:
    *   `spring.jpa.hibernate.ddl-auto=update`: Automatically updates the database schema based on entities. Change as needed for different environments (e.g., `validate` or `none` for production).
    *   `spring.jpa.show-sql=true`: Logs SQL statements.
    *   `spring.jpa.properties.hibernate.format_sql=true`: Formats logged SQL statements.

## 🧪 Testing

It's recommended to use an API client like [Postman](https://www.postman.com/) or [Insomnia](https://insomnia.rest/) to test the API endpoints.

1.  Ensure the application is running (e.g., by executing `java -jar target/Inventra-0.0.1-SNAPSHOT.jar` from the project root after building).
2.  Send HTTP requests to the defined endpoints (see [API Endpoints](#-api-endpoints) section).
    *   For `POST` and `PUT` requests, ensure the `Content-Type` header is set to `application/json`.
    *   Observe the HTTP status codes and JSON responses.

## 🤝 Contributing (Placeholder)

Contributions are welcome! If you'd like to contribute, please follow these steps:
1.  Fork the repository.
2.  Create a new branch (`git checkout -b feature/your-feature-name`).
3.  Make your changes.
4.  Commit your changes (`git commit -m 'Add some feature'`).
5.  Push to the branch (`git push origin feature/your-feature-name`).
6.  Open a Pull Request.

## 📜 License (Placeholder)

This project is licensed under the MIT License - see the `LICENSE.md` file for details (if one is created).

---

*Happy Coding!* 