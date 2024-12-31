# Docker Documentation

## Introduction
Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications.

## Table of Contents
1. [Getting Started](#getting-started)
2. [Docker Commands](#docker-commands)
3. [Dockerfile](#dockerfile)
4. [Docker Compose](#docker-compose)
5. [Best Practices](#best-practices)
6. [Troubleshooting](#troubleshooting)

## Getting Started
1. **Run your first container**:
    ```sh
    docker run hello-world
    ```
2. **List running containers**:
    ```sh
    docker ps
    ```
3. **Stop a container**:
    ```sh
    docker stop <container_id>
    ```

## Docker Commands
- `docker run`: Run a container.
- `docker ps`: List containers.
- `docker stop`: Stop a running container.
- `docker build`: Build an image from a Dockerfile.
- `docker pull`: Pull an image from a registry.
- `docker push`: Push an image to a registry.

## Dockerfile
A `Dockerfile` is a text document that contains all the commands to assemble an image. Example:
```Dockerfile
# Use an official Python runtime as a parent image
FROM python:3.8-slim

# Set the working directory
WORKDIR /app

# Copy the current directory contents into the container
COPY . /app

# Install any needed packages
RUN pip install --no-cache-dir -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Run app.py when the container launches
CMD ["python", "app.py"]
```

## Docker Compose
Docker Compose is a tool for defining and running multi-container Docker applications. Example `docker-compose.yml`:
```yaml
version: '3'
services:
  web:
     image: my-web-app
     build: .
     ports:
        - "5000:5000"
  redis:
     image: "redis:alpine"
```
Run with:
```sh
docker-compose up
```

## Best Practices
- Keep images small.
- Use multi-stage builds.
- Leverage caching.
- Regularly update base images.

## Troubleshooting
- **Check logs**: `docker logs <container_id>`
- **Inspect container**: `docker inspect <container_id>`
- **Remove unused data**: `docker system prune`
