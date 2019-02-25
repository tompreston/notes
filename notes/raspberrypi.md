# Raspberry Pi notes
GPIO mapping

    https://pinout.xyz/

Serial UART

    echo "enable_uart=1" >> /boot/config.txt

    GPIO Outside row:
    5V 5V [GND TX RX]<-UART
           |   |  |
       black   |  |
           white  |
              green
    GPIO Inside row:
    3V3 [SDA SCL]<-I2C

    baud: 115200 8N1, flow control: N
    https://elinux.org/RPi_Serial_Connection

Configure interfaces with `raspi-config`

Static IP

    # cat /etc/network/interfaces
    iface eth0 inet static
        address 192.168.1.118
        gateway 192.168.1.1
        netmask 255.255.255.0
    # service networking restart

Headless ssh

    touch /boot/ssh

Ping multiple rpis

    fping ts-rig{1..6}
