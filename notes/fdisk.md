# fdisk
Wipe and create a new partition:

    sudo fdisk /dev/sdb
    o # delete partition table
    n # create a new parititon
    w # write changes to disk

Make sure you format it:

    sudo mkfs.fat /dev/sdb1
