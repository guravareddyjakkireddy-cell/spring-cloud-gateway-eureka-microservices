# API Gateway Configuration – Spring Cloud Gateway

## Objective
Configure a centralized API Gateway using Spring Cloud Gateway to route all client requests to backend microservices.

## Technology Stack
- Java 17
- Spring Boot
- Spring Cloud Gateway
- Spring Cloud Netflix Eureka Client
- Maven
- REST APIs

## Gateway Responsibilities
- Centralized routing for all microservices
- Dynamic service discovery using Eureka
- Load-balanced routing through service names
- Common entry point for client applications
- Route-level logging and request tracing support

## Sample `application.yml`

```yaml
server:
  port: 8080

spring:
  application:
    name: api-gateway

  cloud:
    gateway:
      discovery:
        locator:
          enabled: true
          lower-case-service-id: true

      routes:
        - id: user-service
          uri: lb://USER-SERVICE
          predicates:
            - Path=/api/users/**

        - id: task-service
          uri: lb://TASK-SERVICE
          predicates:
            - Path=/api/tasks/**

eureka:
  client:
    service-url:
      defaultZone: http://localhost:8761/eureka/
```

## Key Configuration Points
- `lb://USER-SERVICE` enables client-side load balancing.
- Gateway retrieves service instances from Eureka Server.
- Routes are defined based on URL path predicates.
- All backend services are hidden from direct external access.

## Expected Output
Client requests should pass through the API Gateway and be routed to the appropriate microservice.
