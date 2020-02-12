# Cross compile
## Debian, GCC
On Debian, you will need to install the package:

    gcc-arm-linux-gnueabi

To get the following tools:

    /usr/bin/arm-linux-gnueabi-addr2line
    /usr/bin/arm-linux-gnueabi-ar
    /usr/bin/arm-linux-gnueabi-as
    /usr/bin/arm-linux-gnueabi-c++filt
    /usr/bin/arm-linux-gnueabi-cpp
    /usr/bin/arm-linux-gnueabi-cpp-6
    /usr/bin/arm-linux-gnueabi-dwp
    /usr/bin/arm-linux-gnueabi-elfedit
    /usr/bin/arm-linux-gnueabi-gcc
    /usr/bin/arm-linux-gnueabi-gcc-6
    /usr/bin/arm-linux-gnueabi-gcc-ar
    /usr/bin/arm-linux-gnueabi-gcc-ar-6
    /usr/bin/arm-linux-gnueabi-gcc-nm
    /usr/bin/arm-linux-gnueabi-gcc-nm-6
    /usr/bin/arm-linux-gnueabi-gcc-ranlib
    /usr/bin/arm-linux-gnueabi-gcc-ranlib-6
    /usr/bin/arm-linux-gnueabi-gcov
    /usr/bin/arm-linux-gnueabi-gcov-6
    /usr/bin/arm-linux-gnueabi-gcov-dump
    /usr/bin/arm-linux-gnueabi-gcov-dump-6
    /usr/bin/arm-linux-gnueabi-gcov-tool
    /usr/bin/arm-linux-gnueabi-gcov-tool-6
    /usr/bin/arm-linux-gnueabi-gprof
    /usr/bin/arm-linux-gnueabi-ld
    /usr/bin/arm-linux-gnueabi-ld.bfd
    /usr/bin/arm-linux-gnueabi-ld.gold
    /usr/bin/arm-linux-gnueabi-nm
    /usr/bin/arm-linux-gnueabi-objcopy
    /usr/bin/arm-linux-gnueabi-objdump
    /usr/bin/arm-linux-gnueabi-ranlib
    /usr/bin/arm-linux-gnueabi-readelf
    /usr/bin/arm-linux-gnueabi-size
    /usr/bin/arm-linux-gnueabi-strings
    /usr/bin/arm-linux-gnueabi-strip

Compile as normal:

    arm-linux-gnueabi-gcc foo.c -o foo

On embedded systems you may also have to link to the armhf lib:

    ln -s /lib/ld-linux-armhf.so.3 /lib/ld-linux.so.3

## Fedora, GCC (impossible)
Even though it is possible to install the cross-toolchain, we are missing the
glibc-arm-linux-gnu-devel package - which contains the ARM glibc (crt1.o).

    dnf install \
        binutils-arm-linux-gnu \
        gcc-arm-linux-gnu \
        gcc-c++-arm-linux-gnu

Just build in a Debian chroot/container.

https://bugzilla.redhat.com/show_bug.cgi?id=1456209
