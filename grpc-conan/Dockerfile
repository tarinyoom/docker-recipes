FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    python3-pip \
    git \
    cmake \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

RUN pip3 install conan

RUN conan profile detect --force

WORKDIR /workspace

# Install conan dependencies
COPY conanfile.txt ./
RUN conan install . --output-folder=build --build=missing

WORKDIR /workspace/build
