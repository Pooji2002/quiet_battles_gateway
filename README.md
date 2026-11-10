# QUIET BATTLES™ – API Gateway

## Overview

The API Gateway is the central entry point for the QUIET BATTLES™ microservices-based e-commerce application.

It receives HTTP requests from the React frontend and routes them to the appropriate backend microservice. This provides a centralized entry point and keeps the frontend independent of individual service addresses.

## Technology Stack

| Technology | Version / Purpose |
|---|---|
| Java | 17 |
| Spring Boot | 4.1.2 |
| Spring Cloud | 2025.1.4 |
| Spring Cloud Gateway Server WebMVC | API routing |
| Spring Boot Actuator | Application monitoring |
| Maven | Build and dependency management |

## Microservices Architecture

The API Gateway communicates with the following services:

| Service | Port | Responsibility |
|---|---:|---|
| Identity Service | 8091 | Registration, login and authentication |
| Content Service | 8092 | Series and chapter management |
| Product Service | 8093 | Product and stock management |
| Order Service | 8094 | Order creation and management |

The API Gateway runs on port **8090**.

## API Routing

The gateway exposes the following API prefixes:

| API Prefix | Destination |
|---|---|
| `/api/auth/**` | Identity Service |
| `/api/content/**` | Content Service |
| `/api/products/**` | Product Service |
| `/api/orders/**` | Order Service |

All frontend API requests are sent through the gateway instead of calling individual microservices directly.

## Key Responsibilities

- Centralized API entry point.
- Request routing to the appropriate microservice.
- Cross-Origin Resource Sharing (CORS) configuration.
- Support for HTTP methods including GET, POST, PUT, PATCH, DELETE and OPTIONS.
- Integration with the backend microservices.
- Application monitoring through Spring Boot Actuator.

## CORS Configuration

The gateway includes a CORS configuration to control which frontend origins can communicate with backend APIs.

Allowed origins should be configured according to the environment, such as local development and the authorized public demo hostname.

Avoid using unrestricted wildcard origins in production.

## Project Structure

```text
api-gateway/
│
├── src/
│   └── main/
│       ├── java/
│       │   └── com/
│       │       └── quietbattles/
│       │           └── api_gateway/
│       │               ├── ApiGatewayApplication.java
│       │               └── CorsConfig.java
│       │
│       └── resources/
│           └── application.properties
│
├── pom.xml
├── mvnw
├── mvnw.cmd
└── README.md
```

## Prerequisites

- Java Development Kit (JDK) 17
- Maven
- Git
- All required backend microservices configured and running

## Running the Application

### 1. Clone the repository

```bash
git clone https://github.com/Pooji2002/quiet_battles_gateway.git
```

### 2. Navigate to the project

```bash
cd quiet_battles_gateway
```

### 3. Build the application

On Windows:

```powershell
.\mvnw.cmd clean package
```

### 4. Run the application

```powershell
.\mvnw.cmd spring-boot:run
```

The API Gateway runs on:

```text
http://localhost:8090
```

Ensure the downstream microservices are running and their configured routes are reachable.

## Integration with Frontend

The React frontend communicates with the API Gateway through the `/api` base path.

The gateway forwards each request to the corresponding backend service based on its API prefix.

## Repository

GitHub: https://github.com/Pooji2002/quiet_battles_gateway

## Project Context

This API Gateway is part of the QUIET BATTLES™ premium fashion and lifestyle e-commerce demonstration project.

**Brand Tagline: WEAR YOUR BATTLES.**