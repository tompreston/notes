# Serial
Uploading files over serial
- http://www.tldp.org/HOWTO/Remote-Serial-Console-HOWTO/upload.html

minicom default settings

    baud: 115200 8N1, flow control: N

Setting terminal width over UART:

    stty rows 50 cols 132

# minicom
Setup

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

# Cable colours
Some cable colours for a quick reference. This could change with different
cables. Typically you can just swap TX/RX if you can't see anything via serial.
If problems persist double check baud, hard/software flow control and device
status.

    | Device | TX     | RX     |
    | ------ | ------ | ------ |
    | FTDI   | Yellow | Orange |

# Debugging
For terminal issues, try;

    stty sane

Pulseview (from sigrok) can view signals on USB serial.

RS232 has different levels to TTL:

    https://www.sparkfun.com/tutorials/215
