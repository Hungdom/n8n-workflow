# n8n Docker Setup

This repository contains Docker configuration for running n8n with PostgreSQL database.

## Prerequisites

- Docker
- Docker Compose

## Directory Structure

```
n8n/
├── data/              # n8n data directory
├── workflows/         # n8n workflows directory
├── postgres-data/     # PostgreSQL data directory
├── Dockerfile
├── docker-compose.yml
└── README.md
```

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
- `N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS`: Enforce correct file permissions (default: true)

## Data Persistence

The setup uses local directories for data persistence:

- `./data`: Stores n8n general data
- `./workflows`: Stores n8n workflows
- `./postgres-data`: Stores PostgreSQL data

These directories are mounted directly into the containers, ensuring your data persists between container restarts and is version controlled in your repository.

## Workflow Management

Your n8n workflows will be stored in the `workflows` directory. You can:
1. Version control your workflows
2. Share workflows between team members
3. Backup workflows easily
4. Deploy workflows to different environments

## Security Notes

- The setup uses a dedicated `n8n` user inside the container
- File permissions are enforced for security
- PostgreSQL data is stored in a separate volume
- All sensitive data is stored in environment variables 