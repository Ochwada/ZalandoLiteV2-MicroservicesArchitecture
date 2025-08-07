#  🛒  ZalandoLite V2 - Microservices Architecture

**ZalandoLiteV2** is a microservices-based backend system simulating a fashion e-commerce platform. It includes *seven (7) 
services*, secured with **Google OAuth2**, **containerized with Docker**, and **connected** via the **zalando-backend network**. 
No UI—API only.

## Overview

This system consists of 7 microservices:

| Microservice                                                                           | Role / Service                 | Database | Port | Status         | Done By                                       |
|----------------------------------------------------------------------------------------|--------------------------------|----------|------|----------------|-----------------------------------------------|
| [**Authentication  Service**](https://github.com/Ochwada/ZalandoLiteV2-authentication) | Microservice 1: Authentication |          | 9080 | ✅ Done         | [**Ochwada**](https://github.com/Ochwada)     |
| [**Product Service**]( )                                                               | Microservice 2: Product        |          | 8586 | 🚧 in Progress | [**Reyhan**](https://github.com/reyhanovelek) |
| [**Inventory Service**](https://github.com/Ochwada/ZalandoLiteV2-inventory)            | Microservice 3: Inventory      |          | 8587 | 🚧 In Progress | [**Ochwada**](https://github.com/Ochwada)     |
| [**Customer  Service**]( )                                                             | Microservice 4: Customer       |          | 8588 | 🧠 Planning    | [**Reyhan**](https://github.com/reyhanovelek) |
| [**Order Service**]( )                                                                 | Microservice 5: Order          |          | 8589 | 🧠 Planning    | [**Ochwada**](https://github.com/Ochwada)     |
| [**Discount  Service**]( )                                                             | Microservice 6: Discount       |          | 8590 | 🧠 Planning    | [**Reyhan**](https://github.com/reyhanovelek) |                       
| [**Review  Service**]( )                                                               | Microservice 7: Review         |          | 8591 | 🧠 Planning    | [**Ochwada**](https://github.com/Ochwada)     |

Each service is independently deployable and communicates over REST APIs. Docker is used for containerization and
orchestration is done using **Docker Compose**.


## 📁 Project Structure
``` bash

zalando-lite-v2/
├── docker-compose.yml         # 🐳 Root Docker Compose for the entire microservices system
├── README.md                  # 📘 Main project documentation
│
├── authentication-service/    # 🔐 Auth service (Spring Boot + Google OAuth2)
│   ├── .env                   # Google client credentials and port
│   ├── Dockerfile             # Container config
│   ├── .mvn/                  
│   ├── src/                   
│   │   └── main/              # Java source and resources
│
├── product-service/           # 👗 Manages products (Spring Boot + PostgreSQL)
│   ├── .env                   # DB credentials and configs
│   ├── Dockerfile             # Container config
│   ├── .mvn/
│   ├── src/
│   │   └── main/
│
├── inventory-service/         # 📦 Tracks stock (Spring Boot + MongoDB)
│   ├── .env                   # DB URL and port
│   ├── Dockerfile             # Container config
│   ├── .mvn/
│   ├── src/
│   │   └── main/
│
├── customer-service/          # 📬 Sends notifications (Spring Boot + Mail/SMS API)
│   ├── .env                   # Notification settings and secrets
│   ├── Dockerfile             # Container config
│   ├── .mvn/
│   ├── src/
│   │   └── main/
│
├── order-service/             # 🛒 Handles orders (Spring Boot + PostgreSQL)
│   ├── .env                   # DB credentials, service endpoints
│   ├── Dockerfile             # Container config
│   ├── .mvn/
│   ├── src/
│   │   └── main/
│
├── discount-service/          # 💸 Applies discounts (Spring Boot)
│   ├── .env                   # Discount rules and API keys
│   ├── Dockerfile             # Container config
│   ├── .mvn/
│   ├── src/
│   │   └── main/
│
└── review-service/            # ⭐ Manages reviews (Spring Boot + PostgreSQL)
    ├── .env                   # DB config and service ports
    ├── Dockerfile             # Container config
    ├── .mvn/
    ├── src/
    │   └── main/

```

## Key Features
- Seven independent microservices 
- Secured with Google OAuth2 
- Fully containerized using Docker 
- Inter-service communication via a custom zalando-backend Docker network 
- Scalable, modular, and production-inspired architecture

## 🖥️ The Microservices Architecture

The system is composed of several specialized services, each responsible for a specific domain:

### 1️⃣  Microservice 1: Authentication  Service
🖇️ [Git Repository : Authentication Service](https://github.com/Ochwada/ZalandoLiteV2-authentication)

**Purpose**: Handles user authentication, registration, and authorization across the system via Oauth2.

#### Core Functions:
- **Google OAuth2 login**: Allows users to sign in securely via Google. 
- **User registration**: Registers new users and stores basic profile info. 
- **Token validation**: Verifies access tokens for inter-service communication.


### 2️⃣ Microservice 2: Product  Service
🖇️ [Git Repository : Product Service]( )

**Purpose**: Manages product catalog (CRUD), categories, pricing.

#### Core Functions:

### 3️⃣ Microservice 3: Inventory  Service
🖇️ [Git Repository : Inventory Service](https://github.com/Ochwada/ZalandoLiteV2-inventory)

**Purpose**: Maintains stock levels for each product and updates inventory on product movement.

#### Core Functions:
- **CRUD operations for inventory**: Allows the creation and updating of stock data.
- **Track stock per product**: Maintains quantity and stock status for each individual product.

---

## Common Tech Stack

| Technology          | Purpose                                                                      |
|---------------------|------------------------------------------------------------------------------|
| **Java 17+**        | Modern programming language used to build the microservice                   |
| **Spring Boot**     | Framework for rapid application development and configuration                |
| **Spring Security** | Handles authentication, authorization, and protection against common attacks |
| **OAuth2 (OIDC)**   | Secure login flow using Google as a trusted identity provider                |
| **Maven**           | Dependency and build management tool for Java projects                       |
| **Docker**          | Containerization for service and database                                    |

### Common Dependencies
| Dependency Artifact                 | Purpose                                                                 |
|-------------------------------------|-------------------------------------------------------------------------|
| `spring-boot-starter-oauth2-client` | Enables OAuth2 login (e.g. Google), and integrates with OpenID Connect  |
| `spring-boot-starter-security`      | Adds Spring Security for securing endpoints, sessions, and roles        |
| `spring-boot-starter-thymeleaf`     | Provides Thymeleaf support for rendering HTML views on the server side  |
| `spring-boot-starter-validation`    | Enables Java Bean Validation (e.g., `@Valid`, `@Email`, etc.)           |
| `spring-boot-starter-web`           | Core starter for RESTful web applications using Spring MVC              |
| `lombok`                            | Reduces boilerplate by auto-generating code like getters, setters, etc. |
| `spring-boot-starter-test`          | Includes tools like JUnit, Mockito, AssertJ for unit/integration tests  |
| `spring-security-test`              | Adds support for testing Spring Security (e.g., mocking users/roles)    |
| `dotenv-java`                       | Loads environment variables from `.env` file at runtime                 |

---

## 🚀 Getting Started

### Prerequisites
- Docker + Docker Compose installed
- Git installed
- Java 17+ and Maven (for local builds, if needed)

### Step 1: Clone the Repositories

```bash 

git clone https://github.com/Ochwada/ZalandoLiteV2-authentication authentication-service

git clone https://github.com/Ochwada/ZalandoLiteV2-inventory inventory-service


```

### Step 2: Directory Layout
Ensure your directory looks like this:

```
MicroInventorySystem/
├── docker-compose.yml
├── .gitignore
├── README.md
│
├── authentication-service/
├── product-service/
├── inventory-service/
└── order-service/
```

### Step 3: Environment Variables / Environment Configurations
Each service includes a `.env` file with required configuration.

## Data Persistence

- MongoDB data is stored in mongo_data volume
- PostgreSQL data is stored in pg_data volume

## Dockerization
Ensure you have a `Dockerfile` and `docker-compose.yml`
Then run with : 
```yaml

docker-compose build --no-cache    # Rebuild all images from scratch
docker-compose up


# Remove volumes & orphan containers
docker-compose down --volumes --remove-orphans  
```

You can verify volumes using:
```bash
docker volume ls
```


