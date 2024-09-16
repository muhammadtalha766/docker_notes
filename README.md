Here’s the updated Docker README file with `docker commit`, `docker login`, `docker logout`, and port binding commands added:

```markdown
# Docker Commands Cheat Sheet

This guide provides a quick reference to commonly used Docker commands.

## General Commands
- **Check Docker Version**:  
  ```bash
  docker -v
  ```
- **List Running Containers**:  
  ```bash
  docker ps
  ```
- **List All Containers (Including Stopped)**:  
  ```bash
  docker ps -a
  ```
- **List All Images**:  
  ```bash
  docker image ls
  ```
  or
  ```bash
  docker images
  ```

## Container Management
- **Run a New Container in Detached Mode (Background) with Port Binding**:  
  ```bash
  docker container run -dt -p <host_port>:<container_port> <image_name>
  ```
  Example:  
  ```bash
  docker container run -dt -p 8080:80 nginx
  ```
  - `-p`: Binds the host port to the container port.

- **Run a New Container and Access Shell (Interactive Mode)**:  
  ```bash
  docker container run -it <image_name>
  ```
  Example:  
  ```bash
  docker container run -it ubuntu
  ```
  - `-it`: Interactive mode, lets you access the shell inside the container.

- **Enter an Existing Container**:  
  ```bash
  docker container exec -it <container_id> /bin/bash
  ```
  or
  ```bash
  docker exec -it <container_id> /bin/bash
  ```
  Example:  
  ```bash
  docker exec -it 123abc456 /bin/bash
  ```

- **Exit a Container Shell**:  
  ```bash
  exit
  ```

- **Detach from a Container Without Stopping It**:  
  Use `Ctrl+P` followed by `Ctrl+Q` to detach and keep the container running.

- **Start a Stopped Container**:  
  ```bash
  docker start <container_id>
  ```

- **Stop a Running Container**:  
  ```bash
  docker stop <container_id>
  ```

- **Remove a Stopped Container**:  
  ```bash
  docker rm <container_id>
  ```

- **Save Changes to a Running Container (Commit Changes)**:  
  ```bash
  docker commit <container_id> <new_image_name>
  ```
  Example:  
  ```bash
  docker commit 123abc456 my_custom_nginx
  ```

## Image Management
- **Pull an Image from Docker Hub**:  
  ```bash
  docker pull <image_name>
  ```
  Example:  
  ```bash
  docker pull ubuntu
  ```

- **Build an Image from a Dockerfile**:  
  ```bash
  docker build -t <image_name> <path_to_dockerfile>
  ```
  Example:  
  ```bash
  docker build -t myapp .
  ```

- **Tag an Image**:  
  ```bash
  docker tag <image_id> <new_tag>
  ```

- **Push an Image to Docker Hub**:  
  ```bash
  docker push <image_name>
  ```

- **Remove an Image**:  
  ```bash
  docker rmi <image_id>
  ```

## Dockerfile Commands
A `Dockerfile` is used to define the steps for creating a Docker image.

- **Basic Example**:
  ```Dockerfile
  # Use an existing image as a base
  FROM ubuntu:latest
  
  # Set working directory
  WORKDIR /app
  
  # Copy files to the container
  COPY . /app
  
  # Install dependencies
  RUN apt-get update && apt-get install -y python3
  
  # Specify a command to run
  CMD ["python3", "app.py"]
  ```

- **Build an Image Using a Dockerfile**:  
  ```bash
  docker build -t <image_name> .
  ```

## Docker Compose Commands
Docker Compose helps define and run multi-container Docker applications using a `docker-compose.yml` file.

- **Basic Example**:
  ```yaml
  version: '3'
  services:
    web:
      image: nginx
      ports:
        - "8080:80"
    db:
      image: mysql
      environment:
        MYSQL_ROOT_PASSWORD: example
  ```

- **Start Services Defined in `docker-compose.yml`**:  
  ```bash
  docker-compose up
  ```

- **Start Services in Detached Mode**:  
  ```bash
  docker-compose up -d
  ```

- **Stop Running Services**:  
  ```bash
  docker-compose down
  ```

- **View Active Services**:  
  ```bash
  docker-compose ps
  ```

- **Scale Services**:  
  ```bash
  docker-compose up --scale <service_name>=<number>
  ```

## Docker Hub Management
- **Log In to Docker Hub**:  
  ```bash
  docker login
  ```
  You'll be prompted to enter your Docker Hub username and password.

- **Log Out of Docker Hub**:  
  ```bash
  docker logout
  ```

## Volume & Network
- **List Volumes**:  
  ```bash
  docker volume ls
  ```

- **Create a Volume**:  
  ```bash
  docker volume create <volume_name>
  ```

- **Attach a Volume to a Container**:  
  ```bash
  docker run -d -v <volume_name>:/path/in/container <image_name>
  ```

- **List Docker Networks**:  
  ```bash
  docker network ls
  ```

- **Create a Network**:  
  ```bash
  docker network create <network_name>
  ```

- **Connect a Container to a Network**:  
  ```bash
  docker network connect <network_name> <container_name>
  ```

## Miscellaneous
- **Inspect a Container or Image**:  
  ```bash
  docker inspect <container_id/image_id>
  ```

- **View Docker System Information**:  
  ```bash
  docker info
  ```

- **Clean Up Unused Resources (Containers, Images, Volumes, and Networks)**:  
  ```bash
  docker system prune
  ```

---

Feel free to contribute by adding more commands or examples!
``
