[!WARNING]
### ★★★ WARNING ★★★
Untested firmware.
Email emil.cs07@gmail.com with your test results.


I am uploading the raw source code and the compiled version of the source code in here.
Use Ubuntu 16.04 for compiling this code.
All proprietary code is property of Cisco Systems, Inc. provided by their external-opensource-requests@cisco.com team.
Based on the source code of Release 1.0.03.26 for RV34X based routers.
Support for Cisco RV340W only.

```
FROM ubuntu:16.04

# Prevent interactive prompts
ENV DEBIAN_FRONTEND=noninteractive

# Install the build dependencies for OpenWrt 15.05
RUN apt-get update && apt-get install -y \
    build-essential \
    gcc \
    g++ \
    binutils \
    patch \
    bzip2 \
    flex \
    bison \
    make \
    autoconf \
    automake \
    libtool \
    gettext \
    texinfo \
    unzip \
    wget \
    xz-utils \
    libncurses5-dev \
    zlib1g-dev \
    git \
    subversion \
    libssl-dev \
    gawk \
    python \
    curl \
    file \
    diffutils \
    sudo \
    && rm -rf /var/lib/apt/lists/*

# Ignore SSL errors for any old feeds
RUN git config --global http.sslVerify false

# Create a non-root user (OpenWrt refuses to build as root)
RUN useradd -m -s /bin/bash builder && \
    echo "builder ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

USER builder
WORKDIR /work
```
