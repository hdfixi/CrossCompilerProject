FROM ubuntu:latest
# Install required packages
RUN apt-get update && apt-get install -y \
    build-essential \
    git \
    curl \
    && rm -rf /var/lib/apt/lists/*
# Download and install the "gcc-arm-none-eabi" toolchain
RUN curl -L -o gcc-arm-none-eabi.tar.bz2 https://developer.arm.com/-/media/Files/downloads/gnu-rm/10.3-2021.07/gcc-arm-none-eabi-10.3-2021.07-x86_64-linux.tar.bz2 \
    && tar -xvf gcc-arm-none-eabi.tar.bz2 -C /opt \
    && rm gcc-arm-none-eabi.tar.bz2
ENV PATH="/opt/gcc-arm-none-eabi-10.3-2021.07/bin:${PATH}"