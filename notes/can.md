# CAN (Automotive Bus)
* https://elinux.org/Bringing_CAN_interface_up

PEAK CAN initialisation:
```
ip link set "can0" type can bitrate 125000
ip link set up "can0"
```

Cantact.io initialisation:
```
ip link set "can1" type can bitrate 500000
ip link set up "can1"
```
