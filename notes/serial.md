# Serial
Uploading files over serial
- http://www.tldp.org/HOWTO/Remote-Serial-Console-HOWTO/upload.html

minicom default settings

    baud: 115200 8N1, flow control: N

# minicom
setup
sudo minicom -s

Example:

    115200 8N1 | NOR | Minicom 2.7 | VT102 | Offline | ttyUSB1

Notes:
- If the serial is messed up, it might be multiple processes. Try killing

    sudo fuser -a /dev/ttyUSB1

- If exiting uncleaning, the lock might be held. rm /var/lock/LCK..ttyUSB1

# Persistent udev naming of serial devices
- http://hintshop.ludvig.co.nz/show/persistent-names-usb-serial-devices/

    $ udevadm info -a -n /dev/ttyUSB1 | grep '{serial}' | head -1
    ATTRS{serial}=="FT9FPMI7"

    $ vim /etc/udev/rules.d/50-serial-symlinks.rules
    SUBSYSTEM=="tty", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", \
        ATTRS{serial}=="FTA5HWK2", SYMLINK+="tty-my-device"
    SUBSYSTEM=="tty", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", \
        ATTRS{serial}=="FT9FPMI7", SYMLINK+="tty-my-device"

    $ sudo udevadm control --reload-rules
