# Network
Static IP:

    service networking stop
    ip link set eth0 up
    ip addr add 192.168.100.10/24 dev eth0
    ping 192.168.100.1
