### Complete Docker Management Script

---

```bash
#!/bin/bash

# Function to install Docker and Docker Compose
install() {
    set -e

    echo "Starting Docker installation..."

    # Install Docker Engine
    if ! dpkg -l | grep -q docker.io; then
        echo "Installing Docker..."
        sudo apt update
        sudo apt install -y docker.io
    else
        echo "Docker is already installed."
    fi

    # Start and enable Docker service
    echo "Starting and enabling Docker service..."
    sudo systemctl start docker
    sudo systemctl enable docker

    # Install Docker Compose
    if ! dpkg -l | grep -q docker-compose; then
        echo "Installing Docker Compose..."
        sudo apt install -y docker-compose
    else
        echo "Docker Compose is already installed."
    fi

    # Provide sudo permissions for the current user
    sudo chmod 777 /var/run/docker.sock

    # Verify installation
    echo "Docker version:"
    docker --version
    echo "Docker Compose version:"
    docker-compose --version

    echo "Installation complete!"
}

# Function to build an image
build_image() {
    echo "Enter Dockerfile directory path:"
    read -p "Path: " dir_path
    echo "Enter image name:"
    read -p "Image name: " image_name
    docker build -t "$image_name" "$dir_path"
    echo "Image '$image_name' built successfully."
}

# Function to list and remove Docker images
remove_image() {
    echo "Listing Docker images..."
    docker images --format "table {{.Repository}}\t{{.Tag}}\t{{.ID}}"
    echo "Enter image name or ID to remove:"
    read -p "Image name/ID: " image_name
    docker rmi "$image_name"
    echo "Image '$image_name' removed successfully."
}

# Function to manage containers
container_manage() {
    echo "1. Start a container"
    echo "2. Stop a container"
    echo "3. Remove a container"
    read -p "Choose an option (1-3): " option

    case $option in
        1)
            echo "Enter the container name or ID to start:"
            read -p "Container: " container_name
            docker start "$container_name"
            echo "Container '$container_name' started."
            ;;
        2)
            echo "Enter the container name or ID to stop:"
            read -p "Container: " container_name
            docker stop "$container_name"
            echo "Container '$container_name' stopped."
            ;;
        3)
            echo "Enter the container name or ID to remove:"
            read -p "Container: " container_name
            docker rm "$container_name"
            echo "Container '$container_name' removed."
            ;;
        *)
            echo "Invalid option."
            ;;
    esac
}

# Function to view container logs
view_logs() {
    echo "Fetching running containers..."
    docker ps --format "{{.Names}}"
    read -p "Enter the container name to view logs: " container_name
    if docker ps --format "{{.Names}}" | grep -q "^$container_name$"; then
        echo "Displaying logs for container: $container_name"
        docker logs -f "$container_name"
    else
        echo "Error: Container '$container_name' not found!"
    fi
}

# Function to create Docker volumes
create_volume() {
    echo "Enter volume name:"
    read -p "Volume name: " volume_name
    docker volume create "$volume_name"
    echo "Volume '$volume_name' created successfully."
}

# Function to list and remove Docker volumes
remove_volume() {
    echo "Listing Docker volumes..."
    docker volume ls
    echo "Enter volume name to remove:"
    read -p "Volume name: " volume_name
    docker volume rm "$volume_name"
    echo "Volume '$volume_name' removed successfully."
}

# Function to manage Docker networks
create_network() {
    echo "Enter network name:"
    read -p "Network name: " network_name
    docker network create "$network_name"
    echo "Network '$network_name' created successfully."
}

# Function to list and remove Docker networks
remove_network() {
    echo "Listing Docker networks..."
    docker network ls
    echo "Enter network name to remove:"
    read -p "Network name: " network_name
    docker network rm "$network_name"
    echo "Network '$network_name' removed successfully."
}

# Main menu function
main_menu() {
    echo "Choose an option:"
    echo "1. Install Docker and Docker Compose"
    echo "2. Build a Docker Image"
    echo "3. Manage Docker Containers"
    echo "4. View Container Logs"
    echo "5. Create Docker Volume"
    echo "6. Remove Docker Volume"
    echo "7. Create Docker Network"
    echo "8. Remove Docker Network"
    echo "9. Exit"
    read -p "Enter your choice (1-9): " choice

    case $choice in
        1)
            install
            ;;
        2)
            build_image
            ;;
        3)
            container_manage
            ;;
        4)
            view_logs
            ;;
        5)
            create_volume
            ;;
        6)
            remove_volume
            ;;
        7)
            create_network
            ;;
        8)
            remove_network
            ;;
        9)
            echo "Exiting... Goodbye!"
            exit 0
            ;;
        *)
            echo "Invalid option. Please try again."
            ;;
    esac
}

# Run the main menu in a loop
while true; do
    main_menu
done
```

### Script Breakdown:

1. **Installation (`install`)**:
   - Checks if Docker and Docker Compose are already installed before proceeding with the installation.
   - Starts and enables Docker as a service.
   - Gives necessary user permissions (`chmod 777 /var/run/docker.sock`).

2. **Build Docker Image (`build_image`)**:
   - Prompts the user to enter the directory containing the Dockerfile and the image name.
   - Builds the Docker image using the provided inputs.

3. **Manage Containers (`container_manage`)**:
   - Prompts the user to either start, stop, or remove a container.
   - Based on the user input, it performs the requested action on the specified container.

4. **View Container Logs (`view_logs`)**:
   - Lists running containers and allows the user to view the logs for any selected container.

5. **Create and Remove Volumes (`create_volume`, `remove_volume`)**:
   - Allows the user to create or remove Docker volumes.

6. **Create and Remove Networks (`create_network`, `remove_network`)**:
   - Allows the user to create or remove Docker networks.

7. **Main Menu**:
   - Displays a menu with options to install Docker, build images, manage containers, view logs, and more.
   - Loops continuously, prompting the user to make a choice until they exit.

### How to Use:

1. **Save and Execute**: Save the script as `docker_manager.sh` and make it executable:
   ```bash
   chmod +x docker_manager.sh
   ./docker_manager.sh
   ```

2. **Interact with the Menu**:
   - Choose an option from the menu to either install Docker, manage containers, build images, create volumes, etc.
   - Follow the prompts for additional information (like container names or volume names) when required.

### Features Covered:
- **Docker Installation**: Automated installation of Docker and Docker Compose.
- **Container Management**: Start, stop, and remove containers.
- **Image Management**: Build and remove Docker images.
- **Volume & Network Management**: Create and remove Docker volumes and networks.
- **Log Viewing**: View logs of running containers.
