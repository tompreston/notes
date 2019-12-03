# ARM
- ARM/THUMB instruction set
  http://infocenter.arm.com/help/topic/com.arm.doc.qrc0001l/QRC0001_UAL.pdf

# Testing for hardfp (hardware floating point) support
Hardware supports fp unit (vector floating point, NEON SIMD ufeatures):

    # grep -m1 Features /proc/cpuinfo
    Features        : half thumb fastmult vfp edsp thumbee neon vfpv3 tls vfpd32

Has the userland been compiled with VFP features (no in this case):

    # readelf -A /usr/cid-lib/libm.so | grep -c Tag_ABI_VFP
    0
