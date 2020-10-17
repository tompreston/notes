# Fedora
## DNF
Some simple commands:

    dnf upgrade
    dnf install podman
    dnf provides /usr/bin/ssh
    dnf list --installed
    dnf info openssh

Download an RPM package:

    dnf download openssh
    rpm --query --list openssh-8.0p1-5.fc30.x86_64.rpm

Download the source of a package:

    dnf download --source openssh
    rpm --query --list openssh-8.0p1-5.fc30.src.rpm

List files in a package:

    dnf repoquery -l v4l-utils

## Development

    dnf install @development-tools

## Change the time

    timedatectl
    timedatectl list-timezones
    timedatectl set-timezone Europe/Berlin

## Copr
Remove a copr repo:

    sudo dnf copr remove pschyska/alacritty
