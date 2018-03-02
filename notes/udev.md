# udev
Monitor

    udevadm monitor

Reload rules and trigger all

    udevadm control --reload-rules
    udevadm trigger

Trigger sda1 rule

    udevadm trigger -v -c add -t devices -s block -y sda1
