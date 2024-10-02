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
