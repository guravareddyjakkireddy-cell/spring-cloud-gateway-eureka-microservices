# Eureka Server Setup – Service Discovery

## Objective
Implement Eureka Server to allow microservices to register themselves and discover other services dynamically.

## Technology Stack
- Java 17
- Spring Boot
- Spring Cloud Netflix Eureka Server
- Maven

## Eureka Server Responsibilities
- Maintain registry of available microservices
- Provide service discovery for API Gateway and backend services
- Support dynamic scaling of service instances
- Improve communication reliability between services

## Main Application Class

```java
package com.example.eurekaserver;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.server.EnableEurekaServer;

@SpringBootApplication
@EnableEurekaServer
public class EurekaServerApplication {
    public static void main(String[] args) {
        SpringApplication.run(EurekaServerApplication.class, args);
    }
}
```

## Sample `application.yml`

```yaml
server:
  port: 8761

spring:
  application:
    name: eureka-server

eureka:
  client:
    register-with-eureka: false
    fetch-registry: false
```

## Microservice Eureka Client Configuration

```yaml
eureka:
  client:
    service-url:
      defaultZone: http://localhost:8761/eureka/
```

## Expected Output
Eureka Dashboard should be available at:

```text
http://localhost:8761
```

All microservices should appear as registered applications.
