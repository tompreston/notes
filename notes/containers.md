# Containers
* https://opencontainers.org/

See also notes/chroot.md.

# Terminology
* Prefer "container" to "docker container".
    * Docker is just one type of container engine (Docker, CRI-O, containerd).
* Prefer podman to docker, since it can run containers as a non-privileged user.
* Group of containers is called a "pod", hence Pod Manager.

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
Build with `$SOME_DIR` as context:

    vim "$SOME_DIR/Dockerfile"
    docker build -t CONTAINER_ID "$SOME_DIR/"

Build with no build context (faster):

    docker build  -t CONTAINER_ID - < Dockerfile

Run

    docker images
    docker run -it \
        --mount source="$(realpath ../src)",target=/src,type=bind \
        CONTAINER_ID /bin/bash
    docker ps
    docker cp CONTAINER_ID:/project-dev/asset /to/wherever


# Cleaning up Docker
Clean up unused Docker images with:

    docker system prune -a -f

Remove all docker images with:

    docker rmi $(docker images -q)

# Podman
- https://bt0dotninja.fedorapeople.org/Containers_101_with_Podman_on_Fedora29.pdf
- https://developers.redhat.com/blog/2019/01/15/podman-managing-containers-pods/
Rootless OCI https://podman.io/

Essentially:

    alias docker='podman'

On Fedora, SELinux gets in the way of bind-mounts, so make sure to include the
bind-propagation=z flag:

    podman run -it --mount=type=bind,bind-propagation=z,src=$(pwd),dst=/build \
        build-tag "make"

# Building stuff
I usually take the following approach when building things:

    ==> Dockerfile <==
    FROM fedora:30

    # General, cacheable tooling
    RUN dnf install -y @development-tools

    # Project specific dependencies
    RUN dnf install -y \
            libX11-devel \
            libXtst-devel

    ==> run-build.sh <==
    #!/bin/bash
    # Run the build container
    podman run \
            --mount=type=bind,bind-propagation=z,src=$(pwd),dst=/mnt \
            -it build-xdotool \
            /bin/bash

# Container images
## Debian
For apt-get you'll want to set (see: https://serverfault.com/a/797318):

    ARG DEBIAN_FRONTEND=noninteractive


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
