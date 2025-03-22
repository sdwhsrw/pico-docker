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
RUN apt install -y \
    pkg-config \
    libusb-1.0-0-dev

WORKDIR /root/pico
RUN git clone https://github.com/raspberrypi/pico-sdk.git
RUN cd pico-sdk && \
    git submodule update --init --recursive
ENV PICO_SDK_PATH="/root/pico/pico-sdk"

WORKDIR /root/pico
RUN git clone https://github.com/raspberrypi/picotool.git
RUN cd picotool && \
    mkdir build && \
    cd build && \
    cmake .. && \
    make install
WORKDIR /root/pico/picotool
RUN mkdir -p /etc/udev/rules.d
RUN cp udev/99-picotool.rules /etc/udev/rules.d/

WORKDIR /root/pico/
RUN cp /root/pico/pico-sdk/external/pico_sdk_import.cmake .