# Yocto
- https://elinux.org/Yocto_Project_Introduction

# Useful commands
List all recipes:

    bitbake-layers show-recipes
    bitbake-layers show-recipes $target

Run `do_compile`:

    bitbake $recipie-name -c compile

Enter a devshell before `do_compile`:

    bitbake $recipie-name -c devshell

# Quick notes
These were taken while learning yocto and may not be useful later.

Stages:

    do_unpack
    do_configure
    do_compile
    do_install    Install to ${D}, which is ${WORKDIR}/image
    do_package    Take an install and split into packages (tar a rootfs?)

Open Embedded Image Creator oeic is called wic because it is easier to
pronounce.
