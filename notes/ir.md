# Infrared Receivers in Linux
- IR decoding with BPF https://lwn.net/Articles/759188/
- Linux Remote Controller API https://www.kernel.org/doc/html/latest/userspace-api/media/rc/remote_controllers.html
- LIRC Arch Wiki https://wiki.archlinux.org/index.php/LIRC
- Wayland libinput for debugging https://wayland.freedesktop.org/libinput/doc/latest/tools.html#libinput-list-devices

There are some interesting self-tests in:

    tools/testing/selftests/ir

The ir-ctl and ir-keytable tools are included with v4l-utils:

    dnf install v4l-utils

We can test with the rc-loopback:

    modprobe rc-loopback

Clear keymaps, listen for all protocols and test (print to stdout):

    ir-keytable -c -p all -t

Then send some 0x1e01 scancode in rc5 protocol:

    ir-ctl -S rc5:0x1e01

You should see it in the ir-keytable test. You can also send keymaps keys:

    ir-ctl -k /usr/lib/udev/rc_keymaps/asus_ps3_100.toml -K KEY_HOME

But you will only see the scancode in the ir-keytable test, because we haven't
taught it about any keymaps yet. You can do this with the -k flag:

    ir-keytable -c -p rc5 -k 0x1e14:KEY_UP

Or teach it about a whole keymap:

    ir-keytable -c -w /usr/lib/udev/rc_keymaps/hauppauge.toml

Now when we send in scancodes or keymap keys we can see the correct events
in `ir-keytable -t`. We can also watch them with evtest or libinput:

    evtest /dev/input/event3
    evtest /dev/input/event18
    libinput debug-events

# TODO
- Show that the fake IR KEY_VOLUMEUP can control GNOME 3, as keyboard
  KEY_VOLUMEUP does.
- Demonstrate Python callbacks for IR KEY_VOLUMEUP.
- Suggest people stop using python-lirc.
