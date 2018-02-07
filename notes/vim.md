# Some useful vim commands
loop and printf
:for i in range(0,1016,4) | put =printf('GIC_DIST_TARGET_%02X,0x50041%03x', i/4, i+0x800) | endfor
