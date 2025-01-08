### **Docker Installation, Configuration, Volumes, and Running Odoo Example**


---

### 1. **Docker Installation**

#### On Ubuntu (or any Linux-based OS):
```bash
# Update system package list
sudo apt-get update

# Install necessary packages
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common

# Add Docker’s official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# Add Docker repository to APT sources
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

# Update package list and install Docker
sudo apt-get update
sudo apt-get install docker-ce

# Verify Docker is installed correctly
docker --version
```

#### On Windows and Mac:
- Install Docker Desktop from the official Docker website: https://www.docker.com/products/docker-desktop

---

### 2. **Docker Configuration**

After installing Docker, ensure that the Docker service is running correctly:

```bash
# Start Docker service
sudo systemctl start docker

# Enable Docker to start on boot
sudo systemctl enable docker

# Check Docker status
sudo systemctl status docker
```

To manage Docker without `sudo` (Optional):
```bash
# Add your user to the Docker group
sudo usermod -aG docker $USER

# Log out and log back in
```

Verify Docker works by running the hello-world container:
```bash
docker run hello-world
```

---

### 3. **Creating and Running Odoo in Docker**

#### Step 1: **Create Dockerfile for Odoo**

First, you need to create a **Dockerfile** to set up Odoo. Here's a simple example of the `Dockerfile` for Odoo.

```dockerfile
# Use official Odoo base image
FROM odoo:17

# Set environment variables (Optional)
ENV LANG C.UTF-8

# Copy custom configurations or modules (if any)
# COPY ./my_addons /mnt/extra-addons

# Set working directory
WORKDIR /mnt/extra-addons

# Install dependencies (Optional for additional Odoo modules)
RUN pip install -r requirements.txt

# Expose the port where Odoo will be running
EXPOSE 8069

# Start Odoo server
CMD ["odoo", "-c", "/etc/odoo/odoo.conf"]
```

Save this `Dockerfile` in your project directory.

#### Step 2: **Create Docker-Compose Configuration (`docker-compose.yml`)**

To run Odoo in Docker, it is recommended to use `docker-compose` to define services and networks. Create a `docker-compose.yml` file.

```yaml
version: '3'
services:
  odoo:
    image: odoo:17
    container_name: odoo_container
    ports:
      - "8071:8069"
    environment:
      - HOST=odoo_db
      - USER=odoo
      - PASSWORD=odoo
    volumes:
      - odoo-data:/var/lib/odoo
      - ./odoo-config:/etc/odoo
    networks:
      - odoo-network
    depends_on:
      - odoo_db

  odoo_db:
    image: postgres:13
    container_name: odoo_db
    environment:
      - POSTGRES_USER=odoo
      - POSTGRES_PASSWORD=odoo
      - POSTGRES_DB=odoo
    volumes:
      - postgres-data:/var/lib/postgresql/data
    networks:
      - odoo-network

volumes:
  odoo-data:
  postgres-data:

networks:
  odoo-network:
    driver: bridge
```

Explanation:
- `odoo`: Odoo service running on port 8071.
- `odoo_db`: PostgreSQL database service running for Odoo.
- `volumes`: Persisting data for Odoo and PostgreSQL.
- `networks`: Using a custom bridge network for both services to communicate.

#### Step 3: **Directory Structure**

Ensure your directory structure looks like this:

```
/my-odoo-project
  |-- docker-compose.yml
  |-- Dockerfile
  |-- odoo-config/          # Optional: Custom Odoo configuration (odoo.conf)
  |-- my_addons/            # Optional: Custom Odoo modules (if any)
```

#### Step 4: **Running the Docker Containers**

Now, go to the directory where you have the `docker-compose.yml` file and run the following command:

```bash
docker-compose up -d
```

- The `-d` flag runs the containers in detached mode (in the background).
- Docker will pull the necessary images (`odoo:17` and `postgres:13`) if not available locally, set up the containers, and connect them via the `odoo-network`.

#### Step 5: **Accessing Odoo**

Once the containers are running, you can access Odoo in your browser by navigating to:

```
http://localhost:8071
```

#### Step 6: **Stopping and Removing Containers**

To stop and remove the containers, run the following command:

```bash
docker-compose down
```

To stop all containers without removing them:

```bash
docker-compose stop
```

To remove the containers, networks, and volumes:

```bash
docker-compose down -v
```

---

### 4. **Docker Volumes**

Docker volumes allow you to persist data even if the container is removed or recreated. In the above `docker-compose.yml`, we are using two volumes:
- `odoo-data`: To persist Odoo's data.
- `postgres-data`: To persist PostgreSQL's data.

You can inspect and manage Docker volumes using the following commands:

- **List all volumes**:
  ```bash
  docker volume ls
  ```

- **Inspect a volume**:
  ```bash
  docker volume inspect odoo-data
  ```

- **Remove unused volumes**:
  ```bash
  docker volume prune
  ```

---

### 5. **Docker Networks**

By default, Docker Compose creates a network (`odoo-network` in our case) for the services to communicate. Docker provides several types of networks:
- **Bridge** (default): Isolated network for containers.
- **Host**: The container shares the network stack of the host.
- **Overlay**: Used for multi-host communication (Docker Swarm).

You can inspect networks using:

```bash
docker network inspect odoo-network
```

If you want to remove a network, use:

```bash
docker network rm odoo-network
```

---

### 6. **Docker Best Practices**

- **Use official images**: For production, always use official Docker images (e.g., `odoo:17` and `postgres:13`).
- **Persist data using volumes**: Always use volumes to store persistent data such as database files, media files, and logs.
- **Isolate networks**: Use separate networks for different containers to avoid unnecessary exposure between services.
- **Environment variables**: Use environment variables to pass sensitive data such as database credentials and application configurations.

---

### 7. **Advanced Configuration (Optional)**

- **Custom Configuration (`odoo.conf`)**:
  You can create a custom `odoo.conf` file to modify the configuration of Odoo (e.g., logging, database settings, etc.). You can pass it into the container via volumes.

Example `odoo.conf`:
```ini
[options]
   db_host = odoo_db
   db_port = 5432
   db_user = odoo
   db_password = odoo
   db_name = odoo
   logfile = /var/log/odoo/odoo.log
```

- **Custom Addons**: If you have custom Odoo modules, you can mount them via a volume to `/mnt/extra-addons` in the container:
  ```yaml
  volumes:
    - ./my_addons:/mnt/extra-addons
  ```

---

### Conclusion


---


### **Ref:**

docker-compose.yml

```
version: '3'

services:
  odoo-17:
    image: kgisl:v3
    container_name: odoo
    volumes:
      - odooappdata:/var/lib/odoo
      - ./extra-odoo-addons:/mnt/extra-addons
    depends_on:
      - db
    ports:
      - "8069:8069"
    environment:
      - POSTGRES_USER=odoo
      - POSTGRES_PASSWORD=odoo
      - POSTGRES_DB=postgres
      - PGHOST=db
      - PGUSER=odoo
      - PGPASSWORD=odoo

  db:
    image: postgres:16
    container_name: postgres
    ports:
      - '5434:5432'
    environment:
      - POSTGRES_USER=odoo
      - POSTGRES_PASSWORD=odoo
      - POSTGRES_DB=postgres
    volumes:
      - './odoo-db-dump:/resources/db-dump'
      - 'odoodbdata:/var/lib/postgresql/data'

volumes:
  odooappdata:
  odoodbdata:

```



