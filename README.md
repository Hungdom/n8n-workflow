# n8n Docker Setup

This repository contains Docker configuration for running n8n with PostgreSQL database.

## Prerequisites

- Docker
- Docker Compose

## Configuration

The setup uses the following default configuration:

- n8n runs on port 5678
- PostgreSQL runs on port 5432
- Default database credentials:
  - Database: n8n
  - Username: n8n
  - Password: n8n

You can modify these settings by:
1. Editing the `docker-compose.yml` file
2. Setting environment variables before running docker-compose

## Running n8n

To start n8n and its dependencies:

```bash
docker-compose up -d
```

To stop the services:

```bash
docker-compose down
```

## Accessing n8n

Once running, you can access n8n at:
- http://localhost:5678

## Environment Variables

You can configure n8n by setting the following environment variables:

- `N8N_HOST`: The host n8n runs on (default: localhost)
- `N8N_PORT`: The port n8n runs on (default: 5678)
- `N8N_PROTOCOL`: The protocol to use (default: http)
- `N8N_USER_MANAGEMENT_DISABLED`: Disable user management (default: false)
- `N8N_BASIC_AUTH_ACTIVE`: Enable basic authentication (default: false)

## Data Persistence

The setup includes two Docker volumes:
- `n8n_data`: Stores n8n data
- `postgres_data`: Stores PostgreSQL data

These volumes ensure your data persists between container restarts. 