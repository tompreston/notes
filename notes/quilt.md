# Quilt
Use quilt to apply patches when we don't have git.
- http://www.shakthimaan.com/downloads/glv/quilt-tutorial/quilt-doc.pdf

## Workflow
Make a new patch:

    quilt new 0001-add-the-foo.patch

Edit changes, which will automatically add the file to the patch:

    quilt edit include/cef_browser.h

Alternatively, add all the files we're interested in and Quilt will begin to
track changes to these files no matter how you edit them:

    quilt add include/cef_browser.h
    quilt add libcef/browser/browser_host_impl.cc
    quilt add libcef/browser/browser_host_impl.h

Make some changes however you like (you can even use patch!):

    quilt edit include/cef_browser.h
    vim include/cef_browser.h
    patch -p1 < /path/to/change.patch

Then refresh the patch:

    quilt refresh
    cat patches/0001-add-the-foo.patch

Add a new patch on top:

    quilt new 0002-switch-the-bar.patch

Now is a good time to look at the patch stack:

    quilt top
    quilt series

Add the new files and repeat as above:

    quilt add include/cef_browser.h

You can pop to go back on the patch stack and push to re-apply.
