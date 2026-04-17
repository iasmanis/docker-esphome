# Use Python 3.11 as base image
FROM python:3.11-bullseye

# Avoid warnings by switching to noninteractive
ENV DEBIAN_FRONTEND=noninteractive

# Install system dependencies required for ESPHome
RUN apt-get update && apt-get install -y \
    git \
    curl \
    wget \
    build-essential \
    gcc \
    g++ \
    cmake \
    ninja-build \
    python3-dev \
    python3-pip \
    python3-setuptools \
    python3-wheel \
    libffi-dev \
    libssl-dev \
    libtool \
    autoconf \
    pkg-config \
    clang-format \
    # Additional tools
    sudo \
    vim \
    nano \
    && rm -rf /var/lib/apt/lists/*

# Create a non-root user
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Install PlatformIO Core
RUN pip3 install --no-cache-dir platformio

# Install ESPHome
# RUN pip3 install --no-cache-dir esphome
RUN pip3 install --no-cache-dir "esphome==2026.4.0"

# Install additional Python tools for development
RUN pip3 install --no-cache-dir \
    pylint \
    black \
    pytest

# Switch back to dialog for any ad-hoc use of apt-get
ENV DEBIAN_FRONTEND=dialog

# Set the default user
USER $USERNAME

# Set working directory
WORKDIR /workspace
