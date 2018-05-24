# Building Linux Kernel

    KERNEL=git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git
    git clone $KERNEL

    make O=$OUT $DEFCONFIG

    make O=$OUT modules
    make O=$OUT modules_install INSTALL_MOD_PATH=$KMOD_OUT

# Cross compiling ARM64

    sudo apt install gcc-aarch64-linux-gnu

    export CROSS_COMPILE=aarch64-linux-gnu-
    make zImage dtbs
