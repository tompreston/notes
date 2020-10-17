# Infrared Receivers in Linux
- IR decoding with BPF https://lwn.net/Articles/759188/
- LIRC Arch Wiki https://wiki.archlinux.org/index.php/LIRC

The old way to handle IR commands is with LIRC, a daemon process which requires
lots of context switching in and out the kernel. The new way is with IR protocol
decoding in BFP (see above).

The kernel has some interesting self-tests in:

    tools/testing/selftests/ir

The tools are included with v4l-utils:

    sudo dnf install v4l-utils

We can test with the rc-loopback:

    sudo modprobe rc-loopback

Clear keymaps, listen for all protocols and test (print to stdout):

    sudo ir-keytable -c -p all -t

Then send some 0x1e01 scancode in rc5 protocol:

    sudo ir-ctl -S rc5:0x1e01

You should see it in the ir-keytable test. You can also send keymaps keys:

    sudo ir-ctl -k /usr/lib/udev/rc_keymaps/asus_ps3_100.toml -K KEY_HOME

But you will only see the scancode in the ir-keytable test, because we haven't
taught it about any keymaps.

TODO demonstrate this in Python. Suggest people stop using python-lirc.
