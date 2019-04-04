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
    make menuconfig # menuconfig operated on .config

Build:

    make


# Saving config
Sometimes you want to change config options using menuconfig, then track them
using git. Don't just `cp .config arch/$ARCH/configs/mydefconfig` use
savedefconfig:

    make defconfig     # create .config
    make menuconfig    # edit .config
    make savedefconfig # use kbuild to generate defconfig
    mv defconfig arch/x86/configs/tpreston-defconfig
    git add arch/x86/configs/tpreston-defconfig

# Cross compiling ARM64
Get dependencies:

    sudo apt install gcc-aarch64-linux-gnu

    export CROSS_COMPILE=aarch64-linux-gnu-
    export ARCH=arm64

    make defconfig  # arch/arm64/configs/defconfig -> .config
    make
