# ctags
Use universal-ctags
- https://ctags.io/
- http://docs.ctags.io/en/latest/
- https://github.com/universal-ctags/ctags

Which is available via snap:

    snap install universal-ctags

Create the alias:

    alias ctags="universal-ctags"

Example 1: Python tags for tests in buildroot:

    ctags -R --languages=python --python-kinds=-iv -f tags support/testing

Example 2: Tags in kernel:

    make tags
