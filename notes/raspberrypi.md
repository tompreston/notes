# Raspberry Pi notes
raspi-config

Headless ssh

    touch /boot/ssh

UART

    echo "enable_uart=1 >> /boot/config.txt

    GPIO Outside row
    5V 5V [GND TX RX]<-UART
           |   |  |
       black   |  |
           white  |
              green

    baud: 115200 8N1, flow control: N
    https://elinux.org/RPi_Serial_Connection

GPIO mapping

    https://pinout.xyz/

Ping multiple rpis

    fping ts-rig{1..6}
