# Containers
It all began with chroots. Then came containers.

! You cannot have users in containers, only root !

# systemd-nspawn
https://www.freedesktop.org/software/systemd/man/systemd-nspawn.html

    systemd-nspawn
    machinectl

Machines are stored at:

    /var/lib/machines

Install:

    sudo apt install systemd-containers
    sudo -i
    cd /var/lib/machines
    debootstrap testing deb-testing http://deb.debian.org/debian/

Chroot into other architectures:

    sudo systemd-nspawn --bind /usr/bin/qemu-arm-static -UD mnt

-U for randomised root user ID, omit if you want to use 0.

# Docker
Docker https://docs.docker.com/get-started/
Download and run containers

How can I keep a docker debian container open?
https://stackoverflow.com/questions/34863645

    docker build . # Expects ./Dockerfile
    docker run -it debian /bin/bash

The -i means "run interactively", and -t means "allocate a pseudo-tty".

# Docket/Debian

    https://hub.docker.com/_/debian/
    https://docs.docker.com/install/linux/docker-ce/debian/
    https://docs.docker.com/install/linux/linux-postinstall/

# Building things with docker
Build

    docker build -t CONTAINER_ID . # build env
    docker build  -t CONTAINER_ID -f Dockerfile

Run

    docker images
    docker run -it --mount source="$(realpath ../src)",target=/src,type=bind \
        CONTAINER_ID /bin/bash
    docker ps
    docker cp CONTAINER_ID:/project-dev/asset /to/wherever
