# Disk paritions
## fdisk
Wipe and create a new partition:

    sudo fdisk /dev/sdb
    o # delete partition table
    n # create a new parititon
    w # write changes to disk

Make sure you format it:

    sudo mkfs.fat /dev/sdb1

## kpartx
Use kpartx to mount images on the loopback:

    $ sudo kpartx -av mmc.img
    GPT:Primary header thinks Alt. header is not at the end of the disk.
    GPT:Alternate GPT header not at the end of the disk.
    GPT: Use GNU Parted to correct GPT errors.
    add map loop0p1 (253:4): 0 25141215 linear 7:0 24576
    add map loop0p2 (253:5): 0 256 linear 7:0 2048
    add map loop0p3 (253:6): 0 896 linear 7:0 4096
    add map loop0p4 (253:7): 0 1152 linear 7:0 6144
    add map loop0p5 (253:8): 0 128 linear 7:0 8192
    add map loop0p6 (253:9): 0 384 linear 7:0 10240
    add map loop0p7 (253:10): 0 1152 linear 7:0 12288
    add map loop0p8 (253:11): 0 128 linear 7:0 14336
    add map loop0p9 (253:12): 0 1280 linear 7:0 16384
    add map loop0p10 (253:13): 0 896 linear 7:0 18432
    add map loop0p11 (253:14): 0 256 linear 7:0 20480
    add map loop0p12 (253:15): 0 160 linear 7:0 22528

    $ sudo mount /dev/mapper/loop0p1 /mnt

When you're done:

    $ sudo umount /mnt
    $ sudo kpartx -d mmc.img

## sfdisk
Dump a partition table:

    sfdisk --dump /dev/loop0 > loop0.dump

Restore:

    sfdisk /dev/loop0 < loop0.dump

Backup a disk:

    sfdisk --backup /dev/loop0

See `man sfdisk` BACKING UP THE PARTITION TABLE.
