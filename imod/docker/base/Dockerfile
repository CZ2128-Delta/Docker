ARG UBUNTU_VERTION=20.04
ARG CUDA_VERSION=11.7.10
ARG IMAGE_DIGEST=2841c6138039d5514157735db1d21515a5f35332149c07478e0c10269fc97e0d

# regarding to https://hub.docker.com/r/nvidia/cuda/tags?page=1&name=11.7.1-base
FROM nvidia/cuda:${CUDA_VERSION}-base-ubuntu${UBUNTU_VERTION}@sha256:${IMAGE_DIGEST}

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
        build-essential \
        curl \
        git \
        openjdk-8-jdk-headless \
        libtool \
        ca-certificates \
        ninja-build \
        python3-dev \
        python3-distutils \
        python3-pip \
        nginx \
        wget\
        jq \
        libatlas-base-dev \
        unzip \
        vim \
        ffmpeg \
        libsm6 \
        libxext6 \
        libglu1-mesa \
        && \
    rm -rf /var/lib/apt/lists/*

RUN ln -sf /usr/bin/python3 /usr/bin/python
COPY imod_4.12.21_RHEL7-64_CUDA10.1.sh /mnt

WORKDIR /mnt
RUN sh imod_4.12.21_RHEL7-64_CUDA10.1.sh -y

RUN echo 'export IMOD_DIR="/usr/local/IMOD"' >> ~/.bashrc
RUN echo 'if [ -e $IMOD_DIR/IMOD-linux.sh ] ; then source $IMOD_DIR/IMOD-linux.sh ; fi' >> ~/.bashrc
