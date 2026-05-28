# Spring Boot JWT Authentication API

This project is a REST API built using Spring Boot and Spring Security.
It implements JWT (JSON Web Token) based authentication and role-based authorization.

The application allows users to:

* Register new users
* Authenticate using username and password
* Generate JWT tokens
* Access secured endpoints based on roles

---

# Technologies Used

* Java
* Spring Boot
* Spring Security
* JWT (JJWT)
* Maven
* BCrypt Password Encoder

---

# Project Structure

```id="hmamyd"
src/main/java/com/javatechie
│
├── config
│   ├── SecurityConfig.java
│   └── UserInfoUserDetailsService.java
│
├── controller
│   └── ProductController.java
│
├── dto
│   ├── AuthRequest.java
│   └── Product.java
│
├── entity
│   └── UserInfo.java
│
├── filter
│   └── JwtAuthFilter.java
│
├── repository
│   └── UserInfoRepository.java
│
├── service
│   ├── JwtService.java
│   └── ProductService.java
```

---

# Authentication Flow

1. User registers using the registration API.
2. Password is encrypted using BCrypt before saving.
3. User authenticates with username and password.
4. JWT token is generated after successful authentication.
5. Client sends the token in the Authorization header.
6. JWT filter validates the token for every protected request.
7. Access is granted based on user roles.

---

# API Endpoints

## Public Endpoints

### Welcome Endpoint

```http id="mqcax8"
GET /products/welcome
```

Response:

```text id="d0gwdf"
Welcome this endpoint is not secure
```

---

### Register User

```http id="brqzkr"
POST /products/new
```

Request Body:

```json id="diyv3t"
{
  "name": "john",
  "password": "password123",
  "roles": "ROLE_USER"
}
```

---

### Authenticate User

```http id="i4n0yj"
POST /products/authenticate
```

Request Body:

```json id="w18xyo"
{
  "username": "john",
  "password": "password123"
}
```

Response:

```text id="8z3g2t"
JWT_TOKEN
```

---

# Protected Endpoints

### Get All Products

```http id="d7zwxw"
GET /products/all
```

Required Role:

```text id="vzw0bo"
ROLE_ADMIN
```

---

### Get Product By ID

```http id="fy9h3m"
GET /products/{id}
```

Required Role:

```text id="1elrxe"
ROLE_USER
```

Example:

```http id="n7h7fr"
GET /products/1
```

---

# Authorization Header

For protected APIs, include the JWT token in the request header.

```http id="3i8x8t"
Authorization: Bearer YOUR_JWT_TOKEN
```

Example:

```http id="t34vfa"
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
```

---

# Security Configuration

The application uses:

* Spring Security
* JWT Authentication Filter
* Stateless Session Management
* BCrypt Password Encoding
* Role-Based Authorization

---

# Running the Project

## Clone Repository

```bash id="65l8lr"
git clone https://github.com/your-username/spring-security-jwt.git
```

---

## Move to Project Directory

```bash id="a44dz7"
cd spring-security-jwt
```

---

## Build the Project

```bash id="6m7w5x"
mvn clean install
```

---

## Run the Application

```bash id="g9e8u9"
mvn spring-boot:run
```

---

# Testing

You can test the APIs using:

* Postman
* Thunder Client
* Insomnia

---

# Future Improvements

* Database integration
* Refresh token support
* Swagger documentation
* Docker support
* Role management APIs

---

# Author

Krishan Bhadala
