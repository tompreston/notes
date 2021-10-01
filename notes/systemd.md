# Systemd
* https://docs.fedoraproject.org/en-US/quick-docs/understanding-and-administering-systemd/
* https://opensource.com/article/20/5/systemd-units
* https://www.freedesktop.org/wiki/Software/systemd/
* https://www.freedesktop.org/wiki/Software/systemd/TipsAndTricks/
* https://www.freedesktop.org/wiki/Software/systemd/FrequentlyAskedQuestions/
* https://www.freedesktop.org/wiki/Software/dbus/
* https://www.freedesktop.org/wiki/Software/DbusProjects/
* https://pythonhosted.org/txdbus/dbus_overview.html
* https://www.freedesktop.org/wiki/Software/systemd/dbus/
* https://static.sched.com/hosted_files/ossna19/ee/systemd-SLIDES.pdf
* http://0pointer.net/blog/casync-a-tool-for-distributing-file-system-images.html

## Coredump
https://jlk.fjfi.cvut.cz/arch/manpages/man/coredumpctl.1

    coredumpctl list foo
    coredumpctl debug
    coredumpctl info 6654
    coredumpctl -o bar.coredump dump /usr/bin/bar

## Analyse

    systemd-analyse plot > /tmp/systemd-plot.svg
    systemd-analyse blame
    systemd-analyse time

For more detail see `man systemd-bootchart`:

* https://github.com/systemd/systemd-bootchart
* https://fedoraproject.org/wiki/Bootchart
* http://manpages.ubuntu.com/manpages/bionic/man1/systemd-bootchart.1.html

## How to I figure out which service a process belongs to?
You may either use ps for that:

    ps xawf -eo pid,user,cgroup,args

Or you can even check /proc/$PID/cgroup directly. Also see this blog story.
http://0pointer.de/blog/projects/systemd-for-admins-2.html

## Viewing active units

    systemctl

Shows user scopes like firefox, gnome-software:

    systemctl --user
