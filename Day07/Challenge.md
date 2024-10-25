# Challenge Day 07: 

---

### Current Status
- **Day Completed**: 7
- **Total Days in Challenge**: 90

Join #TrainWithShubham Community on an exhilarating journey of learning and growth as we embark on the #90DaysofChallenge!

---
# Day 07: Understanding Package Manager and Systemctl

### Overview
In this challenge, we will learn about package managers in Linux and how to manage services using `systemctl`. You will install important software tools, understand their dependencies, and practice service management.

### What is a Package Manager in Linux?
A package manager is a tool that allows users to install, remove, upgrade, configure, and manage software packages on an operating system. It can be a graphical application or a command-line tool, such as `apt-get` for Debian-based systems or `yum` for Red Hat-based systems.

### What is a Package?
A package is essentially an archive file that contains the binary executable, configuration files, and sometimes information about dependencies. Packages can be GUI applications, command-line tools, or software libraries needed by other programs.

### Different Kinds of Package Managers
There are various package managers based on different packaging systems:
- **RPM**: Uses `yum` and `dnf` package managers.
- **DEB**: Uses `apt-get` and `aptitude`.

### Tasks

### Understanding Systemd and Systemctl

#### What is Systemd?
`systemd` is a system and service manager for Linux operating systems. It is responsible for initializing the system, managing services, and handling system resources. `systemd` has replaced older init systems in many distributions due to its efficiency and ability to parallelize service startup, making boot processes faster.

#### What is Systemctl?
`systemctl` is the command-line tool used to interact with `systemd`. It allows users to manage services, check their status, enable or disable them, and perform various administrative tasks related to service management.

#### Commonly Used Systemctl Commands
Here are some essential `systemctl` commands along with explanations:

1. **Check Status of a Service**:
   ```bash
   sudo systemctl status <service_name>
   ```
   - **Example**: `sudo systemctl status docker`
   - **Explanation**: Displays the current status of the specified service (e.g., whether it is active, inactive, or failed).

2. **Start a Service**:
   ```bash
   sudo systemctl start <service_name>
   ```
   - **Example**: `sudo systemctl start jenkins`
   - **Explanation**: Starts the specified service immediately.

3. **Stop a Service**:
   ```bash
   sudo systemctl stop <service_name>
   ```
   - **Example**: `sudo systemctl stop jenkins`
   - **Explanation**: Stops the specified service.

4. **Restart a Service**:
   ```bash
   sudo systemctl restart <service_name>
   ```
   - **Example**: `sudo systemctl restart docker`
   - **Explanation**: Stops and then starts the specified service again.

5. **Enable a Service to Start on Boot**:
   ```bash
   sudo systemctl enable <service_name>
   ```
   - **Example**: `sudo systemctl enable docker`
   - **Explanation**: Configures the specified service to start automatically at boot time.

6. **Disable a Service from Starting on Boot**:
   ```bash
   sudo systemctl disable <service_name>
   ```
   - **Example**: `sudo systemctl disable jenkins`
   - **Explanation**: Prevents the specified service from starting automatically at boot time.

7. **List All Services**:
   ```bash
   systemctl list-units --type=service
   ```
   - **Explanation**: Lists all services, showing their current status (active, inactive, etc.).

---

## Understanding Journalctl

### What is Journalctl?
`journalctl` is a command-line utility that allows users to query and display messages from the journal, which is a component of `systemd` that collects and stores logs for services and the system. This logging mechanism provides a more structured and robust way of logging compared to traditional syslog.

### Commonly Used Journalctl Commands
Here are essential `journalctl` commands with explanations:

1. **View Logs for a Specific Service**:
   ```bash
   journalctl -u <service_name>
   ```
   - **Example**: `journalctl -u docker`
   - **Explanation**: Displays logs for the specified service. Useful for troubleshooting service issues.

2. **View All Logs**:
   ```bash
   journalctl
   ```
   - **Explanation**: Displays all logs collected by the journal.

