FROM ubuntu:18.04
ARG DEBIAN_FRONTEND="noninteractive"

USER root

RUN apt-get update
RUN apt-get install -y --no-install-recommends apt-utils

RUN apt-get install -y sudo

# Add docker as new user
RUN useradd -s /bin/bash -d /home/docker -m -G sudo docker

# Give our user sudo privileges without a password
RUN usermod -aG sudo docker
RUN passwd -d docker
RUN echo "docker    ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Install development packages
RUN apt-get install -y gdb \
                        python3 \
                        python3-pip \
                        python3-venv \
                        cmake \
    && apt-get autoremove -y \
    && apt-get clean

# Install conan
RUN python3 -m pip install --upgrade pip
RUN python3 -m pip install conan

USER docker
