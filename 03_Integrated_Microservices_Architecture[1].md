# Integrated Microservices Architecture

## Objective
Design and integrate a microservices architecture using API Gateway, Eureka Server, and multiple backend services.

## Architecture Components

| Component | Description |
|---|---|
| API Gateway | Central entry point for client requests |
| Eureka Server | Service registry and discovery server |
| User Service | Handles user-related business operations |
| Task Service | Handles task-related business operations |
| Client App/Postman | Sends requests through the API Gateway |

## Architecture Flow

```text
Client / Postman
       |
       v
API Gateway :8080
       |
       v
Eureka Server :8761
       |
       +----------------------+
       |                      |
       v                      v
User Service :8081       Task Service :8082
```

## Communication Flow
1. Eureka Server starts on port `8761`.
2. User Service and Task Service register with Eureka.
3. API Gateway registers with Eureka.
4. Client sends request to API Gateway.
5. Gateway uses Eureka to locate the correct service.
6. Request is routed to the available service instance.
7. Response is returned back through the Gateway.

## Sample Service Ports

| Service | Port |
|---|---:|
| Eureka Server | 8761 |
| API Gateway | 8080 |
| User Service | 8081 |
| Task Service | 8082 |

## Benefits
- Centralized routing
- Dynamic service discovery
- Load-balanced service communication
- Easier scalability
- Loose coupling between services
- Improved maintainability

## Deliverable Status
Integrated microservices architecture is ready for local execution and testing.
