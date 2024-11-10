# Gateway Service

This is the Gateway Service for a microservice-based architecture using Spring Boot and Spring Cloud Gateway. It routes requests to the appropriate microservices.

## Prerequisites

- Java 21
- Maven
- Eureka Server running on `http://localhost:8761/eureka`

## Getting Started

### Clone the Repository

```sh
git clone https://github.com/your-username/gateway-service.git
cd gateway-service
```

### Build the Project
```sh
mvn clean install
```

### Run the Application
```sh
mvn spring-boot:run
```

### Configuration
The application is configured to register with Eureka and route requests to the productservice and userservice microservices.
application.properties
```sh
spring.application.name=gateway
eureka.client.registerWithEureka=true
eureka.client.fetchRegistry=true
eureka.client.service-url.defaultZone=http://localhost:8761/eureka
```
### Request Routing mappings
```sh
# /products/* -> productservice
# /userservice/* -> productservice
spring.cloud.gateway.routes[0].id=productservice
spring.cloud.gateway.routes[0].predicates[0]=Path=/products/*
spring.cloud.gateway.routes[0].uri=lb://productservice

spring.cloud.gateway.routes[1].id=userservice
spring.cloud.gateway.routes[1].predicates[0]=Path=/products/*
spring.cloud.gateway.routes[1].uri=lb://userservice
```
### Dependencies
```sh
spring-cloud-starter-gateway
spring-cloud-starter-netflix-eureka-client
spring-cloud-starter-loadbalancer
spring-boot-devtools
spring-boot-configuration-processor
lombok
spring-boot-starter-actuator
spring-boot-starter-test
```
## License
This project is licensed under the MIT License.
