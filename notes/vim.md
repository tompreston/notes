# vim
Loop and printf

    :for i in range(0,1016,4) | put =printf('GIC_DIST_TARGET_%02X,0x50041%03x', i/4, i+0x800) | endfor

# Registers
- https://www.brianstorti.com/vim-registers/
- https://stackoverflow.com/a/3961954

Print registers:

    :reg

Normal yank is like "unnamed register + yank":

    ""y
    ""yy

Last yank is stored in "0 register. "1 to "9 are last deleted lines.

Clipboard is "+:

    "+y
    "+yy

See the currently loaded filetype:

    :set filetype?
    :set ft?
