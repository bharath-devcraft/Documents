
# Docker Commands

## Pull Odoo Docker Image
- Pull the Odoo Docker image:
  ```bash
  docker pull odoo   # (Pulling odoo docker image from hub.docker.coodoo:17m)
  ```

## List Docker Images
- List the Docker images:
  ```bash
  docker images
  ```

## Change Permissions
- Grant permissions without using `sudo`:
  ```bash
  sudo chmod 777 /var/run/docker.sock
  ```

## Enter Container
- Enter into a running container:
  ```bash
  docker exec -it <container_id> bash
  ```
- Alternatively, enter the container with a different shell:
  ```bash
  docker exec -it <container_id> /bin/sh
  ```

## Build Custom Docker Image
- Build a custom Docker image:
  ```bash
  docker build -t travelromeobharath/custom-odoo17 .
  ```

## Docker Hub Image Push/Pull
- Log in to Docker Hub:
  ```bash
  docker login
  ```
- Build and push your custom Docker image:
  ```bash
  docker build -t travelromeobharath/custom-odoo17 .
  docker push travelromeobharath/custom-odoo17
  ```

## Start Odoo Server
- Start Odoo server using the `odoo-bin` command:
  ```bash
  python3 ./odoo-bin -c ../odoo.conf
  ```

## Docker Container and Image Management
- Stop Docker container:
  ```bash
  docker stop <container_id>
  ```
- Start Docker container:
  ```bash
  docker start <container_id>
  ```
- Remove Docker image:
  ```bash
  docker rmi <image_id>
  ```
- Remove Docker container:
  ```bash
  docker rm <container_id>
  ```

## Run Odoo Container
- Pull and run Odoo container in one command:
  ```bash
  docker run odoo:latest
  ```
- Run Odoo container with port mapping:
  ```bash
  docker run -p 8071:8069 odoo
  ```

## Logs
- View container logs:
  ```bash
  docker logs <container_id>
  ```
  Or by container name:
  ```bash
  docker logs <container_name>
  ```

## Run Odoo in Detached Mode
- Run Odoo container in detached mode with a custom name:
  ```bash
  docker run -d -p 8071:8069 --name nameyourcontainer odoo:latest
  ```

## Docker Compose Commands
- Start Docker Compose:
  ```bash
  docker-compose -f test.yaml up
  ```
- Stop Docker Compose:
  ```bash
  docker-compose -f test.yaml down
  ```

## Find Docker Container by Image Name
- Find a container by image name:
  ```bash
  docker ps -a | grep <image_name>
  ```

## Remove Unknown Containers
- Remove unknown Docker containers:
  ```bash
  sudo aa-remove-unknown
  ```

## Docker Volumes Management
- List Docker volumes:
  ```bash
  docker volume ls
  ```
- Prune unused Docker volumes:
  ```bash
  docker volume prune
  ```
- Remove specific volume:
  ```bash
  docker volume rm $(docker volume ls -q)
  ```

## Remove All Docker Containers
- Remove all Docker containers:
  ```bash
  docker rm $(docker ps -a -q)
  ```
- Stop all Docker containers:
  ```bash
  docker stop $(docker ps -aq)
  ```

## Remove Volumes and Containers Using Docker Compose
- Remove volumes along with containers in Docker Compose:
  ```bash
  docker-compose down -v
  ```

## Check Port Usage
- Check which process is using a specific port (e.g., 5434):
  ```bash
  sudo lsof -i :5434
  ```

## Create Docker Volume
- Create a new Docker volume:
  ```bash
  docker volume create <volume_name>
  ```

## Inspect Docker Volume
- Inspect a specific Docker volume:
  ```bash
  docker volume inspect <volume_name>
  ```

## Inspect Docker Container
- Inspect a specific Docker container:
  ```bash
  docker inspect <container_name>
  ```

## Display First 5 Docker Images
- Display the first 5 Docker images:
  ```bash
  docker images | head -5
  ```

## Postgres Docker Container Access
- Access a Postgres container:
  ```bash
  docker exec -it <container_name> psql -U <db_user> -d <db_name>
  ```
- Alternatively, after entering the container:
  ```bash
  psql -U <db_user> -d <db_name>
  ```
  Or:
  ```bash
  psql
  ```

## Docker Image Tagging
- Tag a Docker image:
  ```bash
  docker tag <image_name>:<version>
  ```

------------------------------------------------------------------------------------------------------------------


### **Basic Docker Commands**


#### Docker Installation & Information
- **Check Docker version**:
  ```bash
  docker --version
  ```
- **View Docker info** (system-wide information about Docker):
  ```bash
  docker info
  ```

#### Docker Images
- **Pull an image from Docker Hub**:
  ```bash
  docker pull <image_name>:<tag>
  ```
- **List all available Docker images**:
  ```bash
  docker images
  ```
