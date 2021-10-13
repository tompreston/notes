# dbus
List of properties from `man org.freedesktop.systemd1`
* https://www.freedesktop.org/software/systemd/man/org.freedesktop.systemd1.html

Print startup times:

    busctl get-property --json=short --no-pager \
        org.freedesktop.systemd1 /org/freedesktop/systemd1 org.freedesktop.systemd1.Manager \
        FirmwareTimestampMonotonic \
        LoaderTimestampMonotonic \
        InitRDTimestampMonotonic \
        UserspaceTimestampMonotonic \
        FinishTimestampMonotonic

Some gdbus stuff:

    gdbus introspect --system -d com.service.Bluetooth -o / -r

Monitor all Bluetooth Events

    dbus-monitor --profile --system
        interface='com.service.Bluetooth',type='signal'

Get the name of the Bluetooth DBus connection:

    gdbus call -y -d org.freedesktop.DBus -o /
        -m org.freedesktop.DBus.GetNameOwner 'com.service.Bluetooth'

Using that connection name, the PID can be found with:

    gdbus call -y -d org.freedesktop.DBus -o /
        -m org.freedesktop.DBus.GetConnectionUnixProcessID :1.251
