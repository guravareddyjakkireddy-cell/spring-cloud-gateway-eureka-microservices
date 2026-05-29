# Testing Documentation – Microservices Communication

## Objective
Validate communication between API Gateway, Eureka Server, User Service, and Task Service.

## Testing Scope
- Verify Eureka Server startup
- Verify service registration
- Verify Gateway routing
- Verify load-balanced communication
- Validate API responses through Gateway

## Pre-Requisites
- Java 17 installed
- Maven installed
- Postman or browser available
- All services configured with Eureka Client
- Ports available: `8761`, `8080`, `8081`, `8082`

## Test Execution Order

### Step 1: Start Eureka Server
Run Eureka Server application.

Expected URL:

```text
http://localhost:8761
```

Expected Result:
- Eureka dashboard opens successfully.

### Step 2: Start User Service
Expected Result:
- `USER-SERVICE` appears in Eureka dashboard.

### Step 3: Start Task Service
Expected Result:
- `TASK-SERVICE` appears in Eureka dashboard.

### Step 4: Start API Gateway
Expected Result:
- `API-GATEWAY` appears in Eureka dashboard.

## API Gateway Test Cases

| Test Case ID | Scenario | Endpoint | Expected Result |
|---|---|---|---|
| TC-001 | Check User Service route | `GET http://localhost:8080/api/users` | User service response returned |
| TC-002 | Check Task Service route | `GET http://localhost:8080/api/tasks` | Task service response returned |
| TC-003 | Invalid route validation | `GET http://localhost:8080/api/invalid` | 404 Not Found |
| TC-004 | Eureka dashboard validation | `http://localhost:8761` | All services registered |
| TC-005 | Load balancing validation | Multiple calls to same endpoint | Requests handled successfully |

## Sample Postman Testing Steps
1. Open Postman.
2. Select GET request.
3. Enter Gateway URL.
4. Click Send.
5. Validate HTTP status code and response body.

## Expected Final Result
All microservices should communicate through API Gateway using Eureka-based service discovery.
