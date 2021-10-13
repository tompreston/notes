# Network
- https://www.incognito.com/tutorials/dhcp-options-in-plain-english/

Prefer
- NetworkManager
- iproute2
- iw

Do not use:
- wireless-tools (iwlist, iwconfig)
- ifconfig

Set a static IP for eth0:

    service networking stop

    ip link set eth0 up
    ip addr add 192.168.1.1/24 dev eth0

    ping 192.168.100.1

Set default route:

    ip route add default via 192.168.90.111 dev eth0


## ifup/ifdown
If just using /etc/networking/interface*, use ifup/ifdown commands.

More info https://wiki.debian.org/NetworkConfiguration#Setting_up_an_Ethernet_Interface


## NetworkManager
You can access NetworkManager from the cli:

    nmcli
    nmcli connection show
    nmcli device show


## DNS, DHCP
dhclient usually broadcasts IP and hostname to DNS

Use `host` to search DNS for hostname:

    $ host HOSTNAME DNS-IP

ifup/ifdown will reassociate using dhclient


## Traceroute
We can use traceroute follow hops to a given IP.

    traceroute 10.35.7.2


## Forward IP traffic through device (eg. network - raspberry pi - devkit)
Just looked this up [0], you need to setup the pi as a router:

    root@ts-rig1:~# echo 1 > /proc/sys/net/ipv4/ip_forward
    root@ts-rig1:~# iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
    root@ts-rig1:~# iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
    root@ts-rig1:~# iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

Then add a default route on the device:

    # ip route add default via 192.168.90.133 dev toucan
    # ip route
    default via 192.168.90.133 dev toucan
    192.168.90.0/24 dev toucan scope link  src 192.168.90.100

    # ping -c1 8.8.8.8
    PING 8.8.8.8 (8.8.8.8): 56 data bytes
    64 bytes from 8.8.8.8: seq=0 ttl=56 time=9.221 ms

    --- 8.8.8.8 ping statistics ---
    1 packets transmitted, 1 packets received, 0% packet loss
    round-trip min/avg/max = 9.221/9.221/9.221 ms

    # echo "nameserver 8.8.8.8" > /etc/resolv.conf
    # ping -c1 goo.gl
    PING goo.gl (216.58.213.14): 56 data bytes
    64 bytes from 216.58.213.14: seq=0 ttl=56 time=10.088 ms

[0] https://www.tecmint.com/setup-linux-as-router/

## tcpdump
You can use tcpdump to record network traffic. Here is a useful guide:
- https://danielmiessler.com/study/tcpdump/

    tcpdump -i eth0 -w capture.pcap

## Captive Portal
For whatever reason, captive portals don't always work on Linux (eg. it breaks
in Fedora 33, probably because of some domain name resolver change).  To
debug/fix, use route, curl, nmap to find out the gateway IP, then manually add
the domain into /etc/hosts.

    $ curl 8.8.8.8
    [snip]
    <LoginURL>https://crosscountrywifi.co.uk/connect?res=wispr&amp;uamip=192.168.101.1&amp;uamport=3990&amp;challenge=3b36a4a892ee976a02de8662066098fa</LoginURL>
    [snip]

    $ tail -1 /etc/hosts
    192.168.101.1   crosscountrywifi.co.uk

Once you've managed to log in, the DNS is probably broken. Inspect it, and
remove the broken one with an empty string (to fallback on the global defaults):

    resolvectl status
    resolvectl dns 4 ""

## Programming with Berkley Socket API
The protocol and transport-agnostic API used by Linux for all sockets, be they
UDP, TCP, UDS, Econet, arcnet, CANbus, etc.  Ie the
socket/listen/bind/accept/select system calls.

Some examples here: https://en.wikipedia.org/wiki/Berkeley_sockets
