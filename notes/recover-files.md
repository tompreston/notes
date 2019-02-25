# Recover files from encrypted ext4
Download System Rescue CD from http://www.system-rescue-cd.org/Download/

Install to a USB stick:

    sudo mount -o loop,exec systemrescuecd-x86-x.y.z.iso
    sudo bash /mnt/usb_inst.sh

Boot System Rescue CD and mount encrypted rootfs:

    cryptsetup luksOpen /dev/sda6 tpreston-rootfs

Recover files:

    extundelete --restore-directory /deleted/dir /dev/mapper/tpreston-rootfs

If recoverable, files should be in `RECOVERED_FILES`.