3. **View Logs in Real-Time**:
   ```bash
   journalctl -f
   ```
   - **Explanation**: Follows the log output in real-time, similar to `tail -f`.

4. **View Logs Since a Specific Time**:
   ```bash
   journalctl --since "YYYY-MM-DD HH:MM:SS"
   ```
   - **Example**: `journalctl --since "2024-10-01 12:00:00"`
   - **Explanation**: Displays logs since the specified date and time.

5. **Filter Logs by Priority Level**:
   ```bash
   journalctl -p <priority_level>
   ```
   - **Example**: `journalctl -p err`
   - **Explanation**: Displays logs filtered by priority level (e.g., `err`, `warning`, `info`, etc.).

6. **Clear Journal Logs**:
   ```bash
   sudo journalctl --vacuum-time=2weeks
   ```
   - **Explanation**: Removes journal logs older than the specified time (e.g., 2 weeks).

---

## Putting It All Together

### Example Usage Scenario
Let's combine these commands in a typical usage scenario where you might be managing Docker and Jenkins:

1. **Install Docker and Jenkins**:
   Use the package manager (like `apt` for Debian-based systems) to install Docker and Jenkins.

2. **Check Service Status**:
   After installation, check if the services are running:
   ```bash
   sudo systemctl status docker
   sudo systemctl status jenkins
   ```

3. **Start the Services**:
   If they are not running, start them:
   ```bash
   sudo systemctl start docker
   sudo systemctl start jenkins
   ```

4. **Enable Services to Start on Boot**:
   Enable them to start automatically at boot:
   ```bash
   sudo systemctl enable docker
   sudo systemctl enable jenkins
   ```

5. **Check Logs for Troubleshooting**:
   If there are issues, view logs for each service:
   ```bash
   journalctl -u docker
   journalctl -u jenkins
   ```

6. **View All Logs**:
   If you need to investigate system-wide issues, check all logs:
   ```bash
   journalctl
   ```

7. **Real-Time Monitoring**:
   To watch logs as they happen:
   ```bash
   journalctl -f
   ```

---

### Shell Script for Installation
You can use the following shell script to automate the installation of Docker and Jenkins based on provided arguments:

```bash
#!/bin/bash

# Check if at least one argument is provided
if [ "$#" -lt 1 ]; then
    echo "Usage: $0 <software1> <software2>"
    exit 1
fi

# Update and Upgrade the system
echo "Updating and upgrading the system..."
sudo apt update && sudo apt upgrade -y

# Function to install Docker
install_docker() {
    echo "Installing Docker..."
    sudo apt install -y docker.io
    sudo systemctl start docker
    sudo systemctl enable docker
    echo "Docker installation completed."
}

# Function to install Jenkins
install_jenkins() {
    echo "Installing Jenkins..."
    sudo apt install -y openjdk-11-jdk
    wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
    echo deb http://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list
    sudo apt update
    sudo apt install -y jenkins
    sudo systemctl start jenkins
    sudo systemctl enable jenkins
    echo "Jenkins installation completed."
}

# Loop through the arguments and install the requested software
for software in "$@"; do
    case $software in
        docker)
            install_docker
            ;;
        jenkins)
            install_jenkins
            ;;
        *)
            echo "Unknown software: $software. Please use 'docker' or 'jenkins'."
            ;;
    esac
done
```

### Shell Script for Automating Service Management
Below is a sample script that automates the starting and stopping of Docker and Jenkins services:

```bash
#!/bin/bash

# Function to start services
start_services() {
    echo "Starting Docker and Jenkins services..."
    sudo systemctl start docker
    sudo systemctl start jenkins
    echo "Docker and Jenkins services started."
}

# Function to stop services
stop_services() {
    echo "Stopping Docker and Jenkins services..."
    sudo systemctl stop docker
    sudo systemctl stop jenkins
    echo "Docker and Jenkins services stopped."
}

# Main script execution
if [ "$1" == "start" ]; then
    start_services
elif [ "$1" == "stop" ]; then
    stop_services
else
    echo "Usage: $0 {start|stop}"
    exit 1
fi
```
