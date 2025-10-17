# Use the official ROS Jazzy image as base
FROM osrf/ros:jazzy-desktop-full

# Set environment variables for GPU access
ENV NVIDIA_VISIBLE_DEVICES=all
ENV NVIDIA_DRIVER_CAPABILITIES=all

# Set environment variables for X11 forwarding
ENV DISPLAY=:0
ENV WAYLAND_DISPLAY=wayland-0
ENV QT_X11_NO_MITSHM=1

# Install zsh first and then set it as the default shell
RUN apt-get update && apt-get install -y \
    zsh \
    zoxide \
    python3-virtualenvwrapper \
    git \
    curl \
    iputils-ping \
    net-tools \
    wl-clipboard \
    && rm -rf /var/lib/apt/lists/*

# Set the default shell to zsh
SHELL ["/bin/zsh", "-c"]

# Set the working directory to root's home
WORKDIR /root

# Set the container's home to the host's home directory
ENV HOME /host_home

# Create a directory for the home volume and mount the host's home directory
VOLUME ["/host_home"]

# Set the entrypoint to start a shell by default
CMD ["zsh"]

