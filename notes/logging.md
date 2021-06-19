# Logging
* [Kafka distributed logging](http://kafka.apache.org/)

## Linux kernel
Dump the kernel log:

    dmesg

## systemd journal
* https://fedoramagazine.org/systemd-using-journal/

Look at system log for this boot, or all:

    journalctl --boot
    journalctl -b

    journalctl --all
    journalctl -a

Look at the end of a singe unit (systemd), eg snapd:

    journalctl --pager-end --unit snapd
    journalctl -eu snapd

## Fedora Logging
- https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/security_guide/sec-searching_the_audit_log_files

    sudo less /var/log/audit/audit.log

Although the audit.log is a bit hard to sift though, so use ausearch:

    sudo ausearch --message USER_LOGIN --success no --interpret

## Debian Logging

    sudo less /var/log/auth.log

## Searching for logs

    lsof | grep -iE "log|txt"
