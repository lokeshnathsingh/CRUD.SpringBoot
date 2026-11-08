# Student Management CRUD API — Spring Boot & MySQL

A RESTful backend service built with **Java**, **Spring Boot**, **Spring Data JPA (Hibernate)**, and **MySQL** to perform full CRUD (Create, Read, Update, Delete) operations on student records.

---

## Tech Stack

* **Language:** Java 24
* **Framework:** Spring Boot 4.1.2 (Spring Web MVC, Spring Data JPA)
* **Database:** MySQL 8.0
* **ORM:** Hibernate
* **Build Tool:** Maven
* **API Testing:** Postman

---

## Project Architecture

The project follows a clean layered architecture separating concerns across Controller, Service, Repository, and Entity layers:

```text
src/main/java/com/project
├── CrudApplication.java          # Application entry point
├── controller
│   └── StudentController.java    # REST API endpoints & HTTP response handling
├── service
│   └── StudentService.java       # Business logic layer
├── repository
│   └── StudentRepository.java    # Spring Data JPA data access interface
└── entity
    └── Student.java              # JPA Entity mapped to MySQL 'student' table
```

---

## REST API Endpoints

**Base URL:** `http://localhost:8080/api/students`

| Operation | HTTP Method | Endpoint | Query Param | Request Body | Success Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Create Student** | `POST` | `/create` | None | `Student` JSON | `201 Created` |
| **Get All Students** | `GET` | `/getAll` | None | None | `200 OK` |
| **Get Student by ID** | `GET` | `/get` | `?id={id}` | None | `200 OK` / `404 Not Found` |
| **Update Student** | `PUT` | `/update` | `?id={id}` | `Student` JSON | `200 OK` / `404 Not Found` |
| **Delete Student** | `DELETE` | `/delete` | `?id={id}` | None | `200 OK` / `404 Not Found` |

---

### Sample Request & Response Payloads

#### 1. Create / Update Student (`POST /api/students/create` or `PUT /api/students/update?id=1`)

**Request Body:**
```json
{
  "name": "Lokesh Nath Singh",
  "email": "lokesh@example.com",
  "age": 21,
  "rollNo": 101,
  "subject": "Computer Science"
}
```

**Response (`201 Created`):**
```json
{
  "id": 1,
  "name": "Lokesh Nath Singh",
  "email": "lokesh@example.com",
  "age": 21,
  "rollNo": 101,
  "subject": "Computer Science"
}
```

#### 2. Delete Student (`DELETE /api/students/delete?id=1`)

**Response (`200 OK`):**
```text
Record deleted
```

---

## Local Setup & Installation

### 1. Clone the repository
```bash
git clone [https://github.com/lokeshnathsingh/CRUD.SpringBoot.git](https://github.com/lokeshnathsingh/CRUD.SpringBoot.git)
cd CRUD.SpringBoot
```

### 2. Configure MySQL Database
1. Make sure your local MySQL server is running on port `3306`.
2. Create the database:
   ```sql
   CREATE DATABASE student_crud_db;
   ```
3. Update `src/main/resources/application.properties` with your MySQL credentials:
   ```properties
   spring.application.name=CRUD

   spring.datasource.url=jdbc:mysql://localhost:3306/student_crud_db
   spring.datasource.username=root
   spring.datasource.password=YOUR_MYSQL_PASSWORD

   spring.jpa.hibernate.ddl-auto=update
   spring.jpa.show-sql=true
   spring.jpa.properties.hibernate.format_sql=true
   ```

### 3. Build and Run the Application
```bash
./mvnw spring-boot:run
```
The server will start on **`http://localhost:8080`**.

---

## Author

**Lokesh Nath Singh**
* [GitHub](https://github.com/lokeshnathsingh)
* [LinkedIn](https://www.linkedin.com/in/lokesh-nath-singh)
