FROM osrf/ros:humble-desktop-full


# Add vscode user with same UID and GID as your host system
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Switch from root to user
USER $USERNAME

# Add user to video group to allow access to webcam
RUN sudo usermod --append --groups video $USERNAME

# Install dependencies
RUN sudo apt update && \
    sudo apt upgrade -y && \
    sudo apt install -y build-essential git tmux ros-dev-tools \
    ros-${ROS_DISTRO}-ros2-control \
    ros-${ROS_DISTRO}-ros2-controllers \
    ros-${ROS_DISTRO}-xacro \
    ros-${ROS_DISTRO}-gazebo-ros2-control \
    ros-${ROS_DISTRO}-joint-state-publisher-gui \
    ros-${ROS_DISTRO}-urdf-tutorial  \
    ros-${ROS_DISTRO}-gazebo-ros-pkgs


# Source the ROS setup file
RUN echo "source /opt/ros/${ROS_DISTRO}/setup.bash" >> ~/.bashrc
# Source workspace setup file
ARG WORKSPACE_NAME=ros2_autonomous_robot 
# Source workspace setup file
RUN echo "source /${WORKSPACE_NAME}/install/setup.bash" >> ~/.bashrc
# Setup colcon
RUN echo "source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash" >> ~/.bashrc

# Add tmux configuration
RUN echo "set -g base-index 1\n\
    set -g pane-base-index 1\n\
    set -g status-style bg=default\n\
    bind H resize-pane -L 5\n\
    bind J resize-pane -D 5\n\
    bind K resize-pane -U 5\n\
    bind L resize-pane -R 5\n\
    bind h select-pane -L\n\
    bind l select-pane -R\n\
    bind k select-pane -U\n\
    bind j select-pane -D" >> ~/.tmux.conf
