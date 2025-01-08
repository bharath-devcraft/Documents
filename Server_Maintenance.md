### **Server maintenance**

```markdown
# Server Maintenance Commands

## Crontab Management
- Edit crontab (schedule tasks):
  ```bash
  crontab -e
  ```
- List crontab entries:
  ```bash
  crontab -l
  ```

## Process Monitoring
- Check running processes:
  ```bash
  top
  ```
  - Use `1+c` to display the latest processes.

## Log Monitoring
- Check system logs while scheduler is running (live):
  ```bash
  sudo tail -f /var/log/syslog
  ```
- Check the last 500 lines of the system log:
  ```bash
  sudo tail -500 /var/log/syslog
  ```

## File Permissions
- Check file permissions:
  ```bash
  ls -lh <file_name>
  ```
- Check permissions of all files in the current directory:
  ```bash
  ll
  ```

## File Searching and Deletion
- Find `.jasper` files:
  ```bash
  find . -type f -name "*.jasper"
  ```
- Find and delete `.jasper` files:
  ```bash
  find . -type f -name "*.jasper" -print0 | xargs -0 rm
  ```

## Disk Usage
- Check the size of a specific file:
  ```bash
  du -h <filename>
  ```

## System Resource Usage
- Monitor CPU and memory usage in a more detailed manner:
  ```bash
  htop
  ```
- Check disk space usage:
  ```bash
  df -h
  ```

## Networking
- Check open network ports and connections:
  ```bash
  netstat -tuln
  ```
- Check listening ports:
  ```bash
  sudo lsof -i -P -n | grep LISTEN
  ```

## Service Management
- Start a service:
  ```bash
  sudo systemctl start <service_name>
  ```
- Stop a service:
  ```bash
  sudo systemctl stop <service_name>
  ```
- Check the status of a service:
  ```bash
  sudo systemctl status <service_name>
  ```

## Disk and File System Management
- Check disk usage by directory:
  ```bash
  du -sh *
  ```
- Check disk partitions:
  ```bash
  sudo fdisk -l
  ```

## System Information
- Get detailed system information:
  ```bash
  uname -a
  ```
- Get hardware information:
  ```bash
  lscpu
  ```

## Package Management (Debian/Ubuntu)
- Update all packages:
  ```bash
  sudo apt update && sudo apt upgrade -y
  ```
- Install a package:
  ```bash
  sudo apt install <package_name>
  ```
- Remove a package:
  ```bash
  sudo apt remove <package_name>
  ```

## User Management
- Add a new user:
  ```bash
  sudo adduser <username>
  ```
- Delete a user:
  ```bash
  sudo deluser <username>
  ```
- Add a user to a group:
  ```bash
  sudo usermod -aG <group_name> <username>
  ```

## Docker Management
- List running Docker containers:
  ```bash
  docker ps
  ```
- Stop a running Docker container:
  ```bash
  docker stop <container_id>
  ```
- Remove a Docker container:
  ```bash
  docker rm <container_id>
  ```
- List Docker images:
  ```bash
  docker images
  ```
- Remove a Docker image:
  ```bash
  docker rmi <image_id>
  ```

## System Shutdown/Restart
- Shutdown the system:
  ```bash
  sudo shutdown -h now
  ```
- Restart the system:
  ```bash
  sudo reboot
  ```

## File Transfer (SCP)
- Transfer files from local to remote server:
  ```bash
  scp <file_path> <user>@<host>:<destination_path>
  ```
- Transfer files from remote to local server:
  ```bash
  scp <user>@<host>:<file_path> <destination_path>
  ```
```
