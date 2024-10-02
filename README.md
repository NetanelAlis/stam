# MTA Coin on Containers

## Objective
This project focuses on practicing Inter-Process Communication (IPC) in a container-based development environment. The system includes a server and multiple miner containers, which communicate through named pipes, to simulate a blockchain mining process.

## Overview
The application includes two Docker containers:
1. **Server Container:** Manages miner subscriptions and validates new blocks.
2. **Miner Containers:** Subscribe to the server, receive the current block, mine, and send new blocks to the server.

### Key Features:
- The server manages subscriptions and block validation.
- Miners use named pipes to communicate with the server.
- Configuration file for server difficulty is generated automatically by the script.
- The system supports dynamic scaling of miners based on input parameters.

## Getting Started

### Prerequisites
Ensure the following tools are installed:
- Docker
- Bash shell
- Sudo privileges

### Running the Application
To launch the system, follow these steps:

1. **Make the launcher script executable:**
   ```bash
   chmod +x launcher.sh

2. **Run the launcher.sh script with two parameters**:

    difficulty level (e.g., 5)
    number of miners (e.g., 3)
   
Example:

If you want to run the system with a difficulty level of 5 and 3 miners, the command would be:

```bash
   ./launcher.sh 5 3
```
   
**Script Behavior**

   - The script will pull the Docker images from Docker Hub. Ensure you're logged into Docker Hub before running the script.
   - The script requires sudo permissions to run Docker commands.
   - A mounted directory (mnt/mta/) will be created in the current working directory to store pipes and the configuration file.
   - The configuration file (mtacoin.conf) is generated automatically and contains the difficulty level and the miner IDs.
   - The script removes old named pipes and updates the configuration file with new parameters each time it runs.

