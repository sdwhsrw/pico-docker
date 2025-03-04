FROM ubuntu:latest

RUN apt update && apt upgrade -y
RUN apt install -y \
    cmake \
    python3 \
    build-essential \
    gcc-arm-none-eabi \
    libnewlib-arm-none-eabi \
    libstdc++-arm-none-eabi-newlib \
    git

WORKDIR /root/pico
RUN git clone https://github.com/raspberrypi/pico-sdk.git

WORKDIR pico-sdk
RUN git submodule update --init --recursive

WORKDIR /workspace
RUN cp /root/pico/pico-sdk/external/pico_sdk_import.cmake .