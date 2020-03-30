# Virtual Machines
- https://docs.fedoraproject.org/en-US/quick-docs/getting-started-with-virtualization/
- http://rabexc.org/posts/how-to-get-started-with-libvirt-on
- https://libvirt.org/apps.html

Use libvirt and the graphical virt-manager:

    sudo dnf install libvirt virt-manager

Gnome boxes is an alternative to virt-manager.

## Windows
Download the Windows 10 ISO and use the key pulled from the ACPI tables.

    strings /sys/firmware/acpi/tables/MSDM | tail -1

Also install the virtio drivers:

    https://docs.fedoraproject.org/en-US/quick-docs/creating-windows-virtual-machines-using-virtio-drivers/
