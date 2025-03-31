# Docker Deployment Guide

This guide provides instructions for building and deploying the application using Docker.

## Prerequisites

- Docker installed on your machine
- Docker Compose installed on your machine

## Deployment Steps

### Option 1: Using Docker Compose (Recommended)

1. Clone the repository
2. Make sure your `.env.local` file is properly configured
3. Build and start the containers:
   ```
   docker-compose up -d
   ```
4. The application will be available at http://localhost:3000

To stop the containers:
```
docker-compose down
```

### Option 2: Using Docker directly

1. Build the Docker image:
   ```
   docker build -t mock-interview-platform .
   ```

2. Run the Docker container:
   ```
   docker run -p 3000:3000 mock-interview-platform
   ```

3. The application will be available at http://localhost:3000

## Environment Variables

The application uses environment variables for configuration. These are loaded from the `.env.local` file during the Docker build process. If you need to modify these variables after building the image, you can:

1. Update the `.env.local` file
2. Rebuild the Docker image
3. Restart the container

## Troubleshooting

### Container fails to start

Check the logs for any errors:
```
docker logs <container_id>
```

### Application cannot connect to external services

Make sure your environment variables in `.env.local` are correctly configured and that the services are accessible from within the container.

## Production Deployment

For production deployment, consider the following:

1. Use a reverse proxy like Nginx to handle HTTPS
2. Set up proper container orchestration (Kubernetes, Docker Swarm, etc.)
3. Implement proper logging and monitoring
4. Use a CI/CD pipeline for automated deployments 