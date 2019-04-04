# Linux Kernel
References:
- http://www.kroah.com/lkn/
- https://lwn.net/Kernel/LDD3/

# Dependencies

    sudo apt install \
        buildessentials
        libelf-dev
        libssl-dev
        lzop
        moreutils

# Building Linux Kernel
Download:

    kernel=git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git
    git clone $kernel
    cd $kernel
    make help

Configure:

    make defconfig
    make menuconfig

Build:

    make

# Cross compiling ARM64
Get dependencies:

    sudo apt install gcc-aarch64-linux-gnu

    export CROSS_COMPILE=aarch64-linux-gnu-
    export ARCH=arm64
    make
