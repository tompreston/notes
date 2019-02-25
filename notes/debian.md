# Debian
Search packages for file

    dpkg --search /usr/bin/ssh
    dpkg -S /usr/bin/ssh

List/search installed packages:

    dpkg --list
    dpkg -l | grep openssh

Show information about a package:

    apt show openssh-client
