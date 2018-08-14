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

Force a build from the `do_unpack` stage:

    bitbake $recipie-name -C unpack

See which recipes built a package:

    oe-pkgdata-util find-path /path/to/package

# Normal recipe build tasks:

    do_build      Depends on all normal tasks
    do_fetch      Download source URI
    do_unpack     Unpack into working directory ${WORKDIR}
    do_patch      Patch the source in ${WORKDIR}
    do_configure  Configures the source
    do_compile    Compiles the source
    do_install    Install to ${D}, which is ${WORKDIR}/image
    do_package    Take an install and split into packages (eg. archive a rootfs)
    do_package_write_*

See: https://www.yoctoproject.org/docs/1.8/ref-manual/ref-manual.html#usingpoky-debugging-taskrunning

# WIC
Open Embedded Image Creator oeic is called wic because it is easier to
pronounce.
