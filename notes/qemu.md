# QEMU
You can use qemu to test a kernel:

    qemu-system-arm -M virt -m 128M -nographic -kernel arch/arm/boot/zImage
