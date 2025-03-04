# Start from an official ROS Humble desktop image (Ubuntu 22.04)
FROM ros:humble-desktop

# Prevent any interactive prompts during build
ENV DEBIAN_FRONTEND=noninteractive

# Install tmux, nano, colcon tools, rosdep, and Gazebo extras if needed
RUN apt-get update && apt-get install -y \
    tmux nano python3-colcon-common-extensions python3-rosdep \
    ros-humble-gazebo-ros-pkgs ros-humble-gazebo-plugins ros-humble-gazebo-ros-control \
    liboctomap-dev \
    && rm -rf /var/lib/apt/lists/*

# Initialize rosdep (ignore errors if already initialized)
RUN rosdep init || true
RUN rosdep update

# Create a workspace in /root/ws (src will be mounted by devcontainer.json)
WORKDIR /root/ws
RUN mkdir -p src

# Default shell command on container start
CMD ["/bin/bash"]
