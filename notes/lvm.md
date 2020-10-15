# Logical Volume Management
- https://wiki.archlinux.org/index.php/LVM

Prepare the physical volume (PV):

    pvcreate /dev/sdb1
    pvs


Create a volume group (VG) of one or many PVs:

    vgcreate vg0 /dev/sdb1
    vgcreate vg0 /dev/sdb1 /dev/sdb2
    vgs

Activate the VG:

    vgchange -a y vg0

Now create the logical volume (LV) called "data":

    lvcreate -l +100%FREE vg0 -n data
