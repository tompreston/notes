# chroot
Create a Debian chroot:

    c="/srv/chroot/debian-buster-i386"
    sudo mkdir -p "$c"
    sudo debootstrap buster "$c"

Manage it with schroot:

    cat > /etc/schroot/chroot.d/debian-buster-i386
    # schroot chroot definitions.
    # See schroot.conf(5) for complete documentation of the file format.
    #
    # Please take note that you should not add untrusted users to
    # root-groups, because they will essentially have full root access
    # to your system.  They will only have root access inside the chroot,
    # but that's enough to cause malicious damage.
    #
    # The following lines are examples only.  Uncomment and alter them to
    # customise schroot for your needs, or create a new entry from scratch.
    #
    [debian-buster-i386]
    description=A 32-bit Debian installation
    aliases=buster32
    type=directory
    directory=/srv/chroot/debian-buster-i386
    users=tpreston
    root-groups=root
    profile=desktop
    personality=linux32
    preserve-environment=true

The profile is a directory in /etc/schroot. Look at /etc/schroot/desktop/fstab
to see what it does.

Enter the chroot as a user or root:

    schroot -c buster32
    sudo schroot -c buster32 -u root

Your rootfs should be the chroot, but /home will be mounted according to fstab.

Make sure your PS1 does something with `/etc/debian_chroot` so you know that
you're in one.

More info:

    man schroot
    man schroot.conf

See also notes/containers.md
