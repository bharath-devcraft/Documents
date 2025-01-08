### **Linux Commands**
---
```markdown

## Terminal Customization
- **Enable a colourful terminal** (using Zsh):
  ```bash
  zsh
  ```

## Process and System Monitoring
- **View system resource usage (CPU, memory, disk)**:
  ```bash
  htop
  ```
- **View all running processes**:
  ```bash
  ps aux
  ```
- **Check system uptime**:
  ```bash
  uptime
  ```
- **Check system load average**:
  ```bash
  top
  ```
- **Check the status of all services**:
  ```bash
  systemctl status
  ```

## File Permissions and Ownership
- **Change file permissions**:
  ```bash
  chmod <permissions> <file_name>
  ```
- **Change file ownership**:
  ```bash
  sudo chown <owner>:<group> <file_name>
  ```
- **Change file permissions recursively**:
  ```bash
  chmod -R <permissions> <directory_name>
  ```

## File Management
- **Create a new file**:
  ```bash
  touch <file_name>
  ```
- **Move or rename a file**:
  ```bash
  mv <source> <destination>
  ```
- **Delete a file**:
  ```bash
  rm <file_name>
  ```
- **Copy a file**:
  ```bash
  cp <source> <destination>
  ```

## Disk and Memory Usage
- **Check disk usage**:
  ```bash
  df -h
  ```
- **Check disk space usage of a directory**:
  ```bash
  du -sh <directory_name>
  ```
- **Check memory usage**:
  ```bash
  free -h
  ```

## Networking and Ports
- **Check active network connections**:
  ```bash
  netstat -tuln
  ```
- **Check listening ports**:
  ```bash
  sudo lsof -i -P -n | grep LISTEN
  ```
- **Check open ports with nmap**:
  ```bash
  nmap -p- <host>
  ```
- **Test connection to a host (ping)**:
  ```bash
  ping <hostname or IP>
  ```
- **Trace route to a host**:
  ```bash
  traceroute <hostname or IP>
  ```
- **Check available network interfaces**:
  ```bash
  ifconfig
  ```

## File Searching and Management
- **Find files by name**:
  ```bash
  find /path/to/directory -type f -name "filename"
  ```
- **Find files by type**:
  ```bash
  find /path/to/directory -type d -name "directory_name"
  ```
- **Search for a pattern in a file**:
  ```bash
  grep "pattern" <file_name>
  ```
- **Find files and delete them**:
  ```bash
  find /path/to/directory -type f -name "*.log" -exec rm -f {} \;
  ```

## Archiving and Compression
- **Create a tar.gz archive**:
  ```bash
  tar -czvf archive_name.tar.gz <file_or_directory>
  ```
- **Extract a tar.gz archive**:
  ```bash
  tar -xzvf archive_name.tar.gz
  ```
- **Zip a file or directory**:
  ```bash
  zip -r archive_name.zip <file_or_directory>
  ```
- **Unzip a file**:
  ```bash
  unzip archive_name.zip
  ```

## Process Management
- **Kill a process by PID**:
  ```bash
  kill <PID>
  ```
- **Kill a process by name**:
  ```bash
  pkill <process_name>
  ```
- **Find a process by name**:
  ```bash
  ps aux | grep <process_name>
  ```

## System Shutdown and Reboot
- **Shutdown the system**:
  ```bash
  sudo shutdown now
  ```
- **Reboot the system**:
  ```bash
  sudo reboot
  ```
- **Power off the system**:
  ```bash
  sudo poweroff
  ```

## Cron Jobs and Scheduling
- **Edit cron jobs**:
  ```bash
  crontab -e
  ```
- **List cron jobs**:
  ```bash
  crontab -l
  ```
- **Schedule a job to run every 5 minutes**:
  ```bash
  */5 * * * * <command>
  ```

## Security and File Integrity
- **Check file permissions**:
  ```bash
  ls -l <file_name>
  ```
- **Change permissions of a directory recursively**:
  ```bash
  chmod -R 755 <directory_name>
  ```
- **Check for broken symbolic links**:
  ```bash
  find -L /path/to/directory -type l
  ```

## Miscellaneous Useful Commands
- **List all environment variables**:
  ```bash
  printenv
  ```
- **Check the last system logins**:
  ```bash
  last
  ```
- **Check disk usage in human-readable format**:
  ```bash
  df -h
  ```
- **Get the current system date and time**:
  ```bash
  date
  ```

## System Resource Allocation
- **View system limits (max number of open files, processes, etc.)**:
  ```bash
  ulimit -a
  ```
- **Set system limits for a user**:
  ```bash
  sudo ulimit -n 10000
  ```

---
