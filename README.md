#  🛒  ZalandoLite V2 - Microservices Architecture

**ZalandoLiteV2** is a microservices-based backend system simulating a fashion e-commerce platform. It includes *seven (7) 
services*, secured with **Google OAuth2**, **containerized with Docker**, and **connected** via the **zalando-backend network**. 
No UI—API only.

## Overview

This system consists of 7 microservices:

| Microservice                                                                           | Role / Service                 | Database | Port | Status      | Done By                                   |
|----------------------------------------------------------------------------------------|--------------------------------|----------|------|-------------|-------------------------------------------|
| [**Authentication  Service**](https://github.com/Ochwada/ZalandoLiteV2-authentication) | Microservice 1: Authentication |          | 9080 | ✅ Done      | [**Ochwada**](https://github.com/Ochwada) |
| [**Product Service**]( )                                                               | Microservice 2: Product        |          | 8586 | 🧠 in Progress |[**Reyhan**](https://github.com/reyhanovelek)]                               
| [**Inventory Service**]( )                                                             | Microservice 3: Inventory      |          | 8587 | 🧠 Planning | [**Ochwada**](https://github.com/Ochwada) |
| [**Customer  Service**]( )                                                             | Microservice 4: Customer       |          | 8588 | 🧠 Planning | [**Reyhan**](https://github.com/reyhanovelek)]                      
| [**Order Service**]( )                                                                 | Microservice 5: Order          |          | 8589 | 🧠 Planning | [**Ochwada**](https://github.com/Ochwada) |
| [**Discount  Service**]( )                                                             | Microservice 6: Discount       |          | 8590 | 🧠 Planning | |[**Reyhan**](https://github.com/reyhanovelek)]                        
| [**Review  Service**]( )                                                               | Microservice 5: Order          |          | 8591 | 🧠 Planning | [**Ochwada**](https://github.com/Ochwada) |

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
🖇️ [Git Repository : Authentication Service]( )

**Purpose**: Handles user authentication, registration, and authorization across the system via Oauth2.

#### Core Functions:
- **Google OAuth2 login**: Allows users to sign in securely via Google. 
- **User registration**: Registers new users and stores basic profile info. 
- **Token validation**: Verifies access tokens for inter-service communication.





---

## 🚀 Getting Started

### Prerequisites
- Docker + Docker Compose installed
- Git installed
- Java 17+ and Maven (for local builds, if needed)

### Step 1: Clone the Repositories

```bash 

git clone https://github.com/Ochwada/ZalandoLiteV2-authentication authentication-Service


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


