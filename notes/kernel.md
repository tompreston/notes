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

# Building out of treee modules
Sometimes you have a kernel module which is out-of-tree. It can be built using
the M= argument:

    cd kernel
    make M=../out_of_tree_module

Although sometimes, the out-of-tree module comes with its own Makefile. For
example, the Intel i210 Ethernet controller driver `igb_avb`. In this case,
we just point to the kernel using KSRC and tell make to change-directory first:

    git clone https://github.com/AVnu/igb_avb.git
    cd kernel
    KSRC=$PWD make -C ../igb_avb/kmod
