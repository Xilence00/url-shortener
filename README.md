# URL Shortener

A simple URL shortener service built with Express.js and Redis.

## Features

- **Basic URL Shortening**: Create short URLs from long URLs
- **Custom Code**: Customize the short code for your URLs
- **Click Counter**: Track the number of clicks for each short URL
- **Toggle**: Enable/disable short URLs without deleting them
- **Web UI**: User-friendly interface for managing URLs

## Prerequisites

- Node.js 14.x or higher
- Redis server (for production) or Docker (for development)

## Getting Started

### 1. Install Dependencies

```bash
npm install
```

### 2. Run Unit Tests

```bash
npm test
```

### 3. Merge Feature Branches

To get all features, merge the feature branches into main:

```bash
# Merge custom code feature
git merge origin/feat/customcode

# Merge counter feature
git merge origin/feat/counter

# Merge toggle feature
git merge origin/feat/toggle
```

**Note**: You may encounter merge conflicts. Resolve them carefully to ensure all features work together.

### 4. Start the Service

#### Development (with Redis via Docker)

```bash
# Start Redis server
docker run -d -p 6379:6379 redis:7-alpine

# Start the application
npm start
```

#### Production (with existing Redis)

```bash
# Set Redis connection string (optional)
export REDIS_HOST=localhost

# Start the application
npm start
```

### 5. Access the Application

- **Web UI**: http://localhost:3000/ui
- **API Health Check**: http://localhost:3000/api/health
- **API Documentation**:
  - `POST /api/shorten` - Create short URL
  - `GET /api/urls` - List all URLs
  - `DELETE /api/:code` - Delete short URL
  - `GET /:code` - Redirect to destination URL

## Docker Deployment

### Build Docker Image

```bash
docker build -t <dockerhub-username>/url-shortener:latest .
```

### Run with Docker Compose

```bash
docker-compose up -d
```

Access the application at http://localhost:3000/ui

## Project Structure

```
url-shortener/
├── src/
│   ├── index.js      # Main Express application
│   └── redis.js      # Redis client and operations
├── www/
│   ├── index.html    # Web UI HTML
│   ├── app.js        # Web UI JavaScript
│   ├── app.css       # Web UI styles
│   └── icons.svg     # UI icons
├── tests/
│   ├── app.test.js       # Basic API tests
│   ├── customcode.test.js # Custom code feature tests
│   ├── counter.test.js    # Counter feature tests
│   └── toggle.test.js     # Toggle feature tests
└── package.json
```

## Environment Variables

- `PORT` - Server port (default: 3000)
- `REDIS_HOST` - Redis connection URL (default: localhost)
- `BUILD_TIME` - Build timestamp (set automatically in Docker)
- `STUDENT_ID` - Student ID for exam purposes (set automatically in Docker)

## License

MIT
