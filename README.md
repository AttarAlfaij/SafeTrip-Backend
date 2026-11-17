# Safe Trip Planner - Spring Boot Backend

The backend REST API and authentication service for **Safe Trip Planner**, built with Java 17 and Spring Boot 3.

---

## Features

- **JWT Authentication & Stateless Security**: Custom JWT token generation and validation with automated user principal mapping.
- **OAuth2 Social Login**: Google and GitHub OAuth2 authentication integration.
- **Trip & Itinerary Management**: APIs for generating, saving, managing, and retrieving travel itineraries with mood-based recommendation logic.
- **Curated & Live Geo Services**: Intelligent destination discovery with curated offline fallbacks and Overpass / OpenStreetMap / Nominatim integration.
- **User Data Isolation**: Secure data isolation ensuring users only access their own itineraries.
- **Containerized**: Production-ready `Dockerfile` based on Eclipse Temurin JDK 17.

---

## Tech Stack

- **Java**: 17
- **Framework**: Spring Boot 3.2.5
- **Build Tool**: Maven Wrapper (`mvnw`)
- **Database**: MySQL (production/local) & H2 in-memory (automated testing)
- **Security**: Spring Security 6, JJWT (io.jsonwebtoken 0.12.5), OAuth2 Client
- **ORM**: Spring Data JPA / Hibernate 6

---

## Getting Started

### Prerequisites

- Java 17 or higher
- MySQL 8.x (or Railway MySQL database)

### Configuration

1. Copy the example configuration template:
   ```bash
   cp src/main/resources/application.properties.example src/main/resources/application.properties
   ```
2. Or configure via environment variables:
   - `PORT`: Server port (default: `8080`)
   - `SPRING_DATASOURCE_URL`: MySQL JDBC URL (e.g. `jdbc:mysql://localhost:3306/safetrip_db`)
   - `SPRING_DATASOURCE_USERNAME`: Database username
   - `SPRING_DATASOURCE_PASSWORD`: Database password
   - `GITHUB_CLIENT_ID`: GitHub OAuth App Client ID
   - `GITHUB_CLIENT_SECRET`: GitHub OAuth App Client Secret
   - `GOOGLE_CLIENT_ID`: Google OAuth 2.0 Client ID
   - `GOOGLE_CLIENT_SECRET`: Google OAuth 2.0 Client Secret
   - `FRONTEND_URL`: URL of the React frontend (default: `http://localhost:5173`)
   - `JWT_SECRET`: 256-bit signing key for JWTs (optional; a secure random HMAC-SHA256 key is generated in-memory if omitted)
   - `JWT_EXPIRATION_MS`: Token expiration in milliseconds (default: `86400000` / 24 hours)

### Build and Run

To run locally with Maven Wrapper:

```bash
# Windows
.\mvnw.cmd spring-boot:run

# Linux / macOS
./mvnw spring-boot:run
```

To run test suites:

```bash
# Windows
.\mvnw.cmd test

# Linux / macOS
./mvnw test
```

### Docker Build

```bash
docker build -t safe-trip-backend .
docker run -p 8080:8080 safe-trip-backend
```
