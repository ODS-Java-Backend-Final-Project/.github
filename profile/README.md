# 🎲  Board Game Meetup Backend - Board Game Microservices Application

## 📝 Project Description

**GameMeetUp** is a microservices-based application that allows users to explore a collection of board games and link them to social events based on their interests. The goal of the platform is to connect people with board games tailored to their mood, group size, theme preferences, or environment, and to facilitate event planning around those games.

The application includes:
- Management of board games.
- Creation and management of events tied to specific games.
- Cross-service communication using OpenFeign to associate games with events.
- Service discovery with Eureka and centralized routing through an API Gateway.

## 🧩 UML Class Diagram(s)



## 🏗️ Microservice Architecture Overview
```
                            +----------------------+
                            |     API Gateway      |
                            |  (Spring Cloud GW)   |
                            +----------+-----------+
                                       |
     +---------------------------------+---------------------------------+
     |                                 |                                 |
+------------------------+ +------------------------+ +---------------------------+
| board-game-service     | | event-service          | | discovery-service (Eureka)|
| Manages boar           | | Manages events linked  | | Service registry          |
| games (CRUD)           | | to board games (CRUD)  | |                           |
+------------------------+ +------------------------+ +---------------------------+
```

Uses Feign Client to fetch board game details

- **board-game-service**: Handles CRUD operations for board games.
- **event-service**: Manages event creation and association with games.
- **discovery-service**: Eureka Server for dynamic service registration and discovery.
- **api-gateway**: Centralized entry point for routing API requests.

## ⚙️ Setup Instructions for Local Development

### 1. Clone the Repositories you can find in this organization, for example the event-service:

```bash
git clone https://github.com/ODS-Java-Backend-Final-Project/event-service.git
cd event-service
```

2. Run MySQL Database

Make sure you have a MySQL instance running on port 3306

3. Configuration & Ports
Service	Port	Description
discovery-service	8761	Eureka Server
api-gateway	8080	API Gateway (entry point)
board-game-service	8081	Board game CRUD
event-service	8082	Event CRUD

Sample application.properties:

spring.application.name=event-service
spring.datasource.url=jdbc:mysql://localhost:3306/event_service
spring.datasource.username=root
spring.datasource.password=admin
spring.jpa.hibernate.ddl-auto=update
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
eureka.client.service-url.defaultZone=http://localhost:8761/eureka/
server.port=8082

4. Build and Run the Application

From the root directory:

mvn clean install

Then start each service individually:

cd discovery-service && mvn spring-boot:run
cd api-gateway && mvn spring-boot:run
cd board-game-service && mvn spring-boot:run
cd event-service && mvn spring-boot:run

🧪 Technologies Used & Route Overview
Technologies

    Java 21

    Spring Boot

    Spring Cloud (Eureka, Gateway, OpenFeign)

    Spring Data JPA + MySQL

    JUnit and Mockito

    Postman (for API testing)

    Lombok

Main API Endpoints
📦 board-game-service

GET    /api/board-games            → Get all board games
GET    /api/board-games/{id}       → Get game by ID
POST   /api/board-games            → Create a new board game
PUT    /api/board-games/{id}       → Update board game
DELETE /api/board-games/{id}       → Delete board game

🎉 event-service

GET    /api/events                 → Get all events
GET    /api/events/{id}            → Get event by ID
GET    /api/events/board-game/{id} → Get events linked to a specific board game
POST   /api/events                 → Create a new event
PUT    /api/events/{id}            → Update event
DELETE /api/events/{id}            → Delete event

📬 Postman

This project includes a Postman collection with:

    CRUD requests for board games and events

    Sample association queries between events and board games

    Link: [postman/GamesMeetUp](https://craftshop.postman.co/workspace/My-Workspace~64247626-9b1b-40cf-82e4-df164e396f63/collection/39061244-2cab27db-c263-421d-9531-48807903fba6?action=share&creator=39061244&active-environment=39061244-17713532-af05-4d0b-b877-cbb3f0d57619)

🚀 Future Work

    Add user-service with JWT authentication.

    Implement recommendation logic based on game style, mood, and player count.

    Build a front-end client in React connected via the API Gateway.

    Improve error handling with a global exception handler (@ControllerAdvice).

    Add internationalization (i18n) support.

📚 References & Acknowledgments

    Spring Boot Documentation

    Spring Cloud Netflix Eureka

    Spring Cloud Gateway

    Spring Cloud OpenFeign

    PlantUML

    Java Backend with Microservices Bootcamp - Ironhack 2025
