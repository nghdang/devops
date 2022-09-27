FROM ngoalong911/devenv-base:1
ARG DEBIAN_FRONTEND="noninteractive"

USER root

RUN apt-get install -y --no-install-recommends apt-utils

# Install sudo
RUN apt-get install -y sudo

# Add docker as new user
RUN useradd -s /bin/bash -d /home/docker -m -G sudo docker

# Give our user sudo privileges without a password
RUN usermod -aG sudo docker
RUN passwd -d docker
RUN echo "docker    ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

USER docker
