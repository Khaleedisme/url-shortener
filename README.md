# URL Shortener

A RESTful URL shortening service built with Spring Boot and Redis.

## Tech Stack

- Java 21
- Spring Boot 3.4
- Redis 8
- Docker

## Features

- Shorten any URL to an 8-character code
- Track click count per shortened URL
- Automatic expiration (30 days TTL)
- RFC 9457 compliant error responses

## Getting Started

### Prerequisites

- Java 21
- Docker

### Run Redis

```bash
docker run -d --name redis-test -p 6379:6379 redis:8.4.2-alpine3.22
```

### Run the Application

```bash
./mvnw spring-boot:run
```

## API Reference

### Shorten URL
POST /api/urls?originalUrl=https://youtube.com

**Response:**
```json
{
  "shortCode": "a1b2c3d4",
  "originalUrl": "https://youtube.com",
  "createdAt": 1745231400,
  "clickCount": 0
}
```

### Resolve URL
GET /api/urls/{shortCode}

**Response:**
```json
{
  "shortCode": "a1b2c3d4",
  "originalUrl": "https://youtube.com",
  "createdAt": 1745231400,
  "clickCount": 1
}
```

## Project Structure
src/main/java/com/xalid/urlshortener/
├── config/
│   ├── AppProperties.java
│   └── RedisConfig.java
├── controller/
│   └── UrlController.java
├── exception/
│   ├── GlobalExceptionHandler.java
│   └── UrlNotFoundException.java
├── model/
│   └── UrlMapping.java
└── service/
└── UrlService.java
