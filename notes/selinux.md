# SELinux
- Great talk https://www.youtube.com/watch?v=_WOKRaM-HI4
- [SELinux Users and Administrators Guide](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/selinux_users_and_administrators_guide/index)
- https://fedoraproject.org/wiki/SELinux

Security Enhanced Linux.

- DAC Discretionary Access Control is users/groups (normal permissions).
- MAC Mandatory Access Control is policies governing subjects (processes)
  accessing objects (files).

SELinux is MAC and operates alongside DAC, a sort of belt-and-braces approach.

The -Z arg is available for most commands, which shows SELinux labels.

Install setroubleshoot and setroubleshoot-server on machines you'll be
developing policy modules on. Then restart auditd (using the service wrapper):

    dnf install -y setroubleshoot setroubleshoot-server
    systemctl restart auditd # fails by design
    service auditd restart

Debug messages appear in jounal (since last boot):

    journalctl -b -0

With the setroubleshoot tools installed these messages should be really useful.

Get and set sebools:

    getsebool -a
    setsebool BOOL 1 -P # set to 1, Permanently

Locally set bools get stored in:

    /etc/selinux/targeted/modules/active/booleans.local

## Changing context labels
You can change selinux labels:

    chcon -u system_u -r object_r -t httpd_sys_content_t /var/www/html/index.html

Usually we don't care about user or role:

    chcon -t httpd_sys_content_t /var/www/html/index.html

Or just point it at a know reference:

    chcon --reference /var/www/html /var/www/html/index.html

Or, super lazy, just fix labels in dir:

    restorecon -vR /var/www/html

Default contexts are stored in:

    /etc/selinux/targeted/contexts/files/file_contexts

In some instances a new directory might not have parent context to `restorecon`
to, so you have to tell selinux about the context first. Then run `restorecon`:

    semanage fcontext -a -e /var/www/html /foo # add existing context to /foo
    restorecon -vR /foo

## Debugging
Permissive mode lets us log lots of errors but not prevent application from
running. Useful to gathering lots of errors in one go, to create policies for.

    /etc/selinux/config

## Graphical
You can access selinux GUI by installing selinux-config-selinux:

    dnf install -y policycoreutils-gui
    selinux-config-selinux
