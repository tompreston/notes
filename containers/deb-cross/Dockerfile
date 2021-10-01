# Debian container with cross-compilers installed.
#
# For example, to cross compile a kernel:
#
#     https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git
#     export CROSS_COMPILE=aarch64-linux-gnu- ARCH=arm64
#     make defconfig
#     make
#
FROM debian:stable
RUN export DEBIAN_FRONTEND=noninteractive; \
    apt-get update && \
    apt-get install -y \
        autoconf \
        bc \
        bison \
        build-essential \
        crossbuild-essential-arm64 \
        curl \
        dkms \
        flex \
        gawk \
        git \
        libelf-dev \
        libiberty-dev \
        libncurses-dev \
        libpci-dev \
        libssl-dev \
        libudev-dev \
        ncurses-dev \
        openssh-client \
        openssl \
        python3 \
        python3-dev \
        python3-pip \
        python3-setuptools
RUN python3 -m pip install --upgrade pip
RUN sed -i -e 's/ main/ main source/' /etc/apt/sources.list
RUN apt-get update && apt-get build-dep linux linux-image-$(uname -r)
