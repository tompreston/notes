# Yocto
- https://elinux.org/Yocto_Project_Introduction

# Quickstart
- https://www.yoctoproject.org/docs/latest/brief-yoctoprojectqs/brief-yoctoprojectqs.html
- Quickly download and build LTS (dunfell) poky and boot the image with qemu.
- Also add the meta-openembedded layer, and build some lib (poco).

Get poky:

    git clone git://git.yoctoproject.org/poky
    cd poky
    git fetch --tags
    git tag
    git checkout tags/dunfell -b tpreston/dunfell

Build, enter qemu:

    source oe-init-build-env # notice `mkdir build; cd build`
    bitbake core-image-sato
    runqemu qemux86-64

Add meta-openembedded, and build some lib like poco:

    cd ~/poky
    git clone git@github.com:openembedded/meta-openembedded.git

    cd meta-openembedded
    git checkout dunfell -b tpreston/dunfell
    cd -

    cd build
    bitbake-layers add-layer ../meta-openembedded/meta-oe
    bitbake poco

# Useful commands
List all recipes:

    bitbake-layers show-recipes
    bitbake-layers show-recipes $target

Show all versions of packages:

    bitbake -s

Run `do_compile` or `do_clean`:

    bitbake -c compile $recipie-name
    bitbake -c clean $recipie-name

Enter a devshell before `do_compile`:

    bitbake -c devshell $recipie-name

Force a build from the `do_unpack` stage:

    bitbake -C unpack $recipie-name

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
