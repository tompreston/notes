# Network
Use iproute2, not ifconfig.

Set a static IP for eth0:

    service networking stop

    ip link set eth0 up
    ip addr add 192.168.1.1/24 dev eth0

    ping 192.168.100.1

Set default route:

    route add default gw 192.168.x.111


# NetworkManager (debian)
You can access NetworkManager from the cli:

    nmcli
    nmcli connection show
    nmcli device show


# DNS, DHCP
dhclient usually broadcasts IP and hostname to DNS

Use `host` to search DNS for hostname:

    $ host HOSTNAME DNS-IP

ifup/ifdown will reassociate using dhclient
