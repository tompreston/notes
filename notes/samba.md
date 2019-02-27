# Samba share
Samba is slower than NFS but offers network discovery for things like macOS.

    sudo apt install samba
    sudo apt install samba-client

Add a guest user for passwordless access:

    sudo useradd samba-guest
    sudo gpasswd -a samba-guest users
    sudo smbpasswd -a samba-guest

Create the share:

    sudo mkdir -p /srv/samba/guest
    sudo chown root:users /srv/samba/guest
    sudo chmod 2775 /srv/samba/guest

Edit config:

    man smb.conf
    /etc/samba/smb.conf

    # set the guest account for passwordless
    guest account = samba-guest

    # add a guest share
    [guest]
    path = /srv/samba/guest
    read only = no
    guest ok = yes
