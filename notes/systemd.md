# Systemd
- https://static.sched.com/hosted_files/ossna19/ee/systemd-SLIDES.pdf

## Coredump
- https://jlk.fjfi.cvut.cz/arch/manpages/man/coredumpctl.1

    coredumpctl list foo
    coredumpctl debug
    coredumpctl info 6654
    coredumpctl -o bar.coredump dump /usr/bin/bar

## Analyse

    systemd-analyse plot > /tmp/systemd-plot.svg
    systemd-analyse blame
    systemd-analyse time

For more detail see systemd-bootchart:

* https://github.com/systemd/systemd-bootchart
* https://fedoraproject.org/wiki/Bootchart
* http://manpages.ubuntu.com/manpages/bionic/man1/systemd-bootchart.1.html
