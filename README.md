MTA Coin on Containers
Objective

The goal of this project is to practice Inter-Process Communication (IPC) within a container-based development environment. The system simulates a blockchain mining process by running server and miner applications in separate Docker containers that communicate via named pipes.
Overview

The application involves two key components, each running in its own container:

    Server Container: Manages miner subscriptions, sends current block information, and validates new blocks.
    Miner Containers: Each miner container subscribes to the server, receives the current block, mines a new one, and sends it back to the server for validation.

Key Features

    Server container manages subscriptions and validates new blocks mined by the miners.
    Miners communicate with the server using named pipes.
    A configuration file for server difficulty is automatically generated.
    The system can dynamically scale the number of miners based on user input.

How to Launch the System

To run the entire system, you only need to execute the provided launcher.sh script, which simplifies the setup. The script requires two input parameters:

    Difficulty level for the mining process.
    Number of miner containers to launch.

Running the Script

    Prepare the launcher script:
    Before running the launcher script, you must make it executable by using the following command:
    chmod +x launcher.sh.

    Execute the launcher script with the two parameters (difficulty level and number of miners):
    Example command:
    ./launcher.sh <difficulty> <number_of_miners>.
    For example, if you want to set a difficulty level of 5 and launch 3 miner containers, run:
    ./launcher.sh 5 3.

Script Details

    The script will pull the necessary Docker images from Docker Hub. Make sure you are logged in to Docker Hub before running the script.
    Sudo permissions are required to run the Docker commands, so the script must be executed with sudo rights.
    The script automatically creates a mounted directory (mnt/mta/) where the configuration file and pipes are stored.
    The configuration file (mtacoin.conf) is generated in the mounted directory. This file stores essential system settings, including the difficulty level and miner IDs.
    If you run the script multiple times, it will clean up any existing named pipes from previous runs and update the configuration file with new parameters, such as the difficulty level and the number of miners.

Docker Image Information

The launcher script pulls the following Docker images from Docker Hub:

    Server Image: nadir0702/mtacoin_ex3:mtacoin-server
    Miner Image: nadir0702/mtacoin_ex3:mtacoin-miner

Example Usage

Suppose you want to launch the system with a difficulty level of 3 and 2 miners. Simply run:
./launcher.sh 3 2.

The script will handle the following:

    Pull the Docker images.
    Create the necessary directory and configuration file.
    Remove old pipes and update settings for new runs.
    Launch the server container and the specified number of miner containers.

Important Notes

    Always ensure that you are logged into Docker Hub before running the script, as it will pull the required images from Docker Hub.
    The script removes old named pipes from previous runs and updates the configuration file for each new execution.
    Once launched, the containers will start communicating via named pipes located in the mounted directory.
    The server must always be up before the miner containers are launched. The script handles this automatically by launching the server first and then waiting a short time before starting the miners.
