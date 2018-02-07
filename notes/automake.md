# Automake
Dependencies:

    sudo apt install build-essential autoconf automake libtool pkg-config

configure:

    AC_INIT([helloworld], [0.1], [george@thoughtbot.com])
    AM_INIT_AUTOMAKE
    AC_PROG_CC
    AC_CONFIG_FILES([Makefile])
    AC_OUTPUT

Makefile.am:

    AUTOMAKE_OPTIONS = foreign
    bin_PROGRAMS = helloworld
    helloworld_SOURCES = main.c

On the maintainers system:

    libtoolize
    aclocal                # Set up an m4 environment
    autoconf               # Generate configure from configure.ac
    automake --add-missing # Generate Makefile.in from Makefile.am
    autoreconf --install   # optional
    ./configure            # Generate Makefile from Makefile.in
    make distcheck         # Build and test a tarball to distribute

Or all in one go:

    libtoolize && aclocal && autoconf && automake --add-missing && \
        autoreconf --install && ./configure && make distcheck

On the end-user's system:

    ./configure # Generate Makefile from Makefile.in
    make # Use Makefile to build the program
    make install # Use Makefile to install the program

https://robots.thoughtbot.com/the-magic-behind-configure-make-make-install

# Source Dependencies (deb-src)
You will also want to install source dependencies:

    root@deb-testing:~# cat /etc/apt/sources.list
    deb http://deb.debian.org/debian testing main contrib non-free
    deb-src http://deb.debian.org/debian testing main contrib non-free

    root@deb-testing:~# apt-get build-dep mesa
