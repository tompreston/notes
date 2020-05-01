# BuildStream
Building:

    bst build hello.bst

Checking out artifacts:

    bst checkout hello.bst hello

Running from target:

    bst shell hello.bst

Workspace:

    bst workspace open hello.bst hello-src
    vim hello-src/doc/amhello/src/main.c
    bst build hello.bst

BuildStream knows about the workspace and build from that. You can close to go
back using the original package.

Freeze an element at the current track HEAD:

    bst track hello.bst


## Debugging
You can create a BuildStream stack, which groups together elements:

    $ cat elements/tpreston-debug.bst
    kind: stack

    runtime-depends:
    - freedesktop-sdk.bst:components/gdb.bst
    - freedesktop-sdk.bst:components/strace.bst
    - sdk/gtk+-3.bst

    $ bst build tpreston-debug.bst
    $ bst shell tpreston-debug.bst
    > strace gtk3-demo
    > gdb gtk3-demo
