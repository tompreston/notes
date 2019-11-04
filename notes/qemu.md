# QEMU
You can use qemu-system to test a kernel:

    qemu-system-arm -M virt -m 128M -nographic -kernel arch/arm/boot/zImage

You can use qemu-user to test userspace binaries (give it a sysroot for dynamic
libraries):

    qemu-aarch64 -L toolchain/linarogcc/aarch64-linux-gnu/libc ./hello
