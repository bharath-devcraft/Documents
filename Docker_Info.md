
```markdown
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

## References
- [Codeclef: Docker Commands to Stop and Remove All Images and Containers](https://codeclef.medium.com/docker-commands-to-stop-and-remove-all-images-and-containers-2995c5c5f586)
```

### Notes:
- Replace placeholder `<container_name>`, `<image_name>`, `<volume_name>`, `<db_user>`, and `<db_name>` with your actual values.
- Markdown formatting will ensure these commands are easy to read and execute from your repository documentation.
