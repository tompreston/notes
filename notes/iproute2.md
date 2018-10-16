# iproute2
Some common iproute2 commands.

Set a static IP for eth0:

    ip link set eth0 up
    ip addr add 192.168.1.1/24 dev eth0

Set default route:

    route add default gw 192.168.x.111
