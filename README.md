# ROS2 Humble Dev Container Template

This repository serves as a template for ROS2 projects. It includes a Dockerfile and a Dev Container configuration to help you and your team develop ROS2 projects in a consistent environment.

## Prerequisites

- Docker
- Visual Studio Code
- Remote - Containers extension for VS Code

## How to Use

1. **Clone the Repository**: Clone this template repository and navigate into it.
    ```bash
    git clone https://github.com/Santos-Enoque/ros_template.git
    cd ros-template
    ```

2. **Open in VS Code**: Open the folder in Visual Studio Code.

3. **Start Dev Container**: When prompted, reopen the folder in a Dev Container. This will build the Docker image and start a new container. You can also manually start it by clicking on the green "Open a Remote Window" button in the bottom-left corner and selecting "Reopen in Container".

4. **Wait for Build to Complete**: The first build may take some time as it installs all the necessary dependencies.

## Features

### Display Forwarding

The Dev Container is configured to forward the display from the container to your local machine. This is useful for running graphical ROS2 such as gazebo and rviz applications from within the container.

### Pre-installed Extensions

The Dev Container comes with several useful VS Code extensions pre-installed, including:

- C/C++ IntelliSense
- CMake Tools
- Error Lens
- GitHub Copilot
- Prettier
- XML Tools
- YAML
- ROS

### Custom tmux Configuration

A custom tmux configuration is included for easier terminal multiplexing.

## Environment Variables

- `ROS_DISTRO`: Set to `humble` by default.
- `PROJECT_NAME`: Automatically set to the name of the folder you opened in VS Code.

> To not forget to set the `Dockerfile` base image in accordance with the `ROS_DISTRO`

## Troubleshooting

### Display Forwarding Issues

If you encounter issues with display forwarding, ensure that your local machine's display server is accessible and that you have the necessary permissions.

For Linux:

```bash
xhost +local:
