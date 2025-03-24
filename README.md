# Docker Useful Commands

## Docker Images

### Build an image from a Dockerfile:
```sh
docker build -t image_name path_to_dockerfile
# Example
docker build -t myapp .
```

### List all local images:
```sh
docker images
# Example
docker lsimage
```

### Pull an image from Docker Hub:
```sh
docker pull image_name:tag
# Example
docker pull nginx:latest
```

### Remove a local image:
```sh
docker rmi image_name:tag
# Example
docker rmi myapp:latest
```

### Tag an image:
```sh
docker tag source_image:tag new_image:tag
# Example
docker tag myapp:latest myapp:v1
```

### Push an image to Docker Hub:
```sh
docker push image_name:tag
# Example
docker push myapp:v1
```

### Inspect details of an image:
```sh
docker inspect image image_name:tag
# Example
docker inspect image myapp:v1
```

### Save an image to a tar archive:
```sh
docker save -o image_name.tar image_name:tag
# Example
docker save -o myapp.tar myapp:v1
```

### Load an image from a tar archive:
```sh
docker load -i image_name.tar
# Example
docker load -i myapp.tar
```

### Prune unused images:
```sh
docker image prune
```

## Docker Containers

### Run a container from an image:
```sh
docker run container_name image_name
# Example
docker run myapp
```

### Run a named container from an image:
```sh
docker run --name container_name image_name:tag
# Example
docker run --name my_container myapp:v1
```

### List all running containers:
```sh
docker ps
```

### List all containers (including stopped ones):
```sh
docker ps -a
```

### Stop a running container:
```sh
docker stop container_name_or_id
# Example
docker stop my_container
```

### Start a stopped container:
```sh
docker start container_name_or_id
# Example
docker start my_container
```

### Remove a stopped container:
```sh
docker rm container_name_or_id
# Example
docker rm my_container
```

### Remove a running container (forcefully):
```sh
docker rm -f container_name_or_id
# Example
docker rm -f my_container
```

### Inspect details of a container:
```sh
docker inspect container_name_or_id
# Example
docker inspect my_container
```

### View container logs:
```sh
docker logs container_name_or_id
# Example
docker logs my_container
```

## Docker Volumes and Networks

### Create a named volume:
```sh
docker volume create volume_name
# Example
docker volume create my_volume
```

### List all volumes:
```sh
docker volume ls
```

### Inspect details of a volume:
```sh
docker volume inspect volume_name
# Example
docker volume inspect my_volume
```

### Remove a volume:
```sh
docker volume rm volume_name
# Example
docker volume rm my_volume
```

### Run a container with a volume (mount):
```sh
docker run --name container_name -v volume_name:/path/in/container image_name:tag
# Example
docker run --name my_container -v my_volume:/app/data myapp:v1
```

### List all networks:
```sh
docker network ls
```

### Create a user-defined bridge network:
```sh
docker network create network_name
# Example
docker network create my_network
```

### Connect a container to a network:
```sh
docker network connect network_name container_name
# Example
docker network connect my_network my_container
```

### Disconnect a container from a network:
```sh
docker network disconnect network_name container_name
# Example
docker network disconnect my_network my_container
```

## Docker Compose

### Create and start containers defined in a `docker-compose.yml` file:
```sh
docker-compose up -d
```

### Stop and remove containers defined in a `docker-compose.yml` file:
```sh
docker-compose down
```

### Build or rebuild services:
```sh
docker-compose build
```

### List containers for a specific Docker Compose project:
```sh
docker-compose ps
```

### View logs for services:
```sh
docker-compose logs
```

### Scale services to a specific number of containers:
```sh
docker-compose up -d --scale service_name=number_of_containers
# Example
docker-compose up -d --scale web=3
```

### Run a one-time command in a service:
```sh
docker-compose run service_name command
# Example
docker-compose run web npm install
```

## Dockerfile Reference

### Example Dockerfile:
```dockerfile
# Use an official Node.js runtime as a base image
FROM node:20-alpine

# Set the working directory to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the current directory contents to the container at /app
COPY . .

# Expose port 8080 to the outside world
EXPOSE 8080

# Define environment variable
ENV NODE_ENV=production

# Run app.js when the container launches
CMD ["node", "app.js"]
```
---
