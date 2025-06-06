FROM ubuntu:latest

# Set non-interactive mode for installations
ENV DEBIAN_FRONTEND=noninteractive

# Install apt dependencies
RUN apt-get update
# Flutter dependencies
RUN apt-get install -y curl git unzip xz-utils zip libglu1-mesa
# Saber dependencies
RUN apt-get install -y libgtk-3-dev libx11-dev pkg-config cmake ninja-build libblkid-dev libsecret-1-dev libjsoncpp-dev ghostscript libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libunwind-dev webkit2gtk-4.1-dev
RUN apt-get clean

# Install Flutter
RUN git clone https://github.com/flutter/flutter.git /opt/flutter --branch stable
ENV PUB_CACHE=/root/.pub-cache
RUN mkdir -p /root/.pub-cache/bin/
ENV PATH="/opt/flutter/bin:/root/.pub-cache/bin:$PATH"
RUN flutter precache --no-universal --linux
RUN flutter doctor

# Install rustup
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
ENV PATH="/root/.cargo/bin:$PATH"
RUN rustup --version

WORKDIR /app

# Default command: open a shell
CMD ["/bin/bash"]