- **Build a Docker image from a Dockerfile**:
  ```bash
  docker build -t <image_name>:<tag> .
  ```
- **Remove a Docker image**:
  ```bash
  docker rmi <image_id or image_name>
  ```
- **Tag a Docker image**:
  ```bash
  docker tag <image_name>:<tag> <new_image_name>:<new_tag>
  ```

#### Docker Containers
- **Run a container from an image**:
  ```bash
  docker run <image_name>:<tag>
  ```
- **Run a container with a specific port mapping**:
  ```bash
  docker run -p <host_port>:<container_port> <image_name>
  ```
- **Run a container in detached mode (background)**:
  ```bash
  docker run -d <image_name>
  ```
- **List running containers**:
  ```bash
  docker ps
  ```
- **List all containers (including stopped ones)**:
  ```bash
  docker ps -a
  ```
- **Stop a running container**:
  ```bash
  docker stop <container_id or container_name>
  ```
- **Start a stopped container**:
  ```bash
  docker start <container_id or container_name>
  ```
- **Remove a container**:
  ```bash
  docker rm <container_id or container_name>
  ```
- **Exec into a running container** (bash shell):
  ```bash
  docker exec -it <container_id or container_name> bash
  ```
- **Exec into a running container** (sh shell):
  ```bash
  docker exec -it <container_id or container_name> sh
  ```

#### Docker Logs
- **View the logs of a container**:
  ```bash
  docker logs <container_id or container_name>
  ```

#### Docker Compose (for Multi-container Applications)
- **Start containers with Docker Compose**:
  ```bash
  docker-compose up
  ```
- **Start containers in detached mode using Docker Compose**:
  ```bash
  docker-compose up -d
  ```
- **Stop containers with Docker Compose**:
  ```bash
  docker-compose down
  ```
- **View logs of containers managed by Docker Compose**:
  ```bash
  docker-compose logs
  ```

#### Docker Network
- **List Docker networks**:
  ```bash
  docker network ls
  ```
- **Create a Docker network**:
  ```bash
  docker network create <network_name>
  ```
- **Inspect a Docker network**:
  ```bash
  docker network inspect <network_name>
  ```

#### Docker Volumes (Persistent Data)
- **List Docker volumes**:
  ```bash
  docker volume ls
  ```
- **Create a Docker volume**:
  ```bash
  docker volume create <volume_name>
  ```
- **Inspect a Docker volume**:
  ```bash
  docker volume inspect <volume_name>
  ```
- **Remove a Docker volume**:
  ```bash
  docker volume rm <volume_name>
  ```

#### Docker System Cleanup
- **Remove unused images, containers, volumes, and networks**:
  ```bash
  docker system prune
  ```
- **Remove all stopped containers**:
  ```bash
  docker rm $(docker ps -a -q)
  ```
- **Remove all unused images**:
  ```bash
  docker rmi $(docker images -q)
  ```

#### Docker Container Networking
- **List all active connections**:
  ```bash
  docker network inspect <network_name>
  ```

### Advanced Docker Commands

#### Docker Build & Push
- **Login to Docker Hub**:
  ```bash
  docker login
  ```
- **Push an image to Docker Hub**:
  ```bash
  docker push <image_name>:<tag>
  ```
- **Build and push a custom image to Docker Hub**:
  ```bash
  docker build -t <username>/<image_name>:<tag> .
  docker push <username>/<image_name>:<tag>
  ```

#### Docker Container Inspection
- **Inspect a running container** (shows detailed container information):
  ```bash
  docker inspect <container_id or container_name>
  ```
  
#### Docker Resource Management
- **Show running processes in a container**:
  ```bash
  docker top <container_id or container_name>
  ```
- **View resource usage of containers** (CPU, memory):
  ```bash
  docker stats
  ```

#### Docker Container Health Checks
- **Run a container with a health check command**:
  ```bash
  docker run --health-cmd="curl --fail http://localhost:8080/health || exit 1" <image_name>
  ```

#### Docker Prune Commands (Clean Up Unused Resources)
- **Remove unused containers, networks, and volumes**:
  ```bash
  docker system prune -a
  ```
- **Remove unused volumes**:
  ```bash
  docker volume prune
  ```

#### Docker Build Caching & Optimizations
- **Build an image without using cache**:
  ```bash
  docker build --no-cache -t <image_name>:<tag> .
  ```

#### Docker Logs and Monitoring
- **View real-time logs for a container**:
  ```bash
  docker logs -f <container_id or container_name>
  ```

#### Docker Container Restart Policies
- **Run a container with restart policies**:
  ```bash
  docker run --restart=always <image_name>
  ```
- **Other restart policies**:
  - `no` (do not automatically restart the container)
  - `on-failure` (restart the container only when it exits with a non-zero status)
  - `always` (always restart the container)
  - `unless-stopped` (restart the container unless it is explicitly stopped)

---
