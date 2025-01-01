# URL Shortener with Go, Redis, and Docker

A high-performance URL shortening service built with Go, using Redis for storage and Docker for containerization.

## Project Structure
```
└── anujagrawal699-URL-Shortener-Golang-Redis-Docker/
    ├── api/                    # Go API service
    │   ├── database/          # Redis connection and operations
    │   ├── helpers/           # Utility functions
    │   ├── routes/            # API endpoints
    │   │   ├── shorten.go     # URL shortening logic
    │   │   └── resolve.go     # Short URL resolution
    │   └── Dockerfile         # API service container
    ├── docker-compose.yml     # Multi-container orchestration
    └── db/                    # Redis configuration
        └── Dockerfile         # Redis container
```

## Prerequisites
- Docker and Docker Compose
- Go >= 1.18 (for local development)

## Quick Start
```bash
# Start the service
docker-compose up -d

# Stop the service
docker-compose down
```

## API Endpoints

### Shorten URL
```
POST /api/v1/shorten
Content-Type: application/json

{
    "url": "https://example.com/long-url"
}
```

### Resolve URL
```
GET /:shortURL
```

## Environment Variables
```env
# api/.env
REDIS_URL=redis://redis:6379
API_PORT=3000
DOMAIN=localhost:3000
```

## Development Setup

### Local Development
```bash
cd api
go mod tidy
go run main.go
```

### Docker Build
```bash
# Build images
docker build -t url-shortener-api ./api
docker build -t url-shortener-redis ./db

# Run with Docker Compose
docker-compose up -d
```

## Architecture

- **API Service**: Go service handling URL shortening and resolution
- **Redis**: In-memory database for storing URL mappings
- **Docker**: Containerization for consistent deployment
- **Docker Compose**: Multi-container orchestration

## Performance Features

- Redis for high-speed URL lookups
- Concurrent request handling
- Connection pooling
- Docker for scalable deployment
