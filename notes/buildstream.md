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
