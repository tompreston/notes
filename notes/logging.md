# Debian Logging

    sudo less /var/log/auth.log

# Fedora Logging
- https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/security_guide/sec-searching_the_audit_log_files

    sudo less /var/log/audit/audit.log

Although the audit.log is a bit hard to sift though, so use ausearch:

    sudo ausearch --message USER_LOGIN --success no --interpret